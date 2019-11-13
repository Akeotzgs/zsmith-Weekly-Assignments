`install.packages("tidyverse")`

`if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager")`

`BiocManager::install("DESeq2")`

`install.packages("readr")`

`library(readr)`

`library(tidyverse)`

`library(DESeq2)`

`Counts <- read_csv("https://github.com/stechtmann/BL4300-5300/raw/master/data/Weekly_Assignment_data/WA_counts.csv")`

`Metadata <- read_csv("https://github.com/stechtmann/BL4300-5300/raw/master/data/Weekly_Assignment_data/WA8_Metadata.csv")`

`head(counts)`

`head(metadata)`

`class(counts)`

`framecounts <- as.data.frame(Counts)`

`framemetadata <- as.data.frame(Metadata)`

`names(framecounts)[-1]`

`framemetadata$id`

`names(framecounts)[-1]==framemetadata$id`

`all(names(framecounts)[-1]==framemetadata$id)`

`dds.data <- DESeqDataSetFromMatrix(countData=framecounts,
                                   colData=framemetadata, 
                                   design=~dex, 
                                   tidy=TRUE)`
`dds <- DESeq(dds.data)`

`res <- results(dds, tidy=TRUE)`

`res <- tbl_df(res)`

`res2 <- arrange(res, padj)`

`res3 <- filter(res2, padj<=0.05 & log2FoldChange>=2)`

`res4 <- filter(res2, padj<=0.05 & log2FoldChange<=-2)`

`res=mutate(res,significance=ifelse(padj<0.05,"Significant","Non-significant"))`

`res3=mutate(res3,significance=ifelse(padj<0.05,"Significant","Non-significant"))`

`res4=mutate(res4,significance=ifelse(padj<0.05,"Significant","Non-significant"))`
