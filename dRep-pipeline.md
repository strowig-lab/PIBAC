# MAG mapping pipeline

## Table of Contents

[Description](#Description)  
[Requirements](#Requirements)  
[Data pre-processing](#Data-pre-processing)  
[MAGs-settings](#MAGs-settings)  
[Mapping](#Mapping)  
[TPM-normalization](#TPM-normalization)  
[Basic-statistics](#Basic-statistics)  

# Requirements
* [BBmap](https://sourceforge.net/projects/bbmap/)
* [samtools](http://samtools.sourceforge.net/)
* [sambamba](http://lomereiter.github.io/sambamba/)


# Data-pre-processing

**1. Demultiplexing and adapter removing**

All reads were processed with Ilumina bcl2fastq Conversion

**2. Quality check of the reads**

Very low quality should be trimmed. Otherwise you do not need to preform quality trimming or any kind of error correction. If you want to trim you data you can just remove the "untrim" parameter in the next step. Please see [bbmap/bbduk documentation](https://jgi.doe.gov/data-and-tools/bbtools/bb-tools-user-guide) for more details.

**3. Removal of contaminated host**

You can use bbmap and the reference pig genome from and assign  the ${PIGgenome} variable.

    # for each Sample ($SampleName) with ReadR1 ($Fastq_R1) and ReadR2 ($Fastq_R2) we preform
    bbmap.sh -Xmx50g usejni=t unpigz=t threads=10 fast=t \
    minratio=0.9 maxindel=3 bwr=0.16 bw=12 fast minhits=2 qtrim=r trimq=10 untrim idtag printunmappedcount kfilter=25 maxsites=1 k=14 \
    in=${Fastq_R1} \
    in2=${Fastq_R2} \
    ref=${PIGgenome} \
    statsfile=${SampleName}_rmhost_filtering.stats \
    outu=${SampleName}_R1_rmhost.fastq.gz \
    outu2=${SampleName}_R2_rmhost.fastq.gz

# MAGs-settings

**1. Select and download MAG collection**

    # only high quality MAGS (comp>90, con<5) hqMAG (recommended resource)
	wget -O PIBAC-hqMAGs-dereplicated_genomes.tar.gz "https://onedrive.live.com/"
	# all mMAG even with medium Quality (comp>50, con<10) to cover full diversity
	wget -O PIBAC-mMAGs.tar.gz "https://onedrive.live.com/"
	

**2. Index PIBAC catalog**

	tar -xzf PIBAC-hqMAGs-dereplicated_genomes.tar.gz
    bbsplit.sh ref=PIBAC-hqMAGs-dereplicated_genomes


# Mapping

For this tutorial we use bbmap for mapping the reads to MAG collection. You can use an other mapper and process the standard output (sam-files) with bbmap to summarize the counts. Please see [bbmap documentation](https://jgi.doe.gov/data-and-tools/bbtools/bb-tools-user-guide) for more details.

    # for each Sample ($SampleName) with ReadR1 ($Fastq_R1) and ReadR2 ($Fastq_R2) we preform:
    bbsplit.sh -Xmx30g unpigz=t threads=${usedCores} minid=0.90 \
    statsfile=${SampleName}.statsfile \
    scafstats=${SampleName}.scafstats \
    covstats=${SampleName}.covstat \
    rpkm=${SampleName}.rpkm \
    sortscafs=f nzo=f \
    in=${SampleName}_R1_rmhost.fastq.gz \
    in2=${SampleName}_R2_rmhost.fastq.gz
