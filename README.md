<img width="146" height="25" alt="image" src="https://github.com/user-attachments/assets/0f2b24c9-7a6d-463b-9df4-3901eafd2adb" /># viral-metagenomics-workflow

This script is for analysing viral metagenomic sequencing data.

## Environment setup

Use conda to create a separate environment for each software package according to its instructions.

> This is a small test intended for studying the workflow.

## Step 1: Download raw sequencing data

Download the raw sequencing data according to your target article/project:

```bash
prefetch --progress --output-directory /yourdirectory/public/PRJXXXXXX/
```

Output data type: `*.sra`

## Step 2: Convert SRA to FASTQ

Make sure the variables `sra`, `FASTQ`, `SCRATCH`, and `THREADS` are set before running:

```bash
fasterq-dump "$sra" -O "$FASTQ" -t "$SCRATCH" -e "$THREADS" -f
```

## Step 3: run esviritu

EsViritu -r '$fqdir/${j}_1.fastq.gz' '$fqdir/${j}_2.fastq.gz' \
-s '$j' -o '$outdir/$j' \
-p paired -q True -t 20 --keep True --db '$db' \
> '$outdir/logs/${j}.log' 2> '$outdir/logs/${j}.err'"


