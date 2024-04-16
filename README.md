# Tools for assessing the accuracy of a genome assembly

This repository contains a small tool to assess the accuracy of an assembly using minimap2.


## Installation
It requires the `pyvcf` and `pysam` python packages, and `minimap2` and `samtools` and `conda` to be on your PATH.
It can be tricky for installation, a direct `conda install {PACKAGE}` can lead to numerous error and version conflict.

You can directly copy tested conda environment config `faster_mencius.yaml` by :
`conda create -f fastmer_mencius.yaml;`

Or you can maunually install the environment using the following command :
```
conda create -n fastmer python=3.6.2;
conda activate fastmer;
conda install -c bioconda pyvcf;
pip install pysam;
conda install -c bioconda minimap2;
conda install -c bioconda samtools;
conda install numpy;
```
If you encounter errors like:
`returned non-zero exit status 127` or 
`samtools: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory`
I just use apt-get to fix it on Ubuntu
`sudo apt-get install libncurses5`

## Usage

```
fastmer.py --reference reference.fasta --assembly assembly.fasta --min-mapping-quality 10
```

## Example output:

```
assembly_name    percent_identity  qscore  num_matches  num_mismatches  num_insertions  num_deletions  4mer_acc  5mer_acc  6mer_acc  7mer_acc  8mer_acc  9mer_acc
nanopolish_r94   99.956154         33.58   4691618      163             730             1165           0.995     0.983     0.923     0.825     0.730     0.545
```

## Run time
For an AMD Ryzen 9 5900X, 128G RAM, and solid state drive, the approximate run time is 4-5h.
