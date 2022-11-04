---
layout: page
---

# Information for instructors

This is how the reads for the *novel pathogen* was produced. Reads were simulated from these original sequences:

* [Original plasmid sequence](/seq-analysis/plasmid_pdiarrX.fasta)
* [Original chromosome sequence](/seq-analysis/vr50.fasta)

The chromosome is *E. coli* VR 50 ([CP011134](https://www.ncbi.nlm.nih.gov/nuccore/CP011134.1)), described here [https://pubmed.ncbi.nlm.nih.gov/25667270/](https://pubmed.ncbi.nlm.nih.gov/25667270/). [Genbank file is here](/seq-analysis/vr50.gbk) if needed.


*Reads are available at [https://zenodo.org/record/7286288](https://zenodo.org/record/7286288)*

## Installing software 

```
mamba install -y -c bioconda art
mamba create -y -n badread badread
conda install python-edlib -y
```

## Simulating the short reads 
Used `art` for illumina

```
art_illumina -ss HS25  -i vr50.fasta  -p -l 150 -f 40 -m 200 -s 10 -o chromo --rndSeed 200 -na
art_illumina -ss HS25  -i plasmid_pdiarrX.fasta  -p -l 150 -f 60 -m 200 -s 10 -o plasmid --rndSeed 200 -na
gzip -c chromo1.fq plasmid1.fq  > novel-pathogen_R1.fastq.gz
gzip -c chromo2.fq plasmid2.fq  > novel-pathogen_R2.fastq.gz
```

The reads were simulated to mimic a HiSeq 2500 Length 150. 

```
The random seed for the run: 200

Parameters used during run
        Read Length:    150
        Genome masking 'N' cutoff frequency:    1 in 150
        Fold Coverage:            60X
        Mean Fragment Length:     200
        Standard Deviation:       10
        Profile Type:             Combined
        ID Tag:                   

Quality Profile(s)
        First Read:   HiSeq 2500 Length 150 R1 (built-in profile) 
        First Read:   HiSeq 2500 Length 150 R2 (built-in profile) 
```

## Simulating the long reads 

Used  `badread` for nanopore

```
badread  simulate --reference vr50.fasta   --quantity 20x | gzip > novel-pathogen-long-reads.fastq.gz
badread  simulate --reference plasmid_pdiarrX.fasta   --quantity 20x | gzip >> novel-pathogen-long-reads.fastq.gz
```

```
Badread v0.2.0
long read simulation

Loading reference from vr50.fasta
  1 contig:
    CP011134.1: 5,000,386 bp, linear, 1.00x depth

Generating fragment lengths from a gamma distribution:
  mean  =  15000 bp      parameters:
  stdev =  13000 bp        k (shape)     = 1.3314e+00
  N50   =  22622 bp        theta (scale) = 1.1267e+04
  │ ▖▌▌▖                                             
  │ ▌▌▌▌▌▌▖                                          
f │▌▌▌▌▌▌▌▌▌▖                                        
r │▌▌▌▌▌▌▌▌▌▌▌▖                                      
a │▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖                                   
g │▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖                               
s │▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖▖                          
  │▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖▖▖▖▖▖▖▖▖           
  ├─────────┬─────────┬─────────┬─────────┬─────────┐
  │       ▖▖▌▌▌▌▌▖▖                                  
  │      ▌▌▌▌▌▌▌▌▌▌▌▌▖                               
b │    ▖▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖                            
a │   ▖▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖                        
s │   ▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖                     
e │  ▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖▖                
s │ ▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖▖▖         
  │▖▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖▖▖
  ├─────────┬─────────┬─────────┬─────────┬─────────┐
  0         13600     27200     40800     54400     68000

Generating read identities from a beta distribution:
  mean  = 87.5%      shape parameters:
  max   = 97.5%        alpha = 3.0513e+01
  stdev =   5%         beta  = 3.4872e+00
  │                                      ▖▌▌▖        
  │                                    ▖▌▌▌▌▌▖       
  │                                   ▖▌▌▌▌▌▌▌       
  │                                  ▌▌▌▌▌▌▌▌▌▌      
  │                                ▖▌▌▌▌▌▌▌▌▌▌▌▖     
  │                              ▖▌▌▌▌▌▌▌▌▌▌▌▌▌▌     
  │                            ▖▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖    
  │                      ▖▖▖▖▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▖   
  ├─────────┬─────────┬─────────┬─────────┬─────────┐
  50        60        70        80        90        100

Read glitches:
  rate (mean distance between glitches) = 10000
  size (mean length of random sequence) =    25
  skip (mean sequence lost per glitch)  =    25

Start adapter:
  seq: AATGTACTTCGTTCAGTTACGTATTGCT
  rate:   90.0%
  amount: 60.0%

End adapter:
  seq: GCAATACGTAACTGAACGAAGT
  rate:   50.0%
  amount: 20.0%

Other problems:
  chimera join rate: 1%
  junk read rate:    1%
  random read rate:  1%
```

