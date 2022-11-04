---
layout: page
---

# Hybrid and short-read-only assembly of sequenced reads
Let’s look at the impact of read length (long read vs short read) on genome assembly. 
In doing so I will also show you how to run the software and assess the output.

If you are unsure about the command line, please review [Crash Course Computer Science episode 22](https://www.youtube.com/watch?v=4RPtJ9UyHS0&list=PL8dPuuaLjXtNlUrzyH5r6jN9ulIgZBpdo&index=23). The [episode on operating systems](https://www.youtube.com/watch?v=26QPDBe-NB8&list=PL8dPuuaLjXtNlUrzyH5r6jN9ulIgZBpdo&index=19) will also help you understand `Unix` a little better. 

### Short read assembly with Shovill
Is Shovill installed? Please see the [Installing software](seq-analysis/installing) section.

We can run Shovill with:
```
shovill  --R1 novel-pathogen_R1.fastq.gz  \
         --R2 novel-pathogen_R2.fastq.gz   \
         --outdir short_read_only --force
```

The final output: 

```
[shovill] Repaired 0 contigs from spades.fasta at 0 positions.
[shovill] Assembly is 4938311, estimated genome size was 4712883 (+4.78%)
[shovill] Using genome graph file 'spades/assembly_graph_with_scaffolds.gfa' => 'contigs.gfa'
[shovill] Walltime used: 3 min 6 sec
[shovill] Results in: /home/ubuntu/code/mmbdtp.github.io/temp/short_read_only
[shovill] Final assembly graph: /home/ubuntu/code/mmbdtp.github.io/temp/short_read_only/contigs.gfa
[shovill] Final assembly contigs: /home/ubuntu/code/mmbdtp.github.io/temp/short_read_only/contigs.fa
[shovill] It contains 297 (min=75) contigs totalling 4938311 bp.
[shovill] More correct contigs is better than fewer wrong contigs.
[shovill] Done.
```

The contents of the `short_read_only` folder: 

```
(shovill) ubuntu@chomp:~/code/mmbdtp.github.io/temp$ ls short_read_only/ -hl
total 15M
-rw-rw-r-- 1 ubuntu ubuntu 4.9M Nov  2 17:01 contigs.fa
-rw-rw-r-- 1 ubuntu ubuntu 4.8M Nov  2 17:01 contigs.gfa
-rw-rw-r-- 1 ubuntu ubuntu    0 Nov  2 17:01 shovill.corrections
-rw-rw-r-- 1 ubuntu ubuntu 365K Nov  2 17:01 shovill.log
-rw-rw-r-- 1 ubuntu ubuntu 4.8M Nov  2 17:01 spades.fasta
```

The important output files:

* contigs.fa: The final assembly you should use
* contigs.gfa: Assembly graph (spades)
* shovill.log: Full log file for bug reporting

## Hybrid assembly with Unicyler 

Is Unicyler installed? Please see the [Installing software](seq-analysis/installing) section. 

We can run Unicyler with:
```
unicycler -1 novel-pathogen_R1.fastq.gz \
  -2 novel-pathogen_R2.fastq.gz \
  -l novel-pathogen-long-reads.fastq.gz  \
  -o hybrid_assembly
```


The contents of the `hybrid_assembly` folder: 

```
001_spades_graph_k027.gfa
001_spades_graph_k053.gfa
001_spades_graph_k071.gfa
001_spades_graph_k087.gfa
001_spades_graph_k099.gfa
001_spades_graph_k111.gfa
001_spades_graph_k119.gfa
001_spades_graph_k127.gfa
002_depth_filter.gfa
003_overlaps_removed.gfa
004_long_read_assembly.gfa
005_bridges_applied.gfa
006_final_clean.gfa
assembly.fasta
assembly.gfa
unicycler.log
```

The important output files:

* assembly.fasta: The final assembly you should use
* assembly.gfa: Assembly graph 
* unicycler.log: Full log file for bug reporting