# Creation of the gene catalog

## Table of Contents

[Description](#Description)  
[Requirements](#Requirements)   
[Assembly](#Assembly)  
[Binning](#Binning)  


# Description

![iMGMC-creation-pipeline](/images/iMGMC-creation-pipeline.png)

# Requirements
* [BBmap](https://sourceforge.net/projects/bbmap/)
* [Megahit](https://github.com/voutcn/megahit/releases)
* [BWA](http://bio-bwa.sourceforge.net/)
* [sambamba](http://lomereiter.github.io/sambamba/)
* [metaBAT](https://bitbucket.org/berkeleylab/metabat)


# Assembly

All reads were used for an all-in-one assembly with Megahit on a SGI UV-2000

    megahit \
    --k-list 21,27,33,37,43,55,63,77,83,99 \
    --min-count 5 \
    --num-cpu-threads 256 \
    --out-dir Megahit-${SampleName} \
    -1 ${SampleName1}_R1_rmhost.fastq.gz \
    -2 ${SampleName1}_R2_rmhost.fastq.gz \
	-1 ${SampleName2}_R1_rmhost.fastq.gz \
    -2 ${SampleName2}_R2_rmhost.fastq.gz \
    [ ... ]
	-1 ${SampleName298}_R1_rmhost.fastq.gz \
    -2 ${SampleName298}_R2_rmhost.fastq.gz

    # filter, sort and rename contigs
	dedupe.sh sort=d in=final.contigs.fa out=stdout.fasta minscaf=1000 | \
	rename.sh in=stdin.fasta out=PIBAC-sort-rename_contigs.fasta prefix="contig"
	
# Binning

**1. Create index for BWA mapping**

	bwa index MegaHIT-sort-rename_contigs.fasta

**2. BWA mapping of all libraries to Contigs**

    # for each Sample ($SampleName) with ReadR1 ($Fastq_R1) and ReadR2 ($Fastq_R2) we preform:
	bwa mem -t 12 MegaHIT-sort-rename_contigs.fasta ${Fastq_R1} ${Fastq_R2} > ${SampleName}.sam

**3. Covert sam to ordered bam file**

	# each Sample ${SampleName}.sam
	sambamba view -t 12 -S -f bam ${SampleName}.sam | sambamba sort -t 12 -m 60G -o ${SampleName}.bam

**4. Calculating abundance table with MetaBAT from all bam-files located in folder ${BamDir}**

	jgi_summarize_bam_contig_depths \
	--outputDepth depth.txt \
	--pairedContigs paired.txt \
	--minContigLength 1000 \
	--minContigDepth 2 \
	${BamDir}/*.bam

**5. Run MetaBAT**

	metabat --keep -t 30 \
	--minClsSize 200000 \
	--verysensitive \
	-B 100 \
	-p paired.txt \
	-i PIBAC-sort-rename_contigs.fasta \
	-a depth.txt  \
	-o MetaBAT-binning


## Dereplication with isolated strains:

[dRep pipeline](/dRep-pipeline.md)
