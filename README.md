[![DOI](https://zenodo.org/badge/195467054.svg)](https://zenodo.org/badge/latestdoi/195467054)

#  In-depth cultivation of the pig gut microbiome towards novel bacterial diversity and tailored functional studies


![logo](/images/pibac_logo.png)

## Description

*Extensive cultivation of the pig gut microbiome identifies novel bacterial diversity and functions and enables tailored functional studies*
  - 1,780 MAGs from all-in-one assembly of 295 pig gut metagenomic samples (Xiao, 2016)
  - 38 isolates representing novel species (single draft genomes)
  - representing in total 617 species (hqMAGs-dereplicated_genomes, comp>90%, con<5%)

See [www.dsmz.de/pibac](https://www.dsmz.de/pibac) and our paper for details:

**A collection of bacterial isolates from the pig intestine reveals functional and taxonomic diversity.**  
David Wylensek, Thomas C. A. Hitch, Thomas Riedel, Afrizal Afrizal, Neeraj Kumar, Esther Wortmann, Tianzhe Liu, Saravanan Devendran, Till R. Lesker, Sara B. Hernández, Viktoria Heine, Eva M. Buhl, Paul M. D’Agostino, Fabio Cumbo, Thomas Fischöder, Marzena Wyschkon, Torey Looft, Valeria R. Parreira, Birte Abt, Heidi L. Doden, Lindsey Ly, João M. P. Alves, Markus Reichlin, Krzysztof Flisikowski, Laura Navarro Suarez, Anthony P. Neumann, Garret Suen, Tomas de Wouters, Sascha Rohn, Ilias Lagkouvardos, Emma Allen-Vercoe, Cathrin Spröer, Boyke Bunk, Anja J. Taverne-Thiele, Marcel Giesbers, Jerry M. Wells, Klaus Neuhaus, Angelika Schnieke, Felipe Cava, Nicola Segata, Lothar Elling, Till Strowig, Jason M. Ridlon, Tobias A. M. Gulder, Jörg Overmann & Thomas Clavel  
Nature Communications volume 11, Article number: 6389 (2020) 
[https://doi.org/10.1038/s41467-020-19929-w](https://doi.org/10.1038/s41467-020-19929-w)

### External studies providing data:  
Xiao, Liang, et al. "A reference gene catalogue of the pig gut microbiome." Nature Microbiology 1.12 (2016): 16161. https://doi.org/10.1038/nmicrobiol.2016.161

## Data:

### Metagenome-assembled genomes (MAGs) : [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4075024.svg)](https://doi.org/10.5281/zenodo.4075024)

| Description | Size | Link |
|--|--|--|
| Representative hqMAGs (n=617) | 400 MB | [PIBAC-hqMAGs-dereplicated_genomes.tar.gz](https://zenodo.org/record/4075024/files/PIBAC-hqMAGs-dereplicated_genomes.tar.gz?download=1) | 
| All mMAGs (n=1,780) | 1 GB | [PIBAC-mMAGs.tar.gz](https://zenodo.org/record/4075024/files/PIBAC-mMAGs.tar.gz?download=1) | 
| Annotations by CheckM, dRep-Clustering, GTDB-Tk | 1 MB | [MAG-annotation_CheckM_dRep_GTDB-Tk.tar.gz](https://zenodo.org/record/4075024/files/MAG-annotation_CheckM_dRep_GTDB-Tk.tar.gz?download=1) |

### metagenomic libraries (Raw Data Fastq):

Accession codes of the used gut metagenome sequences:
European Nucleotide Archive: [PRJEB11755](http://www.ebi.ac.uk/ena/data/view/PRJEB11755)

## Phylogenetic Tree:

Tree was constucted from GTDB-Tk marker genes, including GTDB-Tk taxonomy information and ANI scores to the GTDB reference genomes.

![tree](/images/Fig-4_GitHub.png)

## Pipelines:

We recommend the use of [Bioconda](http://bioconda.github.io/)

### Use of the gene catalog (mapping pipeline using the catalog or MAGs)

[Assembly and Binning Pipeline](/assembly-binning-pipeline.md)

[Dereplication and annotation pipeline](/dRep-pipeline.md)
