---
layout: page
---

# Manually annotate a sequence using web based homology searches

If you had a problem with generating an assembly with Unicycler. Here are some results I prepared earlier. 

* [long_assembly.fasta](/seq-analysis/long_assembly.fasta)
* [long_assembly.gfa](/seq-analysis/long_assembly.gfa)
* [unicycler.log](/seq-analysis/unicycler.log)

If you have having difficulty with the amount of sequence information, try the next few exercises with this short sequence "small_contigs.fasta". If you feel more confident you may try the mystery pathogenicity island, "mystery_island.fasta" - both of these are taken from the long read assembly above. 

* [small_contig.fasta](/seq-analysis/small_contigs.fasta)
* [mystery_island.fasta](/seq-analysis/mystery_island.fasta)

Using a combination different tools, try to assign a function to the genes you have predicted. What can you say about the genome regions?

There are web-based tools for you to use such as: 

* Web BLAST - [https://blast.ncbi.nlm.nih.gov/Blast.cgi](https://blast.ncbi.nlm.nih.gov/Blast.cgi)
* [https://www.ebi.ac.uk/Tools/hmmer/](https://www.ebi.ac.uk/Tools/hmmer/)
* [https://www.ebi.ac.uk/interpro/result/InterProScan/#table](https://www.ebi.ac.uk/interpro/result/InterProScan/#table)

Try to save your findings in `Artemis` by editing the different features. You may want to use fields like `/note`, `/gene`, or `/product`. 