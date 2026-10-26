# drosophila-rna-seq-scripts
Scripts used to analyze and visualize RNA-seq data collected by Dr Carlo Breda circa 2020.

# EXPERIMENTAL DESIGN:
Samples s1 to s3 - Group A: elav, 3Mkk; + (Control/WT, no Htt) - 3 replicates
Samples s5 to s6 - Group B: elav, cnkk; + (KMO knockdown (KD), - 2 replicates (s4 unpaired)
Samples s7 to s8 - Group C: elav, vkk; +  (TDO knockdown (KD), -2 replicates (s9 missing)

# NOTE:
Sample s9 was absent from the delivered raw data archive. S4 had only one unpaired read file. These samples were excluded from all downstream analyses.

# DE ANALYSIS COMPARISONS:
1. KMO KD vs Control: s5, s6 vs s1, s2, s3
2. TDO KD vs Control: s7, s8 vs s1, s2, s3

# PIPELINE OVERVIEW:
1.  Directory Setup
2.  Pre-trimming QC (FastQC + MultiQC)
3.  Trimming (Trimmomatic)
4.  Post-trimming QC (FastQC + MultiQC)
5.  Reference Genome & Annotation Download
6.  Genome Indexing (HISAT2)
7.  Alignment (HISAT2)
8.  SAM → Sorted BAM Conversion (samtools)
9.  Read Counting (featureCounts)
10. Differential Expression Analysis (DESeq2)
11. Visualisation (Volcano Plots)
12. Visualisation (PCA Plot + Sample-to-Sample Distance Heatmap)
13. DEG Extraction and CG ID Annotation
14. Proteomics — RNA-seq Overlap Analysis (run locally in RStudio)

# ANNOTATION NOTE:
Steps 5 onwards use the NCBI BDGP6 reference genome (GCF_000001215.4, Release 6 plus ISO1 MT) after the original Canton S assembly (GCA_048772135.1) was found to contain no gene annotation in its GBFF file (only 'source' and 'assembly_gap' features).

# DATA LOSS NOTE: 
On 30/05/2026, scratch storage was wiped by the HPC purge policy. All trimmed files, SAM files, BAM files and counts data were lost. The raw data tar archive was re-downloaded and the pipeline was re-run from Step 3 onwards.
