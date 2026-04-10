# Structural variants in human congenital heart disease disrupt distal genomic regulatory contacts of developmental genes

To test the hypothesis that SVs from people with congenital heart disease (CHD) disrupt developmental chromatin interactions, we developed CardioAkita, a machine-learning model that predicts how variants alter 3D chromatin structure.

# Installation 
CardioAkita is built on Akita. To run Akita, the installation of basenji/Akita is needed, which could be found at:[https://github.com/calico/basenji/tree/master]. For model training, NVIDIA GPUs with CUDA are recommended.

# Instructions
Code for CardioAkita evaluation is under Ventricular_Model and Atrial_Model

## Preprocess datasets for CardioAkita training
The inputs of CardioAkita are the one-hot encoded sequences and the output is the contact maps. Genome fasta file, and binned Hi-C data in cooler format are needed.

hg38.blacklist.bed and hg38_gaps_binsize2048_numconseq10.bed could be found under the Data folder.

## Make contact map predictions
To evaluate model performance, you will need the params.json and model weights. 