#illumina platinum pedigree realignment
This repository contains files and commands used to realign platinum genome to the GRCh38_BSM.fa

##download fastq file of platinum genome:
downloading address of platinum genome were indexed in illumina_platinum_ped.sequence.index

##Command lines
1. Alignment at run level
```
bwa mem  -t 1 -B 4 -O 6 -E 1 -M -R $rg_string $reference_fasta_file $fastq_file(1) $fastq_file(2) | samtools view -1 - > $bam_file
```

##A quick example:
1. Download and unzip fastq file for NA12878:
```
wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR194/ERR194147/ERR194147_1.fastq.gz
gunzip ERR194147_1.fastq.gz
```
2. Align NA12878 at run level:
```
bwa mem  -t 1 -B 4 -O 6 -E 1 -M -R "@RG\tID:ERR194147\tSM:NA12878\tCN:ILLUMINA\tPL:ILLUMINA\tDS:ERP001960" /nfs/turbo/dcmb-brainsom/technical/reference/GRCh38_bsm_reference_genome/GRCh38_BSM.fa /nfs/remills-scratch2/Xuefang/bsmn/platinum.genome.realignment/fastq/NA12878_1.fastq /nfs/remills-scratch2/Xuefang/bsmn/platinum.genome.realignment/fastq/NA12878_2.fastq |samtools view -1 - > /nfs/remills-scratch2/Xuefang/bsmn/platinum.genome.realignment/alignment/NA12878.bam
```
