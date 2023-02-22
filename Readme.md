#Nikhilesh Vasanthakumar
#Long-read Genome Assembly Excercise
#22-2-23
#===============================
Software used and their versions and installations.
anaconda
fastqc
hifiasm
flye
1.Quality Control
The fastq file given was analysed using fastqc package using the following commands in a bash terminal

$fastqc SRR13577846.fastq

2.Assembly using Hifiasm
Hifisam was used to assemble the sequences using the following code.

$hifiasm -o SRR13577846_untrim.asm  -t 8 SRR13577846.fastq

After the output was generated the following code was used to convert the .gfa file to fasta using the following code.

$awk '/^S/{print ">"$2;print $3}' SRR13577846.p_ctg.gfa > Hifiasm_consensus.fa

This Fasta file was then used as an input for Busco using the following command

busco -m genome -i Hifiasm_consensus.fa -o Output -l saccharomycetes

4.Assembly using HybridSPAdes