* Command 1: grep ">" WA1.txt | sort | head -1
> This command will first pull only the lines in the file that have > in them, which are specifically the sequence names.
> These will then be sorted alphabetically, with the first one being printed.
> For the WA1.fasta file, the expected output will be >alpha_globin_dog P60529 Canis lupus famillaris (dog)
> Removing the [head -1] filter would cause all of the sequence names to be printed alphabetically
> This is useful for identifying what sequences are present in large ammounts of data, and helps to organize it for better organization.
* Command 2: grep -v ">" WA1.txt | uniq | wc -l
> This command will first pull only the lines in the file that do not have > in them, which are the sequences without the names. 
> These will then be checked for uniquness.
> The lines that are uniqe will then be counted and totalled, with the number of unique lines printed.
> For the WA1.fasta file, it will be 13.
> This is useful as it tells us how many unique sequences exist within a data set, as it is possible for a large pool of data to contain the same sequence multiple times, such as a highly conserved gene. Or for finding instances of mutations in a population.
* Command 3: grep ">" WWA1.txt | sed 's/>//' | sort >> hold.txt
> This command will first pull only the lines in the file that have > in them, which are specifically the sequence names.
> These will then have the > symbole at the front of the line removed for easier reading.
> The lines will then be sorted alphabetically by sequence name.
> The output will be printed into a file named hold.txt
> This is useful as it allows us to store the sequence neams in another location, either for further manipulation or for record keeping, and lets us remove the, at this point, not needed '>' symbol.
