---
layout: page
---

# Detecting plasmids and prophages
There are a number of tools for detecting plasmids and prophage. Some of these are on galaxy. You can apply these tools to your assembled genome.

If you had a problem with generating an assembly. Here are some results I prepared earlier. 

* [long_assembly.fasta](/seq-analysis/long_assembly.fasta)

I have provided another plasmid genome, which is totally unrelated to our data. You can run this too to see how results can differ with the various tools:

* [some_plasmid.fasta](/seq-analysis/some_plasmid.fasta)

### Plasmid detection 

* [MOB-Suite](https://github.com/phac-nml/mob-suite). Try this one.
* [Plasmidfinder](https://cge.food.dtu.dk/services/PlasmidFinder/) - Web tool. Try this one.
* [Abricate](https://github.com/tseemann/abricate) (plasmidfinder). Try this one.
* [ARIBA](https://github.com/sanger-pathogens/ariba) (plasmidfinder)
* [PLACNET](https://castillo.dicom.unican.es/upload/) - Web tool. Try this one.
* [COPLA](https://castillo.dicom.unican.es/copla_guide/) - Web tool. Try this one.
* [PlasFlow](https://github.com/smaegol/PlasFlow)

### Phages

* [PHAST/PHASTER](https://phaster.ca/) - Web tool. Try this one.
* [VirSorter 2](https://github.com/jiarong/VirSorter2)
* [DeepVirFinder](https://github.com/jessieren/DeepVirFinder)

#### About PHASTER

PHASTER is a web based tool and can be quite slow. We are showing it as how you can approach characterising a genomic region of interest. 

Have a look at an example [https://phaster.ca/submissions/NC_000913](https://phaster.ca/submissions/NC_000913)

How PHASTER works - Annotation
* Glimmer, tRNAscan-SE, ARAGORN
* DBSCAN for finding clustered genes

How PHASTER works - Finding prophages
* At least four viral genes
* Cumulative length of the gaps between component clusters
* Number and proportion of genes matching known prophage genes
* Presence of blast hits that match a high proportion of a particular phage strain’s known genes
* Presence of IS and viral genes with key functions including integrases transposases, and structural genes.

Arndt D, Marcu A, Liang Y, Wishart DS. PHAST, PHASTER and PHASTEST: Tools for finding prophage in bacterial genomes. Brief Bioinform. 2019;20(4):1560-1567. doi:[10.1093/bib/bbx121](https://academic.oup.com/bib/article/20/4/1560/4222653)

