---
layout: page
---

# Perform QC and compare hybrid and short-read-only assemblies

If you have a problem with generating an assembly with Shovill. Here are some results I prepared earlier. 

* [contigs.fa](/seq-analysis/contigs.fa)
* [contigs.gfa](/seq-analysis/contigs.gfa)
* [shovill.corrections](/seq-analysis/shovill.corrections)
* [shovill.log](/seq-analysis/shovill.log)

## Exercise: Assessing genome assembly quality 
Many tools are available that assess sequence quality through read alignment, k-mer counting, gene finding, and other methods. 
Your exercise now is to compare and contrast the  hybrid and short-read-only assemblies we prepared earlier  using methods like QUAST, webBlast a contig, Kraken, or looking at assembly graph with Bandage.

##### Contiguity

* Less contigs, Longer contigs
* N50, avg. contig length, number of contigs etc.
* Try [QUAST](https://quast.sourceforge.net/quast.html)

##### Completeness

* Compare to reference genome (How to find a reference genome? Start with [web BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi) )
* Assume a genome should have single copy essential genes
* [MLST](https://github.com/tseemann/mlst) intact?
* [BUSCO](https://busco.ezlab.org/) panel
* [CheckM](https://ecogenomics.github.io/CheckM) panel

##### Correctness 

* Assembly free from errors
* Mis-joins
* Collapsed repeats
* Duplication artefacts 
* False SNPs, InDels
* Compare to reference genome 
* Map original reads back to assembled contigs
* Structural rearrangement tools - Socru

##### Contamination 

Check for contamination too with [Kraken/Bracken](https://ccb.jhu.edu/software/bracken/)

