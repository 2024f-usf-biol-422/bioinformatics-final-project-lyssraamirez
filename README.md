# README for Variant Calling Pipeline for SARS-CoV-2 using Illumina Short Reads

## Author
**Alyssa Ramirez**  
**Email:** amramirez18@dons.usfca.edu  

This project implements a bioinformatics pipeline for analyzing SARS-CoV-2 sequencing data using Illumina short reads, focusing on variant calling, gene annotation, and statistical analysis. The pipeline combines computational tools and R scripts to investigate temporal trends, sampling methods, and population size effects on SARS-CoV-2 RNA detection in wastewater.  

Parts of this pipeline are inspired by the [Data Carpentry Genomics lessons](https://datacarpentry.org/genomics-workshop/) under the [CC-BY 4.0 license](https://creativecommons.org/licenses/by/4.0/).  

---

## Project Structure

The project is organized as follows:  
├── Report.pdf
├── README.md  # Overview of the project
├── Report.Rmd                   # Main RMarkdown file for the report
├── Report_files/                # Folder for supporting files for the knitted report
├── references.bib               # Bibliography file for citations
├── DESCRIPTION                  # Package description and dependencies
├── bioinformatics.csl           # Citation style file
├── Makefile                     # Automates the entire analysis pipeline
├── data/                        # Folder for input data files
│   ├── raw/                     # Raw input data (e.g., FASTQ, VCFs, metadata)
│   ├── processed/               # Processed datasets ready for analysis
│   ├── metadata/                # Metadata files for the dataset
├── output/                      # Folder for analysis outputs
│   ├── distribution_sampling_methods.png   # Distribution of sampling methods
│   ├── normalized_sequencing_coverage.png # Sequencing coverage over time
│   ├── population_size_avg_spotlen.png    # Relationship between population size and average spot length
│   ├── population_vs_rna_detection.png    # Relationship between population size and RNA detection
│   ├── snp_counts_across_genes.png        # SNP counts across genes
│   ├── summary_table_output.png           # Summary table output
│   ├── Sample_report.html                 # Sample HTML report
├── code/                        # Folder for scripts
│   ├── 00_setup_directories.sh  # Bash script to set up directories
│   ├── 01_download_fastq.sh     # Download FASTQ files
│   ├── 02_download_reference.sh # Download reference genome
│   ├── 03_download_annotation.sh# Download annotation files
│   ├── 04_fastqc.sh             # Perform quality control
│   ├── 05_trim.sh               # Trim FASTQ reads
│   ├── 06_bwa_index.sh          # Index reference genome with BWA
│   ├── 07_run_bwa.sh            # Map reads to the reference genome
│   ├── 08_sam_to_bam.sh         # Convert SAM to BAM
│   ├── 09_sort_bam.sh           # Sort BAM files
│   ├── 10_flagstat.sh           # Flag statistics for BAM files
│   ├── 11_bcftools_mpileup.sh   # Generate VCF using BCFtools
│   ├── 12_create_vcf.sh         # Create final VCF
│   ├── 13_filter_vcf.sh         # Filter VCF
│   ├── 14_render_rmarkdown.sh   # Render RMarkdown report
│   └── functions/               # Folder for helper R

│       ├── add_genes_metadata_to_vcfstack.R  # Add gene metadata to VCF
│       ├── assign_gene.R                      # Assign genes to variants
│       ├── extract_genes_from_gff.R           # Extract genes from GFF file
│       ├── parse_tidy_and_stack_vcfs.R        # Parse and stack VCF files
│       └── read_gff.R                         # Read GFF annotation files


## Pipeline Overview  

This pipeline processes SARS-CoV-2 sequencing data from raw FASTQ files to annotated and analyzed VCF files. It incorporates quality control, read alignment, variant calling, and downstream analysis. Key features include:  

- **Sampling Methods**: Comparison of composite vs. grab sampling.  
- **Temporal Trends**: Temporal fluctuation in SARS-CoV-2 RNA detection levels.  
- **Population Effects**: Correlation between population size and RNA detection.  
- **SNP Distribution**: Identification of genomic regions with high variability.  

## Steps in the Analysis

1. **Setup and Preprocessing**  
   - Directory creation using `00_setup_directories.sh`.  
   - Download reference genome and annotation files using `02_download_reference.sh` and `03_download_annotation.sh`.  

2. **Quality Control and Trimming**  
   - Perform quality control with `04_fastqc.sh`.  
   - Trim raw FASTQ files with `05_trim.sh`.  

3. **Mapping and Alignment**  
   - Index the reference genome using `06_bwa_index.sh`.  
   - Map reads to the reference genome using `07_run_bwa.sh`.  
   - Convert SAM to BAM and sort BAM files using `08_sam_to_bam.sh` and `09_sort_bam.sh`.  

4. **Variant Calling**  
   - Generate raw VCF files with `11_bcftools_mpileup.sh`.  
   - Filter VCF files using `13_filter_vcf.sh`.  

5. **Data Analysis**  
   - Annotate and stack VCF files using custom R scripts in `functions/`.  
   - Visualize results and generate tables using R scripts in `Report.Rmd`.  


## Outputs  

### Figures  
- **Distribution of Sampling Methods**: Highlights composite vs. grab sampling differences.  
- **Normalized Sequencing Coverage**: Temporal trends in RNA detection levels.  
- **SNP Counts Across Genes**: Genomic variability.  
- **Population Size and RNA Detection**: Correlation analysis.

### Tables  
- **Summary Table**: Sequencing coverage statistics across sampling methods.  

### Report  
- **PDF Report**: Consolidated findings, analysis, and visualizations.  

---

## Dependencies  

- **Software**:  
  - Bash shell scripts (`bash`).  
  - BWA, SAMtools, BCFtools.  
  - RStudio and RMarkdown.  

- **R Packages**:  
  - `tidyverse`, `ggplot2`, `vcfR`, `dplyr`, `rmarkdown`, `knitr`, `testthat`, `RColorBrewer`, `magrittr`.  

- **LaTeX**: Required for generating PDF reports (e.g., TinyTeX).  

---

## Citation  

If using or referencing this project, please cite:  
**Alyssa Ramirez. (2024). Variant Calling Pipeline for SARS-CoV-2 using Illumina short reads.**  

--- 

## Contact  

For any questions or support, please email **amramirez18@dons.usfca.edu**.
