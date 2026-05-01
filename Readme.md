# Convolutional neural networks predict tumor protein subcellular localization based on bulk proteome profiles

## Description

ML framework of predicting protein subcellular localization using global protein abundances from clinical tumors.

## Publication

Citation TBD

## Folder and notebook description

### [raw_datasets](raw_datasets)
Folder containing raw proteomics datasets (protein tables "*XX_ratio_protein_None.tsv*" output from FragPipe), cleaned Proteomics datasets "*XX prot model use.csv*" and cleaned Transcriptomics datasets "*XX mrna model use.csv*".

### [Dataset generation.ipynb](Dataset%20generation.ipynb)
Notebook for generating processed proteomics and transcriptomics datasets. Steps include normalization, quantile transformation, and joint KDE inference. Details are provided in the manuscript's methods section.

### [processed_datasets_unfiltered](processed_datasets_unfiltered)
Folder containing processed proteomics and transcriptomics datasets output from [Dataset generation.ipynb](Dataset%20generation.ipynb). These are the datasets used in model development and testing.

### [labels](labels)
Folder containing marker protein localization labels (markers.txt) and marker protein cluster information (markers_mclusters.txt) from [Orre et al.](https://www.cell.com/molecular-cell/fulltext/S1097-2765(18)31005-0?_returnURL=https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS1097276518310050%3Fshowall%3Dtrue). UniProt protein localization label curated in MetaMass(uniprot_go_markers.txt) from Supplementary Table 2 in [Lund-Johansen et al.](https://www.nature.com/articles/nmeth.3967). Grouped result is grouping 11 compartments into four major compartment neighborhoods (uniprot_go_markers_grouped.txt). Modified labels is generated from cross-referencing marker protein localization labels and MetaMass annotations. For proteins where the localization labels conflicted with MetaMass annotations, they were reassigned based on the MetaMass annotations (markers_modified_1.txt).

### [Label generation.ipynb](Label%20generation.ipynb)
Notebook for generating modified labels [markers_modified_1.txt](labels/markers_modified_1.txt) used in Fig 5

### [NN_tables](NN_tables)
Folder containing CSV files recording metrics throughout the training process. Metrics include loss, accuracy, precision and recall of each class, marco F1 score throughout epochs. Per compartment precision, recall and F1 score from 5 fold cross-validation. Protein, mRNA, and Protein + mRNA indicate the model input.

### [saved_models](saved_models)
Folder containing trained models as parameter dictionaries (.pth) used for inference on independent testing sets.

### [Fig1_FigS2_UMAP](Fig1_FigS1_UMAP)
Folder containing figures used for Figure 1 and S2 in the manuscript. Figures are generated from [Dimension reduction figures.ipynb](Dimension%20reduction%20figures.ipynb)

### [Fig3_FigS3_NN_figures](Fig3_FigS2_NN_figures)
Folder containing figures used for Figure 3 and S3 in the manuscript. Figures are generated from [Fig3_Training_CNN_Prot_Unranked_Input.ipynb](Fig3_customNN%20prot%20unranked%20input.ipynb),
[Fig3_Training_CNN_Prot_Ranked_Input.ipynb](Fig3_customNN%20prot%20ranked%20input.ipynb),
[FigS3_Training_CNN_mRNA_Input.ipynb](FigS3_customNN%20mRNA%20input.ipynb) and
[FigS3_Training_CNN_Prot + mRNA_Input.ipynb](FigS3_customNN%20prot%20+%20mRNA%20input.ipynb)

### [Fig4_Enrichr_Ranked_Prot_Marker_Localization](Fig4_Enrichr_Ranked_Prot_Marker_Localization)
Folder containing figures used for Figure 4 in the manuscript. Figures are generated from [Fig4_Enrichr_Ranked_Prot_Marker_Localization.ipynb](Fig4_Enrichr_Ranked_Prot_Marker_Localization.ipynb) and [comparision of markers.ipynb](comparision%20of%20markers.ipynb)

### [FigS4_Enrichr_Ranked_Prot_Modified_Marker_Localization](FigS4_Enrichr_Ranked_Prot_Modified_Marker_Localization)
Folder containing figures used for Figure S4 in the manuscript. Figures are generated from [FigS4_Enrichr_Ranked_Prot_Modified_Marker_Localization.ipynb](FigS4_Enrichr_Ranked_Prot_Modified_Marker_Localization.ipynb) and [FigS4_Training_CNN_Prot_Ranked_Input_Modified_Label.ipynb](Fig5_customNN%20prot%20ranked%20input%20modified%20label.ipynb)
