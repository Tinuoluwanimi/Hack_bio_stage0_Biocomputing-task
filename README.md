Bash and Bioinformatics Basics

This project is part of the Stage 0 training tasks. It focuses on learning basic command-line operations, file handling, and installing essential bioinformatics tools. The project is divided into two parts:

Project 1: Bash Basics

In this part, I practiced using the command line to:

Print text to the terminal

Create and navigate directories

Download and manage files (.fna and .gbk)

Detect whether a DNA sequence is wild-type or mutant by searching for specific motifs (tata vs tatatata)

Extract useful biological information from .gbk files (sequence length, source organism, gene names)

Clean the terminal and review command history

Organize files into folders

```#Project one-bash basics
#print your name 
echo 'Tinuoluwanimi'
#create a folder titled your name
mkdir Tinuoluwanimi
#create a new directory titled biocomputing and change to that directory with one line
cd Tinuoluwanimi
mkdir biocomputing && cd biocomputing 
# Download these three files
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.fna
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk

# Move the .fna file to the folder titled your name
mv wildtype.fna ../

# delete the duplicate gbk file
rm -f wildtype.gbk.1

# confirm if the .fna file is mutant or wild type (tatatata vs tata)
cd ../
grep 'tatatata' wildtype.fna

# If mutant, print all matching files into a new line
grep 'tatatata' wildtype.fna > output.fna

# Count number of lines (excluding header) in the .gbk file
cd biocomputing/
grep -v 'LOCUS' wildtype.gbk | wc -l

# Print the sequence length of the .gbk file 
grep '^LOCUS' wildtype.gbk | awk '{print $3}'

# Print the source organism of the .gbk file
grep 'SOURCE' wildtype.gbk | awk '{print $2, $3}'

# List all the gene names of the .gbk file
grep '/gene=' wildtype.gbk | sed 's/.*\/gene="//;s/"//'

# Clear your terminal space and print all commands used today
clear
history

# List the files in the two folders
pwd
ls
cd ../
ls ```

Project 2: Installing Bioinformatics Software

In this part, I practiced setting up a conda environment and installing commonly used bioinformatics tools through the bioconda channel, including:

Figlet

BWA

BLAST

Samtools

Bedtools

SPAdes

Bcftools

Fastp

MultiQC

Each step was carried out directly on the terminal, and the exact commands used are documented in the scripts.
