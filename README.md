# HackBio_stage2
Author: Hasiba Asma

## Single-Cell RNA-seq Analysis of Human Bone Marrow using Scanpy
This repository contains a reproducible single-cell RNA-seq analysis pipeline implemented in Python using Scanpy, applied to a human bone marrow dataset originally sourced from the Chan Zuckerberg Initiative (CZI) and adapted for this task.
The analysis processes raw gene expression counts through clustering, cell type annotation, and biological interpretation, with a focus on understanding immune cell composition and tissue context.

### Project Objectives
The goals of this project were to:
- Reproduce a standard single-cell RNA-seq analysis workflow using Scanpy
- Perform unsupervised clustering of cells
- Annotate cell types using decoupler and PanglaoDB marker genes
- Interpret the biological identity of the tissue
- Assess whether the immune landscape reflects a healthy or infected state
- Communicate findings clearly for both scientific and professional audiences

### Dataset
Source: Chan Zuckerberg Initiative (CZI)
Organism: Human
Tissue: Bone marrow
Data type: Single-cell RNA-seq (gene expression counts)
Note: Gene identifiers were provided as Ensembl IDs; marker databases required additional preprocessing to ensure compatibility with decoupler.

### Analysis Workflow
The analysis follows a standard Scanpy pipeline:
- Data loading and preprocessing
  Filtering low-quality cells
  Normalization and log transformation
- Feature selection
  Identification of highly variable genes
- Dimensionality reduction
  PCA and UMAP
- Clustering
  Leiden community detection
- Cell type annotation
  Marker-based enrichment using decoupler (ULM)
- PanglaoDB as the reference marker database
  Manual curation to retain biologically plausible bone marrow lineages
- Biological interpretation
 Identification of major immune populations
  Tissue origin validation
  Assessment of immune activation state

### Identified Cell Types
After clustering and annotation, the following major cell populations were identified:
  T cells
  B cells
  Monocytes / macrophages
  Other / low-confidence cells (minor clusters with weak or conflicting marker enrichment)
Subtypes (e.g., naïve vs memory) were detected but consolidated into broader lineages for robustness and interpretability.

### Key Biological Findings
- The cellular composition is consistent with bone marrow, supported by immune lineage diversity and strong B cell representation.
- No evidence of acute infection or immune dysregulation was observed.
- The immune landscape reflects a healthy or baseline immune state.
- Minor non–bone-marrow annotations were attributed to cross-tissue marker database noise rather than true biology.

### Repository Structure
.
├── Task_2_Single_Cell_Pipeline_with_ScanPy.ipynb
├── README.md
└── figures/

### How to Run the Notebook
Requirements
  Python ≥ 3.8
  scanpy
  anndata
  decoupler
  pandas
  numpy
  matplotlib
  seaborn
### Steps
Clone the repository:
```
git clone <your-repo-url>
```
Install dependencies:
```
pip install scanpy decoupler pandas numpy matplotlib seaborn
```
Open and run the notebook:
```
jupyter notebook Task_2_Single_Cell_Pipeline_with_ScanPy.ipynb
```
