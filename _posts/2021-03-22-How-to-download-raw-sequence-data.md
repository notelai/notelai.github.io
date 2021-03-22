---
layout: post
title: Tutorial: How to download raw sequence data from GEO/SRA
subtitle: download raw sequence data
tags: [raw data, test, linux]
---
download some raw sequence data in fastq format from GEO/SRA and run through an appropriate aligner (BWA, TopHat, STAR, etc) and then variant caller (Strelka, etc) or other analysis pipeline. How do we get started?  First, we need the sequence data.#
Determine the SRR number and then download the data at the command-line with:
~~~
$ prefetch -v SRR925811
~~~
Note where the sra file is downloaded (by default to /home/[USER]/ncbi/public/sra/.) and then convert to fastq with something like the following:
~~~
$ fastq-dump --outdir /opt/fastq/ --split-files /home/[USER]/ncbi/public/sra/SRR925811.sra
~~~
This should produce two fastq files (one for R1 and one for R2). That will give you the raw exome sequence data for the T47D cell line. A very similar process should work for any RNAseq samples that you want.

If you want to start with sam/bam files you can use sam-dump instead of fastq-dump. But note that these will still just contain the unaligned raw sequence data. You will still need to run through an aligner and variant caller.
http://www.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=toolkit_doc&f=sam-dump

If you just want to download X number of raw (fastq) reads to standard output from a particular run you can use a command like the following. This can be useful to just take a quick look at some reads, or obtain some reads for testing purposes or just check whether the SRA toolkit is even working for you.
~~~
$ fastq-dump -X 5 -Z SRR925811
~~~



