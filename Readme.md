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
Folder containing raw proteomics datasets (protein tables [*_ratio_protein_None.tsv] output from FragPipe), cleaned Proteomics datasets [* prot model use.csv] and cleaned Transcriptomics datasets [* mrna model use.csv]

/processed_datasets
Folder containing processed proteomics and transcriptomics datasets output from [Dataset generation.ipynb]. These are the datasets used in model development and testing.

Dataset generation.ipynb
Notebook for generating processed proteomics and transcriptomics datasets. Steps include normalization, quantile transformation, filtering, and joint KDE inference. Details are provided in the manuscript's methods section.

/saved_models
Folder containing trained models used for inference on independent test sets. [*_model.pth]

