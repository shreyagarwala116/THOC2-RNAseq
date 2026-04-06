README.md

# THOC2 RNA-seq Analysis - for correlation between variant cell-types

## Overview
Analysis of RNA-seq data from iPSCs, LCLs, and fibroblasts with THOC2 variants.

## Repository Structure
- `Rmd/` - Analysis scripts
- `data/` - Processed input data
- `images/` - Output plots
- `DEGs/` - Differentially expressed gene lists

## Reference Data
For the reference data for human genome hg38 was taken from (https://www.ncbi.nlm.nih.gov/datasets/genome/?taxon=9606). 
GeneBank: GCA_000001405.15
File_name: GCA_000001405.15_GRCh38_no_alt_analysis_set.fna
Index file: GCA_000001405.15_GRCh38_no_alt_analysis_set.fna.gz.gzi

The file was too large for GitHub. Please visit https://www.ncbi.nlm.nih.gov/datasets/genome/?taxon=9606 to download the latest files for your analysis. 

## Setup
Install required R packages:

```r
install.packages(c(
  "tidyr","dplyr","reshape2","data.table","tximeta","SummarizedExperiment",
  "edgeR","RColorBrewer","ggplot2","pheatmap","ggrepel","rtracklayer",
  "knitr","openxlsx","tibble","readxl","rgl","kableExtra"
))
```