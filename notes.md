Notes

```bash
for FWD in reads/*_R1.fastq.gz;
do
   skesa --reads $FWD ${FWD/_R1/_R2} --contigs_out assembly-$(basename $FWD | cut -f 1 -d _) --cores  10;
done

for i in ass*;
do
   echo $i
   bwa mem -t 10 vir_genomic.fna $i | samtools view -bS | samtools sort --write-index -o $i.bam -
done

bwa index vir_genomic.fna
for FWD in reads/*_R1.fastq.gz;
do
   bwa mem -t 10 vir_genomic.fna $FWD ${FWD/_R1/_R2} | samtools view -bS | samtools sort --write-index -o map-$(basename $FWD | 
cut -f 1 -d _).bam -;
done


for BAM in *bam;
do
   freebayes -f vir_genomic.fna -C 3 -F 0.6 $BAM > var-$(basename $BAM | cut -f 1 -d _).vcf;
done
```
