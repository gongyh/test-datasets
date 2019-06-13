# test-datasets `porepatrol`
Test data to be used for automated testing with the [nf-core/porepatrol](https://github.com/nf-core/porepatrol) pipeline.

## Content of this repository

`nanopore_reads.fastq.gz`: Basecalled ONT reads, gzipped. 

## Dataset origin

This dataset was obtained from:

https://melbourne.figshare.com/articles/Basecalled_ONT_reads/5170843, by Ryan Wick.

The sample is from a bacteria, sequenced with MinION, and basecalled with Albacore. 

I downloaded file `barcode04.fastq.gz`

I subsampled to 0.5% with seqtk:

```bash
gunzip barcode04.fastq.gz
seqtk sample barcode04.fastq 0.005 > nanopore_reads.fastq
gzip nanopore_reads.fastq
```


## Expected output

Running the pipeline locally with the default parameters:

```bash
nextflow run porepatrol --reads nanopore_reads.fastq.gz 
```

The number of reads and number of bases are summarized in `results/read_summary/read_summary.txt`:


* Input                Number of reads   35.0
* After adapter chop   Number of reads   35.0
* After filtering      Number of reads   26.0
* Input                Total bases       629,487.0
* After adapter chop   Total bases       626,738.0
* After filtering      Total bases       465,573.0



