# 🧬 Single-Cell RNA-seq Analysis of Human Bone Marrow Using Scanpy
This notebook presents a complete single-cell RNA-seq (scRNA-seq) analysis workflow using Scanpy, applied to a human bone marrow dataset originally sourced from the Chan Zuckerberg Initiative (CZI) and adapted for this task.
The primary goal of this analysis is biological interpretation, not method development. Specifically, we aim to identify immune cell types, understand their biological roles, determine whether the tissue source is truly bone marrow, and assess whether the immune landscape reflects a healthy or infected state.
 
## 📦 Dataset Overview
•	Organism: Human 
•	Tissue: Bone marrow
•	Data type: Single-cell RNA-seq (gene expression counts)
•	Gene identifiers: Ensembl gene IDs
•	Cell count: ~14,700 cells
•	Gene count: ~17,000 genes
Because PanglaoDB marker genes are indexed using gene symbols, an explicit Ensembl-to-gene-symbol mapping stepis required before cell type annotation.
 
## 🧹 Quality Control and Preprocessing
Quality control ensures that downstream analyses reflect biological signal rather than technical noise.
In this analysis, cells are retained based on:
•	Sufficient gene detection per cell (to remove dead or low-quality cells)
•	Removal of uninformative genes
•	Normalization to correct for sequencing depth differences
These steps are essential for ensuring that clustering and marker-based annotation reflect real biological structure.
 
## 🔬 Dimensionality Reduction and Clustering
After normalization and feature selection:
•	Principal Component Analysis (PCA) is used to reduce dimensionality
•	UMAP is applied for visualization
•	Leiden clustering identifies transcriptionally distinct cell populations
These clusters form the basis for downstream biological interpretation.
 
## 🧠 Cell Type Annotation Using decoupler and PanglaoDB
Cell type annotation is performed using decoupler (ULM) with PanglaoDB as the reference marker database.
Because PanglaoDB spans multiple tissues, it can return non–bone-marrow-associated labels (e.g., neuronal or epithelial cell types). These annotations are systematically evaluated and curated based on biological plausibility and known immune marker expression.
Marker-based annotation is therefore used as evidence, not as unquestioned ground truth.
 
## 🧪 Q1. What cell types were identified?
Based on clustering and marker enrichment, the following immune and hematopoietic cell types were identified:
•	Neutrophils
•	Monocytes / macrophages
•	Natural killer (NK) cells
•	T cells (naïve, memory, helper, and cytotoxic states)
•	B cells (naïve and memory)
•	Plasma cells
•	Platelet / megakaryocyte lineage
•	Low-confidence / ambiguous cells
Closely related subtypes were consolidated into broader lineages to improve robustness and avoid over-annotation.
 
## 🧫 Q2. Biological role of each cell type
•	Neutrophils are short-lived innate immune cells and first responders to infection, performing phagocytosis and antimicrobial defense.
•	Monocytes / macrophages are mononuclear phagocytes involved in innate immunity, antigen processing, and inflammatory cytokine production.
•	Natural killer (NK) cells mediate early defense against virally infected and stressed cells through cytotoxic activity.
•	T cells are central to adaptive immunity, responsible for antigen recognition, immune regulation, and cytokine signaling.
•	B cells are adaptive immune cells responsible for antibody production; bone marrow is the primary site of B cell development.
•	Plasma cells are terminally differentiated B cells that function as antibody-secreting factories.
•	Platelet / megakaryocyte lineage cells contribute to clotting and immune modulation.
•	Low-confidence cells likely reflect technical noise or cross-tissue marker database artifacts rather than true biological populations.
Assignments were supported by canonical immune marker genes such as CD3D/E (T cells), MS4A1/CD79A (B cells), NKG7/GNLY (NK cells), and LYZ/CTSD (monocytes).
 
## 🧬 Q3. Is the tissue source really bone marrow?
The cellular composition is most consistent with bone marrow, supported by several observations:
•	The dataset contains both innate and adaptive immune lineages, including neutrophils, monocytes, B cells, plasma cells, and platelet-related populations.
•	B cells and plasma cells, which originate and mature in bone marrow, are well represented.
•	The presence of multiple immune differentiation states suggests steady-state hematopoiesis, rather than circulating peripheral blood alone.
•	Peripheral blood typically lacks developing B-lineage cells and megakaryocyte-associated populations.
Limitations
Early hematopoietic stem or progenitor populations are not strongly resolved, possibly due to dataset preprocessing, sequencing depth, or filtering thresholds. Additionally, non–bone-marrow-associated annotations were observed but systematically evaluated and discarded based on lack of canonical immune markers.
Overall, while not definitive, the lineage diversity and composition strongly support a bone marrow origin.
 
## 🦠 Q4. Is the patient healthy or infected?
The relative abundance of immune cell populations suggests a healthy or baseline immune state:
•	Neutrophils are present but not disproportionately expanded, arguing against acute bacterial infection.
•	Monocytes do not show inflammatory skewing.
•	NK cells lack strong activation signatures typical of viral infection.
•	Lymphocyte populations (T and B cells) are balanced, with no evidence of depletion or clonal expansion.
In infectious or inflammatory states, one would expect neutrophilia, monocytosis, activated NK cell signatures, or lymphocyte imbalance. These patterns are not observed here.
 
✅ Overall Conclusion
This dataset represents a biologically coherent snapshot of human bone marrow under non-pathological conditions, capturing steady-state immune composition rather than infection-driven or disease-associated immune perturbation.

