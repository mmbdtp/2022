---
layout: page
---

# Assess the quality of some other (provided) assembled genomes. 

The exercise is to download some assembled draft genomes and assess if they pass routine quality control. 

*The genomes are available at [https://zenodo.org/record/7344094](https://zenodo.org/record/7286288)*

You can directly download them with wget or similar. 

```
wget https://zenodo.org/record/7344094/files/additional_genomes_for_qc.zip
```

The files are FASTA (they are plain text) inside the zip file. There are eight genomes.

Each FASTA file will look something like this. There will be multiple contigs, one after the other. Each with a fasta header (`>NODE_XXXX`) followed by the nucleotide sequence (`ATGC`).

```
>NODE_126_length_2252_cov_16.6409_ID_251
CAGCGTGGACTGATGTTCAG......
>NODE_22_length_135487_cov_12.0245_ID_43
GGCCGAGGCTCCCCACCGGCGCGGG....
>NODE_68_length_16957_cov_12.5198_ID_135
TGGTGTTGGTGCCAACGGCCTGACC...
>NODE_16_length_182200_cov_11.9821_ID_31
GCCGCTTTTTCGCGTTGCTTAATCT...
```

You can assess the assemblies anyway you like, but try to assess:

* Contiguity
* Completeness
* Correctness
* Contamination

For more details on which tools you can use see the section, [perform QC and compare hybrid and short-read-only assemblies](/seq-analysis/assembly_qc)

Try to create a table of your assessment (with better explanations), like the one below:

| Sample name | Pass/Fail | Reason |
|-------------|-----------|--------|
| sample_1    |  Yes  |     |
| sample_2    |  No         |        |
| sample_3    | Maybe          |        |
| sample_4    | I don't know         |        |
| sample_5    | Could you repeat the question?          |        |
| sample_6    |         |        |
| sample_7    |           |        |
| sample_8    |           |        |