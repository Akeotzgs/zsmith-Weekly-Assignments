## Pulling the Data
> - `wget https://github.com/stechtmann/BL4300-5300/raw/master/data/Weekly_Assignment_data/HSP_prot.fasta`
> - `wget https://github.com/stechtmann/BL4300-5300/raw/master/data/Weekly_Assignment_data/Unk_therm.faa`

## Making the Database
> - `makeblastdb -in Unk_therm.faa -dbtype prot -title Unk_therm_protein`

## Qurey
> - `blastp -db Unk_therm.faa -query HSP_prot.fasta -out HSP_prot_BLAST.txt -outfmt 7`
> - `nano HSP_prot_BLAST.txt`

## Question Analysis:
1. How many HSPs were found in the unknown organism?
> - 71 total hits for HSPs found in the organism. Of those: 42 had E-Values smaller than 10 and had representable bitscores, thus are signifigant and likely to be HSPs.
2. Provide your justification for how many HSPs were in the organism (use information in the BLAST ouput E-value, length, percent ID, etc).
> - This can be determined based on the E-value, we want lower values, and the bitscore, of which only comes out for viable E-values of less than 10.The higher the bitscore and lower the E-value the more signifigant probability that the identified protein is present.
3. How many HSP have paralogs?
> - Since there were 71 total hits, and 42 could be identified as homologs to HSPs, the remaining 29 would be paralogs of different function but similar sequence.
4. Provide a justification for the presence of paralogs.
> - Paralogs would be present when they are within the field search of homology, but don't meet the parameters that we would use to identify true homologs. The paralogs have a similar structure and thus sequence, but a different function that would be evident from the signfigant difference in sequence, such as those with a <10 e value.



