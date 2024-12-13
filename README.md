### Alyssa Ramirez
### amramirez18@dons.usfca.edu
# README for Variant Calling Pipeline for SARS-CoV-2 using Illumina short reads
Parts of this pipeline approach are based on the pipeline described in the [Data Carpentry Genomics lessons](https://datacarpentry.org/genomics-workshop/), which are made available under a [CC-BY 4.0 license](https://creativecommons.org/licenses/by/4.0/).

# Overall structure format
├── README.md                    # Overview of the project
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
│   ├── Report.html                        # Knitted HTML version of the report
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
│   └── functions/               # Folder for helper R scripts
│       ├── add_genes_metadata_to_vcfstack.R  # Add gene metadata to VCF
│       ├── assign_gene.R                      # Assign genes to variants
│       ├── extract_genes_from_gff.R           # Extract genes from GFF file
│       ├── parse_tidy_and_stack_vcfs.R        # Parse and stack VCF files
│       └── read_gff.R                         # Read GFF annotation files
