## To Pull the Files
> - `gdown.pl https://drive.google.com/file/d/1PWWO5wVRRThLBXXEZjyWZHIb9udVcnCS/edit r1.fastq`
> - `gdown.pl https://drive.google.com/file/d/1mZFvpSIctuBihkOlQX9vhrkxng3cRmvK/edit r2.fastq`
> - `efetch -db nucleotide -format fasta -id CP000141.1 >> C.hydrogenoformans_Z2901.fasta`


## Quality
> - `fastqc r1.fastq`
> - `fastqc r2.fastq`
> - From there, we can open the r1.fastqc.html and r2.fastqc.html to view the quality.
> - From the reports, the Summary for each shows that the only problematic thing that would require quality control would be trimming the adapter sequence used by the sequencer. This is evident in the Overexpressed sequences reeport, and shows that Illumina Paired End PCR Primers were used, specifically 2 for r1, and 1 for r2. Representing potential forward and backward primers and sequences. 
> - Therefore, trimming those portions would be recomended to improve the sequence alignment and mapping to thee reference genome. I am not going to trim these however, as I do not know the exact positioning of the adapters that need trimming, despite the FastQC report providing the potentail primer sequence. 


## Mapping
> - `bowtie2-build C.hydrogenoformans_Z2901.fasta C.hydro`
> - `bowtie2 -x C.hydro -1 r1.fastq -2 r2.fastq -S WA3.sambowtie2 -x C.hydro -1 r1.fastq -2 r2.fastq -S WA3.sam`
> - This returns the following overall alignment rate: 74.52%
