## To Pull the Files
> - `gdown.pl https://drive.google.com/file/d/1PWWO5wVRRThLBXXEZjyWZHIb9udVcnCS/edit r1.fastq`
> - `gdown.pl https://drive.google.com/file/d/1mZFvpSIctuBihkOlQX9vhrkxng3cRmvK/edit r2.fastq`
> - `efetch -db nucleotide -format fasta -id CP000141.1 >> C.hydrogenoformans_Z2901.fasta`
-
## Mapping
> - `bowtie2-build C.hydrogenoformans_Z2901.fasta C.hydro`
> - `bowtie2 -x C.hydro -1 r1.fastq -2 r2.fastq -S WA3.sambowtie2 -x C.hydro -1 r1.fastq -2 r2.fastq -S WA3.sam`
-
## 74.52% overall alignment rate
