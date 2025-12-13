## 10X 分析工具CellRanger学习

### cellranger count

> 官方教程：https://www.10xgenomics.com/support/software/cell-ranger/latest/tutorials/cr-tutorial-ct

`cellranger count` 是 10x Genomics 官方用于**单细胞 RNA-seq（scRNA-seq）数据定量分析**的核心命令，主要功能是将单细胞测序的原始 fastq 文件与参考基因组比对，生成细胞级别的基因表达矩阵。
