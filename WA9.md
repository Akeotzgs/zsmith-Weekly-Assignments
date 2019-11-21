# Question 1
-  `ggplot(res) +`
-  `geom_point(aes(x=log2FoldChange, y=-log10(padj), colour=log2FoldChange<0)) +`
-  `ggtitle("Volcano Plot of Expression for Control and Mutant") +`
-  `xlab("log2 fold change") + `
-  `ylab("-log10 adjusted p-value") +`
-  `#scale_y_continuous(limits = c(0,50)) +`
-  `theme(legend.position = "none",`
-  `      plot.title = element_text(size = rel(1.5), hjust = 0.5),`
-  `      axis.title = element_text(size = rel(1.25)))  +`
-  `theme_bw()`


# Quesstion 2
- `plotCounts(dds, gene="Solyc11g028040.1.1", intgroup="dex", returnData=TRUE) %>%`
- `  ggplot(aes(dex,count))+`
- `  geom_boxplot(aes(fill=dex))+`
- `  scale_y_log10() + `
- `  ggtitle("Solyc11g028040.1.1") `


# Quesstion 3
- `plotCounts(dds, gene="Solyc09g089500.2.1", intgroup="dex", returnData=TRUE) %>%`
- `  ggplot(aes(dex,count))+`
- `  geom_boxplot(aes(fill=dex))+`
- `  scale_y_log10() + `
- `  ggtitle("Solyc09g089500.2.1") `


# Question 4
- `ggplot(res)+`
- `  geom_point(aes(x=log10(baseMean), y=log2FoldChange))`
