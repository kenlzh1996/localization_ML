# Convolutional neural networks predict tumor protein subcellular localization based on bulk proteome profiles

## Description

ML framework of predicting protein subcellular localization using global protein abundances from clinical tumors.

## Publication

Citation TBD

## Folder and notebook description

### [raw_datasets](raw_datasets)
Folder containing the input tables for five cohorts from four studies, named by first author: Krug (training breast tumor cohort), Mertins (breast tumor), Satpathy (lung tumor and lung NAT, normal adjacent tissue) and Liu (brain tumor).
- "*XX_ratio_protein_None.tsv*": raw protein tables output from FragPipe.
- "*XX prot model use.csv*": cleaned proteomics datasets (genes x samples). Values are protein ratios to the pooled reference, not log-transformed.
- "*XX mrna model use.csv*": cleaned transcriptomics datasets (genes x samples). Values are TPM, not log-transformed.

### [Dataset_generation.ipynb](Dataset_generation.ipynb)
Notebook for generating the processed proteomics and transcriptomics datasets from the cleaned datasets in [raw_datasets](raw_datasets). Proteins and transcripts go through the same pipeline, per cohort:
1. Proteome only: exclude samples that are not in the original study, then average technical replicates.
2. Keep samples present in both proteome and transcriptome.
3. Remove transcripts with a TPM of 0 in any sample, average rows sharing a gene symbol, and remove genes with any missing value.
4. Keep genes that pass the filters in both proteome and transcriptome.
5. Normalize: divide each gene by its mean across samples, divide each sample by its median across genes, take log2, then divide each sample by its robust spread, (Q75 - Q25) / 1.349, across its genes.

Further details are provided in the notebook and in the manuscript's methods section.

### [processed_datasets_prot_mrna](processed_datasets_prot_mrna)
Folder containing the output from [Dataset_generation.ipynb](Dataset_generation.ipynb). These are the datasets used in model training and testing.
- "*XX_PD_processed.csv*" (proteome) and "*XX_MD_processed.csv*" (transcriptome): processed datasets (genes x samples), with genes and samples in alphabetical order. Within a cohort, the two files contain the same genes and the same samples. Each cohort keeps its own number of samples: 121 (training, Krug), 77 (breast_tumor, Mertins), 108 (lung_tumor, Satpathy), 94 (lung_nat, Satpathy) and 99 (brain_tumor, Liu).
- "*preprocessing_flow.csv*": number of genes and samples after each step, per cohort.
- "*gene_sample_overlap.csv*": number of genes and samples in the final proteome and transcriptome datasets, per cohort.
- "*preprocessing_settings.json*": settings, package versions and cohort configuration used for the run.

### [labels](labels)
Folder containing marker protein localization labels (markers.txt) and marker protein cluster information (markers_mclusters.txt) from [Orre et al.](https://www.cell.com/molecular-cell/fulltext/S1097-2765(18)31005-0?_returnURL=https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS1097276518310050%3Fshowall%3Dtrue). UniProt protein localization label curated in MetaMass(uniprot_go_markers.txt) from Supplementary Table 2 in [Lund-Johansen et al.](https://www.nature.com/articles/nmeth.3967). Grouped result is grouping 11 compartments into four major compartment neighborhoods (uniprot_go_markers_grouped.txt). Modified labels is generated from cross-referencing marker protein localization labels and MetaMass annotations. For proteins where the localization labels conflicted with MetaMass annotations, they were reassigned based on the MetaMass annotations (markers_modified_1.txt).

### [Label generation.ipynb](Label%20generation.ipynb)
Notebook for generating modified labels [markers_modified_1.txt](labels/markers_modified_1.txt) used in Fig 4

### [NN_tables](NN_tables)
Folder containing CSV files recording metrics throughout the training process. Metrics include loss, accuracy, precision and recall of each class, marco F1 score throughout epochs. Per compartment precision, recall and F1 score from 5 fold cross-validation. Protein, mRNA, and Protein + mRNA indicate the model input.

### [saved_models](saved_models)
Folder containing trained models as parameter dictionaries (.pth) used for inference on independent testing sets.

### [Fig1_FigS2_UMAP](Fig1_FigS2_UMAP)
Folder containing figures used for Figure 1 and S2 in the manuscript. Figures are generated from [Dimension reduction figures.ipynb](Dimension%20reduction%20figures.ipynb)

### [Fig3_FigS3_NN_figures](Fig3_FigS3_NN_figures)
Folder containing figures used for Figure 3 and S3 in the manuscript. Figures are generated from [Fig3_Training_CNN_Prot_Unranked_Input.ipynb](Fig3_customNN%20prot%20unranked%20input.ipynb),
[Fig3_Training_CNN_Prot_Ranked_Input.ipynb](Fig3_customNN%20prot%20ranked%20input.ipynb),
[FigS3_Training_CNN_mRNA_Input.ipynb](FigS3_customNN%20mRNA%20input.ipynb) and
[FigS3_Training_CNN_Prot + mRNA_Input.ipynb](FigS3_customNN%20prot%20+%20mRNA%20input.ipynb)

### [Fig4_Enrichr_Ranked_Prot_Marker_Localization](Fig4_Enrichr_Ranked_Prot_Marker_Localization)
Folder containing figures used for Figure 4 in the manuscript. Figures are generated from [Fig4_Enrichr_Ranked_Prot_Marker_Localization.ipynb](Fig4_Enrichr_Ranked_Prot_Marker_Localization.ipynb) and [comparision of markers.ipynb](comparision%20of%20markers.ipynb)

### [FigS4_Enrichr_Ranked_Prot_Modified_Marker_Localization](FigS4_Enrichr_Ranked_Prot_Modified_Marker_Localization)
Folder containing figures used for Figure S4 in the manuscript. Figures are generated from [FigS4_Enrichr_Ranked_Prot_Modified_Marker_Localization.ipynb](FigS4_Enrichr_Ranked_Prot_Modified_Marker_Localization.ipynb) and [FigS4_Training_CNN_Prot_Ranked_Input_Modified_Label.ipynb](Fig5_customNN%20prot%20ranked%20input%20modified%20label.ipynb)
