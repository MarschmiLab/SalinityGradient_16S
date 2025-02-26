# Goals of this folder 

Date: Wed. February 26th, 2025

Question: Is my data good enough? 

1. Make symbolic links of fastq.gz files.  
2. FastQC on those files.  
3. Aggregate a report with multiQC. 
4. Interpret if my data is high enough quality to continue my project. 


## LOAD FASTQC

# Full path: /programs/FastQC-0.12.1/fastqc 
export PATH=/programs/FastQC-0.12.1:$PATH

### Run FASTQC
fastqc /workdir/mls528/testing_repo/data/01_DADA2/01_raw_gzipped_fastqs/*.fastq.gz \
    --threads 8 \
    -o /workdir/mls528/testing_repo/analysis/00_FastQC/fastqc_reports/


## LOAD MULTI QC
export PYTHONPATH=/programs/multiqc-1.15/lib64/python3.9/site-packages:/programs/multiqc-1.15/lib/python3.9/site-packages
export PATH=/programs/multiqc-1.15/bin:$PATH

### Run Multiqc 
multiqc fastqc_reports/ -o multiqc_results/
