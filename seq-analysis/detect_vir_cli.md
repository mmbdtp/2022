---
layout: page
---
# Detecting virulence factors - CLI
Is `abricate` installed? Please see the [Installing software](seq-analysis/installing) section. 

If you had a problem with generating an assembly. Here are some results I prepared earlier. 

* [long_assembly.fasta](/seq-analysis/long_assembly.fasta)

Try using `abricate` on the command line with the different databases

```
abricate oh/assembly.fasta 
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
#FILE	SEQUENCE	START	END	GENE	COVERAGE	COVERAGE_MAP	GAPS	%COVERAGE	%IDENTITY	DATABASE	ACCESSION	PRODUCT
test_sample	1	610199	614052	entF	1-3854/3882	===============	0/0	99.28	95.67	vfdb	NP_752604	(entF) enterobactin synthase multienzyme complex component ATP-dependent [Enterobactin (VF0228)] [Escherichia coli CFT073]
test_sample	1	615427	616242	fepC	1-816/816	===============	0/0	100.00	97.30	vfdb	NP_752606	(fepC) ferrienterobactin ABC transporter ATPase [Enterobactin (VF0228)] [Escherichia coli CFT073]
test_sample	1	616239	617231	fepG	1-993/993	===============	0/0	100.00	94.06	vfdb	NP_752607	(fepG) iron-enterobactin ABC transporter permease [Enterobactin (VF0228)] [Escherichia coli CFT073]
```

