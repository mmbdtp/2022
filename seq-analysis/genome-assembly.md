---
layout: page
---
# Hybrid and short-read-only assembly of simulated reads
In this exercise, you will take the reads of our novel pathogen and assembly the genome using the short reads alone and a hybrid assembly using both long and short reads. This is to illustrate how differences in sequencing data (namely, read length) will affect the final outcome. We will use these assemblies in subsequent analyses.  

If you are unsure about files and file types, please review [Crash Course Computer Science episode 20](https://www.youtube.com/watch?v=KN8YgJnShPM&list=PL8dPuuaLjXtNlUrzyH5r6jN9ulIgZBpdo&index=21). The [Crash Course Computer Science episode 21](https://www.youtube.com/watch?v=OtDxDvCpPL4&list=PL8dPuuaLjXtNlUrzyH5r6jN9ulIgZBpdo&index=22) is also helpful in understanding compression (.gz, .zip). 

If you complete this exercise (using Galaxy), please attempt the [same process on the command line](/seq-analysis/genome-assembly-cli).

## What is a genome assembler doing?

Genome assemblers assume the following about sequenced reads:

* Reads are resolved into nucleotide bases (ATGC & ambiguous base calls)
* Reads are randomly distributed across the target DNA, and
* Reads are represent an oversampling of the target DNA, such that individual reads repeatedly overlap
* Genome assemblers calculate overlaps between reads and (usually) represent as a graph/network. Then “walk” the graph to determine the original sequence.

Genome assemblers calculate overlaps between reads and (usually) represent as a graph/network. Then “walk” the graph to determine the original sequence.

See [Torsten Seemann’s slides on de novo genome assembly](https://tinyurl.com/torstaseembler)

![Assembly overview]({{site.baseurl}}/seq-analysis/assembler.jpg)

> Whole genome shotgun sequencing: Genome is sheared into small approximately equal sized fragments which are subsequently small enough to be sequenced in both directions followed by cloning. The cloned sequences (reads) are then fed to an assembler (illustrated in Figure 2). b To overcome some of the complexity of normal shotgun sequencing of large sequences such as genomes a hierarchical approach can be taken. The genome is broken into a series of large equal segments of known order which are then subject to shotgun sequencing. The assembly process here is simpler and less computationally expensive. From [Commins, Toft and Fares 2009](http://dx.doi.org/10.1007/s12575-009-9004-1)
 
## What is R1 and R2?
Just as a reminder, many sequencing library preparation kits include an option to generate so-called “paired-end reads“.  Intact genomic DNA is sheared into several million short DNA fragment.  Individual reads can be paired together to create paired-end reads, which offers some benefits for downstream bioinformatics data analysis algorithms.  The structure of a paired-end read is shown here.

![read overview]({{site.baseurl}}/seq-analysis/r1r2.jpg)

“Read 1”, often called the “forward read”, extends from the “Read 1 Adapter” in the 5′ – 3′ direction towards “Read 2” along the forward DNA strand.

“Read 2”, often called the “reverse read”, extends from the “Read 2 Adapter” in the 5′ – 3′ direction towards “Read 1” along the reverse DNA strand.


## How genome assemblers fail perfection
In theory, Genome assembly software with perfect reads of good length will  reconstruct the genome verbatim 

However, Sequencing platform have errors (and cause errors downstream): 

* Struggle with GC rich and/or AT rich DNA.
* Have lower read quality towards the end of reads (5', 3' or both ends)
* Have difficulty reading homopolymers (e.g. AAAAA or TTTTTTT) accurately
* **Have read lengths that does not span repeated sequences in the genome**

 ![Assembly graph]({{site.baseurl}}/seq-analysis/assembly_graph.png)


* Repeats: A segment of DNA that occurs more than once in the genome
* Read length must span the repeat

##### Outcomes of your final contigs

 ![Repeats]({{site.baseurl}}/seq-analysis/repeats.jpg)

> Mate-pair signatures for collapse style mis-assemblies. (a) Two copy tandem repeat R shown with properly sized and oriented mate-pairs. (b) Collapsed tandem repeat shown with compressed and mis-oriented mate-pairs. (c) Two copy repeat R, bounding unique sequence B, shown with properly sized and oriented mate-pairs. (d) Collapsed repeat shown with compressed and mis-linked mate-pairs. From [https://doi.org/10.1186%2Fgb-2008-9-3-r55](https://doi.org/10.1186%2Fgb-2008-9-3-r55)


##### How to span repeats:
* Long reads (ONT, Pacbio)
* Long reads (Sanger)
* Optical mapping
* Hi-C
* Or just don’t! 

## Using Galaxy 

We will be using Galaxy for this exercise, [https://galaxy.quadram.ac.uk/](https://galaxy.quadram.ac.uk/), Please download the sequenced reads, as explained, and upload them into Galaxy. The upload button is the top left (see below)
 
 ![Repeats]({{site.baseurl}}/seq-analysis/UPLOAD.jpg)


## Short read assembly with Shovill
About Shovill: The [SPAdes genome assembler](https://github.com/ablab/spades) has become the de facto standard de novo genome assembler for Illumina whole genome sequencing data of bacteria and other small microbes. 

SPAdes was a major improvement over previous assemblers like Velvet, but some of its components can be slow and it traditionally did not handle overlapping paired-end reads well. 

Shovill is a pipeline which uses SPAdes at its core, but alters the steps before and after the primary assembly step to get similar results in less time. Shovill also supports other assemblers like SKESA, Velvet and Megahit, so you can take advantage of the pre- and post-processing the Shovill provides with those too. 

Warning: Shovill is for isolate data only, primarily small haploid organisms. It will NOT work on metagenomes or larger genomes. Please use Megahit directly instead. See more details at [https://github.com/tseemann/shovill](https://github.com/tseemann/shovill)
 
Use the search in the top left to look for Shovill and then fill in the inputs and launch the job. Make sure that `_R1` and `_R2` as specified correctly! 

![Shovill dialog]({{site.baseurl}}/seq-analysis/shovill.jpg)

Review the output in the right hand history pane. 

The important output files, please review each of these:

* contigs.fa: The final assembly you should use
* contigs.gfa: Assembly graph (spades)
* shovill.log: Full log file for bug reporting

If you have a problem with this process. Here are some results I prepared earlier. 

* [contigs.fa](/seq-analysis/contigs.fa)
* [contigs.gfa](/seq-analysis/contigs.gfa)
* [shovill.corrections](/seq-analysis/shovill.corrections)
* [shovill.log](/seq-analysis/shovill.log)


## Hybrid assembly with Unicyler 

There are different programs for hybrid assembly, with slightly different results. So, why [Unicycler](https://github.com/rrwick/Unicycler)?

* All in one package - Good hybrid assembly
* Can use short read only and bridge gaps with some guesswork 
* A lot of options on how aggressive you want it to join contigs
* Easy install
* Checks for circularisation 

Use the search in the top left to look for Unicyler and then fill in the inputs and launch the job. Make sure that `_R1`, `_R2`, `long reads` are specified correctly! 

![Unicyler dialog]({{site.baseurl}}/seq-analysis/uni.jpg)

*If you run into an error about no `lr`, make sure that the long read input is set as fastqsanger.gz *

Review the output in the right hand history pane. 

At this stage, you may want to ask about what's different about a hybrid assembly?

The important output files:

* assembly.fasta: The final assembly you should use
* assembly.gfa: Assembly graph 
* unicycler.log: Full log file for bug reporting

If you had a problem with generating an assembly with Unicycler. Here are some results I prepared earlier. 

* [long_assembly.fasta](/seq-analysis/long_assembly.fasta)
* [long_assembly.gfa](/seq-analysis/long_assembly.gfa)
* [unicycler.log](/seq-analysis/unicycler.log)