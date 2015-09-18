# procannot

Procannot annotates SNPs in procaryotic genomes

## Getting started

```git clone https://github.com/aakechin/procannot.git```

## Introduction

Procannot is a software package for annotating SNPs from bacteria genomes. It consists of several algorithms of annotation: by genes' information, its presense in our SNP database, influence on organism's pathways and evolution selection type of all genes. All of algorithms uses our databases that can be updated or created by user. Generally Procannot consists of the following databases:
* GenBank_files - contains all GenBank files of all organisms;
* GenomeDB - contains files with information about all genes;
* GenomeSeq - contains files with nucleotide sequences of all genomes;
* Organisms - contains information about all organisms that were written to the databases;
* PathwayDB - contains information about all pathways of all strains;
* SnpDB - contains all SNPs that were found between all strains of an organism;
* OrthoDB and alignedOrthoDB - contain alignments of genes of all strains of an organism.

## Availability

Procannot is released under GPLv3. The latest source code is freely available at github. After you acquire the source code, install python version 3 or higher and then use it. You can install Python3 with the following command:

sudo apt-get install python3

## Manual

All commands and their options you can find by use of -h option or in the Manual.pdf file.

## Examples of use

All commnads of procannot must be run from the installation directory.

### Database creation (procannot.py)

To create all databases that were listed above for Bacillus subtilis (reference NC_000964), run the command:

```python3 procannot.py make_all -o 'Bacillus subtilis' -r NC_000964```

To create only database of genes' information run the command:

```python3 procannot.py make_genomedb -o 'Bacillus subtilis'```

If you already have database of genes for this organism and want to create database of orthologues for this reference of an organism, run the command:

```python3 procannot.py make_orthodb -o 'Bacillus subtilis' -r NC_000964```

If you already have database of orthologues and want to create database of SNPs for this reference of an organism, run the command:

```python3 procannot.py make_snpdb -o 'Bacillus subtilis' -r NC_000964'```

### Data annotation (data.py)

If you have all necessary databases (listed above), you can annotate your SNP list with whole workflow that is used in procannot. One of the most great convinience of procannot is independence from standards of input file. User can input VCF-file, TAB-delimited file from Freebayes or GATK-converted or simple TXT-file that was created manually. Thus for full annotation of your data run the command (use of short parameters' name is available):

```python3 data.py full --input input.tab --row-start 2 --column-names 1 --snp-coordinates 1 --reference-allele 2 --alternative-allele 3 --organism 'Listeria monocytogenes' --reference NC_003210```

In this case output will be written to the same directory as input file. As output there will be the following files:
* input.annotated.tab - file where each SNP has characteristic 'Introgene/Intergene', gene ID, gene strand, gene name, gene description, nucleotide change, aminoacid change, aminoacid class change and all other characteristics that were in the input file;
* input.annotated.checked.tab - file that contains all of previous data and additionally for each SNP it has number of references that 
