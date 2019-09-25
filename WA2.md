* Determine the number of protein sequences in the chloroplast.
> grep ">" Coffee_Chloroplast.fasta | uniq | wc -l
/n This gives an output of 85, so there are 85 protein sequences in the chloroplast. I did it this way as it will pull only the unique names of a sequence, thus the number of lines (wc -l) would be the number of sequences.
/n
* Create a file of all of the names of protein sequences in Coffee plant's chloroplast sequences.
> grep ">" Coffee_Chloroplast.fasta | sed 's/>//' | sort >> Sequence_Names.txt
/n This makes a text file containing all of the sequence names, and even removes the ">" in front.
/n
* How many photosystem subunits are present in the chromosome?
> grep "photosystem" Coffee_Chloroplast.fasta | uniq | wc -l
/n This gives a result of 22 sequences containing "photosystem"
> grep "photosystem" Coffee_Chloroplast.fasta
/n This prints all 22 sequences, and from there we can see which contain the word "subunit". This shows that there are 3 sequences that actually have the keyword "subunit"
/n
* Make a .fasta file with the sequences for ATP synthase CF1 beta subunit protein sequence.
