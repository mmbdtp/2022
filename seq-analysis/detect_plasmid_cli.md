---
layout: page
---

# Detecting plasmids - CLI

Is `abricate` installed? Please see the [Installing software](seq-analysis/installing) section. 

If you had a problem with generating an assembly. Here are some results I prepared earlier. 

* [long_assembly.fasta](/seq-analysis/long_assembly.fasta)

Try using `abricate` on the command line with the different databases

```
abricate oh/assembly.fasta --db plasmidfinder
```


You can use `--list` to see what databases are available. 

```
abricate --list 
DATABASE	SEQUENCES	DATE
argannot	1749	2018-Jul-16
card	2220	2018-Jul-16
ecoh	597	2018-Jul-16
ncbi	4324	2018-Jul-16
plasmidfinder	263	2018-Jul-16
resfinder	2280	2018-Jul-16
vfdb	2597	2018-Jul-16

```

The output will be the same as with the web-based example. What does it mean? Try using `grep` or `cut` to filter the results.

```
Using database plasmidfinder:  263 sequences -  2018-Jul-16
#FILE	SEQUENCE	START	END	GENE	COVERAGE	COVERAGE_MAP	GAPS	%COVERAGE	%IDENTITY	DATABASE	ACCESSION	PRODUCT
Processing: oh/assembly.fasta
Found 1 genes in oh/assembly.fasta
oh/assembly.fasta	2	8821	8951	ColRNAI_1	1-130/130	========/======	1/1	100.00	87.02	plasmidfinder	DQ298019	ColRNAI_1__DQ298019
```

