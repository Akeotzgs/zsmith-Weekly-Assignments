## To pull the files
> - `gdown.pl https://drive.google.com/file/d/1AAi_-gKOmu9lEOgTJTrAtg4pHHqxessZ/edit G15_S3_L001_R1_001.fastq.gz`
> - `gdown.pl https://drive.google.com/file/d/1p5ht1Tm9ZuJmqMroZWh3MbjM0qCpTAuo/edit G15_S3_L001_R2_001.fastq.gz`

## Quality Filtering and Adapter Cutting
> - `fastqc G15_S3_L001_R1_001.fastq.gz`
> - `fastqc G15_S3_L001_R2_001.fastq.gz`
> - From there we are able to look at the .html output and determin the original quality report. A read of this report showed numerous quality concerns and issues that needed addressing via trimming or other quality control. 
> - `cutadapt -q 20,20 -a CTGTCTCTTATACACATCTCCGAGCCCACGAGAC -A CTGTCTCTTATACACATCTGACGCTGCCGACGA -m 50 --max-n 0 -o G15_S3_L001_R1_001.cutadapt.fastq -p G15_S3_L001_R2_001.cutadapt.fastq G15_S3_L001_R1_001.fastq.gz G15_S3_L001_R2_001.fastq.gz`
> - I chose to cut those adapters as it was given in class that this data used the same adapter tags as what we had done in class. These can then have the quality determined by using the same process as finding the original quality.
> - `fastqc G15_S3_L001_R1_001.cutadapt.fastq`
> - `fastqc G15_S3_L001_R2_001.cutadapt.fastq`
 
 ## De Novo Assembly
> - `conda activate de_novo`
> - `spades.py -k 21,51,71,91,111,127 --careful --pe1-1 G15_S3_L001_R1_001.cutadapt.fastq --pe1-2 G15_S3_L001_R2_001.cutadapt.fastq -o G15_S3_L001_R1_and_2_001_spades_output`
> - I chose to use this assembler with these parameters as they are the same that we had used in class previously, additionally I felt that without knowing the exact size of the genome we are working with, it is likely comperable to the bacteria de novo assembly that we did in class, thus these same parameters should be sufficent for the first run through of assembly. 
> - `quast contigs.fasta -o Quast_contigs`

## Write Up
1. Parameters used for assembly and choice of assembler.
> - I chose to use the spades assembler with these parameters as they are the same that we had used in class previously, additionally I felt that without knowing the exact size of the genome we are working with, it is likely comperable to the bacteria de novo assembly that we did in class, thus these same parameters should be sufficent for the first run through of assembly.
2. Table listing the quality statistics of the assembly:

| Statistic | Quality/Number |
| ----------- | ----------- |
| # contigs (>= 0 bp)	| 155 |
| # contigs (>= 1000 bp) | 89 |
| # contigs (>= 5000 bp) |	69 |
| # contigs (>= 10000 bp) |	61 |
| # contigs (>= 25000 bp) |	45 |
| # contigs (>= 50000 bp) |	26 |
| Largest contig | 301694 |
| GC (%) |	65.48 |
| N50 | 96859 |

3. Discussion of if this is a high quality assembly.
> - Since it can be assumed we would ideally want only 1 contig as this is from a bacterial sample, the total number of contigs shows this is not an ideal assembly, however 155 cocntigs is not an unreasonable ammount. The L50 of 14 and N50 of 96,859 are not ideal, however are comperable to the other bacterial assembly that we had done in class for the size. Similarily, the longest contig in this assembly makes about about 1/13th of the entire assembly, which shows that while it is very promising in length, the remainder of the contigs drastically drop off for the L50 to be 14. Overall this is a decent assembly, which is to be expected with the initial quality reading being rather poor, even after cutting the addapters. It may be worth while to re-assemble this after more refined quality control is done, or with different paramiters for the assembler to follow. 



