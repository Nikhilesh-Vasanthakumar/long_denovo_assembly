#Nikhilesh Vasanthakumar
#Long-read Genome Assembly Excercise
#22-2-23
#===============================
Software used and their versions and installations.
anaconda-23.1.0
fastqc-0.11.9
hifiasm-0.16.0
wtdbg2-2.1

1.Quality Control
The fastq file given was analysed using fastqc package using the following commands in a bash terminal

>$fastqc SRR13577846.fastq

2.Assembly using Hifiasm
Hifisam was used to assemble the sequences using the following code.

>$hifiasm -o SRR13577846_untrim.asm  -t 8 SRR13577846.fastq

After the output was generated the following code was used to convert the .gfa file to fasta using the following code.

>$awk '/^S/{print ">"$2;print $3}' SRR13577846.p_ctg.gfa > Hifiasm_consensus.fa

Quast was used to find the quality of the assembly.

>quast --eukaryote -r ref.fasta Consensus.fa

This Fasta file was then used as an input for Busco using the following command

>busco -m genome -i Hifiasm_consensus.fa -o Output -l saccharomycetes

4.Assembly using wtdbg2
Similar to Hifiasm we use the fastq file to assemble the sequences.

We use quast and busco to find the quality of the assembly. 
>quast -e -r ref.fasta Consensus.fa

>busco -m genome -i consensus.fa -o Output -l saccharomycetes

The results of the quast and busco are present in the output folder.
