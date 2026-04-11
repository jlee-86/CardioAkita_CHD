# Structural variants in human congenital heart disease disrupt distal genomic regulatory contacts of developmental genes

To test the hypothesis that SVs from people with congenital heart disease (CHD) disrupt developmental chromatin interactions, we developed CardioAkita, a machine-learning model that predicts how variants alter 3D chromatin structure.

# Installation 
CardioAkita is built on Akita. To run Akita, the installation of basenji/Akita is needed, which could be found at:[https://github.com/calico/basenji/tree/master]. For model training, NVIDIA A30 GPU or equivalent with CUDA are recommended.

## Preprocess datasets for CardioAkita training
The inputs of CardioAkita are the one-hot encoded sequences and the output is the contact maps. Genome fasta file, and binned Hi-C data in cooler format are needed. hg38.blacklist.bed and hg38_gaps_binsize2048_numconseq10.bed are under data/human_genome/ folder. Instructions for training CardioAkita under tutorial_CardioAkita.ipynb 

## CardioAkita models
Model weights and parameters are under ventricular and atrial folders. Explore CardioAkita predictions under explore_CardioAkita.ipynb.  

## Make contact map predictions
To evaluate model performance, you will need the params.json and model weights. 

# Scoring structural variants with SuPreMo
We installed Supremo-Akita[https://github.com/ketringjoni/SuPreMo?tab=readme-ov-file#install-supremo-or-supremo-akita] and replaced the Original Akita model with the weights for CardioAkita. Variants scored with SuPreMo are under structural_variants folder.

An example of scoring variants using SuPreMo: 

python SuPreMo_ventricular_d23.py /CardioAkita/structural_variants/Control_structural_variants.txt --shift_by -1 0 1 --revcomp add_revcomp --file v_d23 --dir /CardioAkita/structural_variants/vd23/control --get_Akita_scores --get_maps --get_tracks --fa hg38.fa --genome hg38

## Expected Output
Output genome folding disruption scores are in the Supplementary Data section of the paper. 

# Contact 
For questions, please contact: jodi.lee@gladstone.ucsf.edu