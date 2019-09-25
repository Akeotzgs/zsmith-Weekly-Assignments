## First, the code I used to pull the Coffee_Chloroplast.gbk and convert it to a .fasta:
> - `efetch -db=nucleotide -id=NC_008535.1 -format=gb>Coffee_Chloroplast.gbk`
> - `python genbank_to_fasta.py Coffee_Chloroplast.gbk Coffee_Chloroplast.fasta`

I did this to first pull the data from the database, put it into a .gbk file, which can then be converted into a .fasta file. I used the same methods and python script as we have used in class.

## Second, the manipulations of the Coffee_Chloroplast.fasta file, and included answers to questions.

* Determine the number of protein sequences in the chloroplast.
> `grep ">" Coffee_Chloroplast.fasta | uniq | wc -l`


This gives an output of 85, so there are 85 protein sequences in the chloroplast. I did it this way as it will pull only the unique names of a sequence, thus the number of lines (wc -l) would be the number of sequences.


* Create a file of all of the names of protein sequences in Coffee plant's chloroplast sequences.
> `grep ">" Coffee_Chloroplast.fasta | sed 's/>//' | sort >> Sequence_Names.txt`


This makes a text file containing all of the sequence names, and even removes the ">" in front. Additionally, this will sort those entries alphabetically to make it easier to go through them. Due to the sheer number of sequences, I am not going to put in what would've been printed without the conversion to a file.


* How many photosystem subunits are present in the chromosome?
>` grep "photosystem" Coffee_Chloroplast.fasta | grep "subunit" | wc -l`


This gives a result of 3, which represents the sequences containing both "photosystem" and "subunit"


> `grep "photosystem" Coffee_Chloroplast.fasta | grep "subunit"`


This prints the name of all 3 sequences, which are:
- ">CoarCp031 [photosystem I subunit VIII] from NC_008535"
- ">CoarCp041 [photosystem I subunit IX] from NC_008535"
- ">CoarCp074 [photosystem I subunit VII] from NC_008535"


* Make a .fasta file with the sequences for ATP synthase CF1 beta subunit protein sequence.
> `grep -A 1 'ATP synthase CF1 beta subunit' Coffee_Chloroplast.fasta >> ATP_synthase_CF1_beta_subunit.fasta`

This makes a .fasta file with the name and sequence for ATP synthase CF1 beta subunit. This is done with 'grep -A 1' which pulls the line that the argument 'ATP synthase CF1 beta subunit' is found, and the line just after it (1).

> `grep -A 1 'ATP synthase CF1 beta subunit' Coffee_Chloroplast.fasta`

- ">CoarCp028 [ATP synthase CF1 beta subunit] from NC_008535
MKINPTTSGSGVSTLEKKNMGRIVQIIGPVLDVAFPAGKMPNIYNALVVKGRDTVGQPINVTCEVQQLLGNNRVRAVAMSSTDGLTRGMEVIDTGAPLSVPVGGATLGRIFNVLGEPVDNLGAVDTRTTSPIHRSAPAFIQLDTKLSIFETGIKVVDLLAPYRRGGKIGLFGGAGVGKTVLIMELINNIAKAHGGVSVFGGVGERTREGNDLYMEMKESGVINKENIAESKVALVYGQMNEPPGARMRVGLTALTMAEYFRDVNEQDVLLFIDNIFRFVQAGSEVSALLGRMPSAVGYQPTLSTEMGSLQERITSTKEGSITSIQAVYVPADDLTDPAPATTFAHLDATTVLSRGLAAKGIYPAVDPLDSTSTMLQPRIVGEEHYETAQRVKQTLQRYKELQDIIAILGLDELSEEDRLTVARARKIERFLSQPFFVAEVFTGSPGKYVGLAETIRGFQLILSGELDSLPEQAFYLVGNIDEATAKAMNLEMENNLKK"

This is what the output of the command looks like without being moved to a file. 
