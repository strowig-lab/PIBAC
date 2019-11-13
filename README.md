#  Pig intestinal bacterial collection 

![logo](/images/pibac_logo.png)

## Description

*In-depth cultivation of the pig gut microbiome towards novel bacterial diversity and tailored functional studies*
  - 1,780 MAGs from all-in-one assembly of 295 pig gut metagenomic samples (Xiao, 2016)
  - 38 isolates representing novel species (single draft genomes)
  - representing in total 617 species (hqMAGs-dereplicated_genomes, comp>90%, con<5%)

See [www.dsmz.de/pibac](https://www.dsmz.de/pibac) and our paper for details:

**In-depth cultivation of the pig gut microbiome towards novel bacterial diversity and tailored functional studies**  
David Wylensek and Thomas C. A. Hitch et al. , corresponding author: Thomas Clavel

### External studies providing data:

Xiao, Liang, et al. "A reference gene catalogue of the pig gut microbiome." Nature microbiology 1.12 (2016): 16161. https://doi.org/10.1038/nmicrobiol.2016.161


## Data:

### Metagenome-assembled genomes (MAGs) :

| Description | Size | Link |
|--|--|--|
| representave hqMAGs (n=617) | 400 MB | [PIBAC-hqMAGs-dereplicated_genomes.tar.gz](https://onedrive.live.com/download?cid=36ADEB4B3D109F6F&resid=36ADEB4B3D109F6F%2138671&authkey=AO-S48yf1OvVk8U) | 
| all mMAGs (n=1,780) | 1 GB | [PIBAC-mMAGs.tar.gz](https://onedrive.live.com/download?cid=36ADEB4B3D109F6F&resid=36ADEB4B3D109F6F%2138674&authkey=APp2rvi3v3pLnts) | 
| Annotations by CheckM, dRep-Clustering, GTDB-Tk | 1 MB | [MAG-annotation_CheckM_dRep_GTDB-Tk.tar.gz](https://onedrive.live.com/download?cid=36ADEB4B3D109F6F&resid=36ADEB4B3D109F6F%2138673&authkey=AC-8-4mBr0U5zjg) |

### metagenomic libraries (Raw Data Fastq):

Accession codes of the used gut metagenome sequences:
European Nucleotide Archive: [PRJEB11755](http://www.ebi.ac.uk/ena/data/view/PRJEB11755)

## Pipelines:

![pipeline](/images/pipeline.png)

We recommend the use of [Bioconda](http://bioconda.github.io/)

### Use of the gene catalog (mapping pipeline using the catalog or MAGs)

[Assembly and Binning Pipeline](/assembly-binning-pipeline.md)

[Dereplication and annotation pipeline ](/dRep-pipeline.md)

[Compair to human and mice MAGs](/dRep-pipeline.md)


### Workflows to create by sample MAGs (single wise)

[Code for the generation and clustering of single-wise assembly MAGs](/sMAG-pipeline.md)

[Code for the evaluation of single-wise assembly MAGs versus all-in-one assembly MAGs](/evaluation/README.md)

