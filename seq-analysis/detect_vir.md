---
layout: page
---
# Detecting virulence factors and AMR

If you had a problem with generating an assembly. Here are some results I prepared earlier. 

* [long_assembly.fasta](/seq-analysis/long_assembly.fasta)

##### In this exercise, use the Galaxy or other web based tools to locate virulence factors and anitmicrobial resistance in a genome. 

With the decreasing costs, whole genome sequencing has become a viable antimicrobial resistance surveillance tool. Several methods and tools have been published in recent years for detecting genetic determinants of antimicrobial resistance from whole-genome sequencing (WGS) and whole-metagenome sequencing (WMS) data. 

Each of these tools are performing some kind of alignment or search in your sequence of interest. The program are looking for known virulence/AMR genes in published databases. The tools may accept sequence reads or assembled contigs are input. The databases are build with slightly different so the results may not be the same when using different tools. See review for more details [Boolchandani, D'Souza & Dantas, (2019)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6525649/).

The tool and the database are usually detacted. So you can run `ARIBA` and `abricate` (tools) with the CARD database. 

It is easy to believe that running your sequence of interest against as many databases are possible will give you the best information. It may not. You may wind up with a number of conflicting reports and no way to decide which one is correct. You must understand your chosen databases and determine whether it is suitable for your work. 

There are numerous databases for different gene panels - AMR, virulence, serotype, etc.

* [NCBI AMRFinderPlus](https://journals.asm.org/doi/10.1128/AAC.00483-19)
* [CARD](https://academic.oup.com/nar/article/45/D1/D566/2333912)
* [Resfinder](https://academic.oup.com/jac/article/67/11/2640/707208)
* [ARG-ANNOT](https://journals.asm.org/doi/10.1128/AAC.01310-13)
* [VFDB](https://academic.oup.com/nar/article/44/D1/D694/2503049)
* [PlasmidFinder](https://journals.asm.org/doi/10.1128/AAC.02412-14)
* [EcOH](https://www.microbiologyresearch.org/content/journal/mgen/10.1099/mgen.0.000064)
* [MEGARES 2.00](https://academic.oup.com/nar/article/48/D1/D561/5624973)

If you have a particular interest in AMR, please review the content from this 
[Workshop on Antimicrobial Resistance](https://www.climb.ac.uk/amr-workshop/)


#### Software to try

In Galaxy try:

* [abricate](https://github.com/tseemann/abricate) - with different databases

What does the output actually mean? See the documentation, [abricate](https://github.com/tseemann/abricate)

```
#FILE	SEQUENCE	START	END	GENE	COVERAGE	COVERAGE_MAP	GAPS	%COVERAGE	%IDENTITY	DATABASE	ACCESSION	PRODUCT
test_sample	1	610199	614052	entF	1-3854/3882	===============	0/0	99.28	95.67	vfdb	NP_752604	(entF) enterobactin synthase multienzyme complex component ATP-dependent [Enterobactin (VF0228)] [Escherichia coli CFT073]
test_sample	1	615427	616242	fepC	1-816/816	===============	0/0	100.00	97.30	vfdb	NP_752606	(fepC) ferrienterobactin ABC transporter ATPase [Enterobactin (VF0228)] [Escherichia coli CFT073]
test_sample	1	616239	617231	fepG	1-993/993	===============	0/0	100.00	94.06	vfdb	NP_752607	(fepG) iron-enterobactin ABC transporter permease [Enterobactin (VF0228)] [Escherichia coli CFT073]
```
N.B. The co-ordinates in your genome may not match the co-ordinates above

Can you locate these genes in `Artemis`? Use the automated annotation - Do these annotations agree?

Other online tools you can try, include: 

* FimTyper: [https://cge.food.dtu.dk/services/FimTyper/](https://cge.food.dtu.dk/services/FimTyper/)
* ResFinder: [https://cge.food.dtu.dk/services/ResFinder/](https://cge.food.dtu.dk/services/ResFinder/)

Using these tools what can you say about the genome?
