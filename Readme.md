# Integrating Global Tumor Proteome Profile with Machine Learning to Predict Protein Subcellular Localization

## Description

ML framework of predicting protein subcellular localization using global protein abundances from clinical tumors.

## Publication

Citation TBD

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

### [raw_datasets](raw_datasets)
Folder containing raw proteomics datasets (protein tables "*XX_ratio_protein_None.tsv*" output from FragPipe), cleaned Proteomics datasets "*XX prot model use.csv*" and cleaned Transcriptomics datasets "*XX mrna model use.csv*".

### [processed_datasets](processed_datasets)
Folder containing processed proteomics and transcriptomics datasets output from [Dataset generation.ipynb](Dataset%20generation.ipynb). These are the datasets used in model development and testing.

### [Dataset generation.ipynb](Dataset%20generation.ipynb)
Notebook for generating processed proteomics and transcriptomics datasets. Steps include normalization, quantile transformation, filtering, and joint KDE inference. Details are provided in the manuscript's methods section.

### [labels](labels)
Folder containing marker protein localization labels (markers.txt) and marker protein cluster information (markers_mclusters.txt) from [Orre et al.](https://www.cell.com/molecular-cell/fulltext/S1097-2765(18)31005-0?_returnURL=https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS1097276518310050%3Fshowall%3Dtrue). Uniprot protein localization label (uniprot_go_markers.txt) from Supplementary Table 2 in [Lund-Johansen et al.](https://www.nature.com/articles/nmeth.3967). Grouped result is grouping 11 compartments into four major compartment neighborhoods (uniprot_go_markers_grouped.txt).

### [Label generation.ipynb](Label%20generation.ipynb)

### [NN_tables](NN_tables)
Folder containing CSV files recording metrics throughout the training process. Metrics include loss, accuracy, precision and recall of each class, marco F1 score throughout epochs. Per compartment precision, recall and F1 score from 5 fold cross-validation. Protein, mRNA, and Protein + mRNA indicate the model input.

### [saved_models](saved_models)
Folder containing trained models as parameter dictionaries (.pth) used for inference on independent testing sets.

### [Fig1_FigS1_UMAP](Fig1_FigS1_UMAP)
Folder containing figures used for Figure 1 and S1 in the manuscript. Figures are generated from [Dimension reduction figures.ipynb](Dimension%20reduction%20figures.ipynb)

### [Fig3_FigS2_NN_figures](Fig3_FigS2_NN_figures)
Folder containing figures used for Figure 3 and S2 in the manuscript. Figures are generated from [Fig3_Training_CNN_Prot_Unranked_Input.ipynb](Fig3_customNN%20prot%20unranked%20input.ipynb),
[Fig3_Training_CNN_Prot_Ranked_Input.ipynb](Fig3_customNN%20prot%20ranked%20input.ipynb),
[FigS2_Training_CNN_mRNA_Input.ipynb](FigS2_customNN%20mRNA%20input.ipynb) and
[FigS2_Training_CNN_Prot + mRNA_Input.ipynb](FigS2_customNN%20prot%20+%20mRNA%20input.ipynb)

### [Fig4_Enrichr_Ranked_Prot_Marker_Localization](Fig4_Enrichr_Ranked_Prot_Marker_Localization)
Folder containing figures used for Figure 4 in the manuscript. Figures are generated from [Fig4_Enrichr_Ranked_Prot_Marker_Localization.ipynb](Fig4_Enrichr_Ranked_Prot_Marker_Localization.ipynb) and [comparision of markers.ipynb](comparision%20of%20markers.ipynb)

### [Fig5_Enrichr_Ranked_Prot_Modified_Marker_Localization](Fig5_Enrichr_Ranked_Prot_Modified_Marker_Localization)
Folder containing figures used for Figure 5 in the manuscript. Figures are generated from [Fig5_Enrichr_Ranked_Prot_Modified_Marker_Localization.ipynb](Fig5_Enrichr_Ranked_Prot_Modified_Marker_Localization.ipynb) and [Fig5_Training_CNN_Prot_Ranked_Input_Modified_Label.ipynb](Fig5_customNN%20prot%20ranked%20input%20modified%20label.ipynb)




