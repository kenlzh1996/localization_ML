# Project Name
Integrating Global Tumor Proteome Profile with Machine Learning to Predict Protein Subcellular Localization

## Description

ML framework of predicting protein subcellular localization using global protein abundances from clinical tumors.

## Publication

## Installation

```bash
# Clone the repository
git clone https://github.com/kenlzh1996/localization_ML.git

# Navigate to the project directory
cd localization_ML

# Create an environment based on the environment file
conda env create -f environment.yml
conda activate localization_ML
```

## Usage


## Folder and notebook description
/raw_datasets
Raw proteomics datasets (protein tables [*_ratio_protein_None.tsv] output from FragPipe)
Cleaned Proteomics datasets [* prot model use.csv]
Cleaned Transcriptomics datasets [* mrna model use.csv]

/processed_datasets
Processed proteomics and transcriptomics datasets output from [Dataset generation.ipynb]. These are the datasets involved in model development and testing.



