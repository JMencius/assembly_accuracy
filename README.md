# Tools for assessing the accuracy of a genome assembly

This repository contains a small tool to assess the accuracy of an assembly using minimap2.


## Installation
It requires the `pyvcf` and `pysam` python packages, and `minimap2` and `samtools` and `conda` to be on your PATH.
It can be tricky for installation, a direct `conda install XXX` can lead to numerous error and version conflict.

You can directly copy my work conda environment config by :
`conda create -f fastmer_mencius.yaml;`

Or you can maunually install the environment using the following command :
```
conda create -n fastmer python=3.6.2;
conda activate fastmer;
conda install -c bioconda pyvcf;
pip install pysam;
conda install -c bioconda minimap2;
conda install -c bioconda samtools;
conda install numpy
```

My final conda config is :
```
# Name                    Version                   Build  Channel
_libgcc_mutex             0.1                        main  
_openmp_mutex             5.1                       1_gnu  
blas                      1.0                         mkl  
ca-certificates           2023.12.12           h06a4308_0  
certifi                   2021.5.30        py36h06a4308_0  
intel-openmp              2022.1.0          h9e868ea_3769  
k8                        0.2.5                h9a82719_1    bioconda
libedit                   3.1                  heed3624_0  
libffi                    3.2.1             hf484d3e_1007  
libgcc-ng                 11.2.0               h1234567_1  
libgomp                   11.2.0               h1234567_1  
libstdcxx-ng              11.2.0               h1234567_1  
minimap2                  2.17                 h5bf99c6_4    bioconda
mkl                       2020.2                      256  
mkl-service               2.3.0            py36he8ac12f_0  
mkl_fft                   1.3.0            py36h54f3939_0  
mkl_random                1.1.1            py36h0573a6f_0  
ncurses                   6.0                  h9df7e31_2  
numpy                     1.19.2           py36h54aff64_0  
numpy-base                1.19.2           py36hfa32c7d_0  
openssl                   1.0.2u               h7b6447c_0  
pip                       21.2.2           py36h06a4308_0  
pysam                     0.22.0                   pypi_0    pypi
python                    3.6.2               hca45abc_19  
pyvcf                     0.6.8                    py36_0    bioconda
readline                  7.0                  ha6073c6_4  
samtools                  1.3.1                         0    bioconda/label/cf201901
setuptools                58.0.4           py36h06a4308_0  
six                       1.16.0             pyhd3eb1b0_1  
sqlite                    3.23.1               he433501_0  
tk                        8.6.12               h1ccaba5_0  
wheel                     0.37.1             pyhd3eb1b0_0  
xz                        5.4.6                h5eee18b_0  
zlib                      1.2.13               h5eee18b_0 
```



## Usage

```
fastmer.py --reference reference.fasta --assembly assembly.fasta --min-mapping-quality 10
```

## Example output:

```
assembly_name    percent_identity  qscore  num_matches  num_mismatches  num_insertions  num_deletions  4mer_acc  5mer_acc  6mer_acc  7mer_acc  8mer_acc  9mer_acc
nanopolish_r94   99.956154         33.58   4691618      163             730             1165           0.995     0.983     0.923     0.825     0.730     0.545
```
