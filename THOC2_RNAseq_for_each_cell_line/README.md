README.md

### THOC2 RNA-seq Analysis

## Overview
This repository contains scripts, metadata, and processed data for RNA-seq analysis of **THOC2** variants in human cell lines (iPSCs, LCLs, and fibroblasts). The main analysis focuses on **iPSC technical replicates**, but the scripts can be adapted for LCLs and fibroblasts with biological replicates by modifying the sample metadata and input counts files. 

## Reference Data
For the reference data for human genome hg38 was taken from (https://www.ncbi.nlm.nih.gov/datasets/genome/?taxon=9606). 
GeneBank: GCA_000001405.15
File_name: GCA_000001405.15_GRCh38_no_alt_analysis_set.fna
Index file: GCA_000001405.15_GRCh38_no_alt_analysis_set.fna.gz.gzi

The file was too large for GitHub. Please visit https://www.ncbi.nlm.nih.gov/datasets/genome/?taxon=9606 to download the latest files for your analysis. 

## Repository Structure
- `Rmd/` - Analysis scripts
- `data/` - Processed input data
- `results/` - Output plots for each cell line

## Folder Structure
THOC2_RNAseq/
│
├── data/
│ ├── counts/ # Gene and transcript counts
│ │ ├── fibroblast/
│ │ │ ├── gene.counts.txt
│ │ │ └── transcript.counts.txt
│ │ ├── iPSC/
│ │ │ ├── gene.counts.txt
│ │ │ └── transcript.counts.txt
│ │ └── LCL/
│ │ ├── gene.counts.txt
│ │ └── transcript.counts.txt
│ │
│ ├── metadata/ # Sample metadata
│ │ ├── pdata_iPSC.csv
│ │ ├── pdata_LCL.csv
│ │ └── pdata_fibroblast.csv
│ │
│ └── refData/ # Reference transcriptome
│ │ └── GCA_000001405.15_GRCh38_no_alt_analysis_set.fna.gz
│
├── results/ # Analysis outputs
│ ├── fibroblast/
│ │ ├── DEGs_biological_replicates/
│ │   ├── GSEA/
│ │   ├── Deletion_vs_WT_allGenes.tsv
│ │   └── limma_decideTests_allGenes.xlsx
│ │ └── images/
│ │   ├── Correlation/
│ │   └── QC/
│ │
│ ├── iPSC/
│ │ ├── DEGs_biological_replicates/
│ │ ├── DEGs_technical_replicates/
│ │ │ └── GSEA, limma, TSV files
│ │ └── images/
│ │ ├── Correlation/
│ │ ├── Pluripotency/
│ │ ├── QC/
│ │ ├── Rloop/
│ │ └── TREX_complex/
│ │
│ └── LCL/
│ │ ├── DEGs_biological_replicates/
│ │   ├── GSEA/
│ │   ├── Missense_vs_WT_allGenes.tsv
│ │   └── limma_decideTests_allGenes.xlsx
│ │ └── images/
│ │   ├── Correlation/
│ │   └── QC/
│ 
└── THOC2_correlation_iPSC_LCL_Fibro_SA.Rmd # Main analysis script


## Setup
Required R Packages

The RNA-seq analysis was performed in R using the following packages for data processing, statistical analysis, visualization, and functional enrichment analysis:

Package	                Purpose
tidyr	                Data tidying and reshaping
dplyr	                Data manipulation and filtering
reshape2	            Data reshaping for plotting and heatmaps
data.table	            Efficient handling of large datasets
tximeta	                Import and manage transcript quantification data from Salmon
SummarizedExperiment	Data structure for storing RNA-seq counts and metadata
limma	                Linear modeling and differential expression analysis
edgeR	                RNA-seq normalization and differential expression analysis
RColorBrewer	        Color palettes for plots
ggplot2	                Data visualization
pheatmap	            Heatmap visualization
ggrepel	                Non-overlapping text labels in plots
rtracklayer	            Import/export genomic annotation files
biomaRt	                Gene annotation and ID conversion
knitr	                R Markdown report generation
openxlsx	            Reading and writing Excel files
org.Hs.eg.db	        Human gene annotation database
tibble	                Modern data frame structure
readxl	                Reading Excel files
msigdbr	                MSigDB gene sets for enrichment analysis
clusterProfiler	        Gene set enrichment analysis (GSEA/ORA)
magrittr	            Pipe operator for cleaner code (%>%)
stringr	                String manipulation
rgl	                    3D visualization
kableExtra	            Formatted tables in R Markdown


Install CRAN packages:
```{r}
install.packages(c(
  "tidyr","dplyr","reshape2","data.table","RColorBrewer","ggplot2",
  "pheatmap","VennDiagram","ggrepel","knitr","openxlsx","tibble",
  "readxl","magrittr","stringr","rgl","kableExtra"
))
```

```{r}
Install Bioconductor packages:

if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install(c(
  "tximeta","SummarizedExperiment","limma","edgeR","rtracklayer",
  "biomaRt","org.Hs.eg.db","msigdbr","clusterProfiler"
))
```