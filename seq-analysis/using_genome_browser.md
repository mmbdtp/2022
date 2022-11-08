---
layout: page
---

# Using a genome browser to look at contigs of our genomic data

You should use the assembled contigs we generated earlier, particularly the one generated with Unicycler.

If you had a problem with generating an assembly with Unicycler. Here are some results I prepared earlier. 

* [long_assembly.fasta](/seq-analysis/long_assembly.fasta)
* [long_assembly.gfa](/seq-analysis/long_assembly.gfa)
* [unicycler.log](/seq-analysis/unicycler.log)

If you have having difficulty with the amount of sequence information, try the next few exercises with this short sequence "small_contigs.fasta!. If you feel more confident you may try the "mystery pathogenicity island" - both of these are taken from the long read assembly above. 

* [small_contig.fasta](/seq-analysis/small_contigs.fasta]
* [mystery_island.fasta](/seq-analysis/mystery_island.fasta]

There a number of genome browsers available, we will use [Artemis](https://www.sanger.ac.uk/tool/artemis/). 
For ease of use, you can split the assembly FASTA file (Use the hybrid assembly for this) into seperate files. The FASTA file may look like this:

```
>1
TGATAGCAGCT...
>2 
AGCAGCTAGCA...
```

You can open `Artemis` like any other graphical program. From the command line you can run it with:

```
art my_assembly.fasta
```

You should try the smaller sequence from your assembly first. 

![Artemis with one tracks]({{site.baseurl}}/seq-analysis/artemis.png)

By default you will see 6 tracks. One for each frame (3 forward, 3 reverse). The black ticks are termination codons. A close up of the seqeunce is shown in the bottom panel. 

Try annotating the sequence by clicking and dragging on one of the tracks. `Right Click` > `Create` > `Feature from base range`. You can annotate any string of bases as whatever you like. 
 