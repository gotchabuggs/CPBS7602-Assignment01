# CPBS 7602 Assignment 01 — Gene Expression Clustering with GTEx

## Course: Introduction to Big Data in the Biomedical Sciences (CPBS 7602)
**Instructor:** Milton Pividori  
**Institution:** University of Colorado Anschutz Medical Campus  
**Student:** Saloni Dixon

---

## Overview

This project performs unsupervised clustering on a subset of the GTEx gene expression dataset to explore whether transcriptomic profiles can distinguish tissue of origin. We assess clustering quality using both internal (e.g. silhouette score) and external (e.g. adjusted Rand index vs true tissue labels) metrics, and interpret biological relevance of clusters using gene expression patterns.

---

## Dataset
- **GTEx v8 Bulk Tissue Expression** (TPM normalized)  
  Downloaded from: [GTEx Portal – Bulk Tissue Expression](https://gtexportal.org/home/datasets)

**Metadata**
- Used the `SMTS` column to identify the **tissue of origin**.  
- Sample metadata was used to extract the top tissues by sample size.

---

## Methods Summary

### 1. Data Preprocessing
- Loaded metadata and expression matrices.
- Extracted the **top 10 tissues** by sample count.
- Selected **top 5,000 most variable genes** (based on variance).
- Matched sample metadata to expression matrix.
- Standardized expression data (`StandardScaler`).

### 2. Clustering
Used two clustering algorithms:
- **KMeans**
- **Agglomerative Clustering**

Parameters:
- Explored **k=5 to 15** clusters.
- Clustered using the standardized gene expression matrix.

### 3. Cluster Evaluation & Interpretation

- **Internal Metric**: Silhouette Score
- **External Metric**: Adjusted Rand Index (ARI) using known tissue labels

Top genes were identified by:
- **ANOVA F-test** to determine the most discriminative genes across clusters
- **Per-cluster mean expression** to find cluster-specific top genes

Visualizations:
- Line plots of ARI and silhouette score by `k`
- PCA-based cluster visualizations
- Heatmaps of top genes by cluster

---

## Results & Findings

- **Optimal k = 10** aligned with the 10 chosen tissues and showed the highest ARI and silhouette scores.
- **Cluster-to-tissue correspondence** revealed biologically meaningful patterns.
- Top genes per cluster reflected tissue-specific functions (e.g., brain, blood, adipose).
- **Heatmaps** illustrated distinct gene expression signatures for each cluster.

UMAP was attempted for dimensionality reduction but encountered compatibility issues on the local system.

---

## Reproducibility
To ensure reproducibility:

### Random Seed Usage
- **All clustering include `random_state=42`.**
- Where applicable, `numpy.random.seed(42)` is set explicitly.

### Environment Setup 
You can recreate the environment using `conda`:

`conda create -n cpbs7602 python=3.10`
`conda activate cpbs7602`
`pip install -r requirements.txt`

Alternatively, install the key dependencies manually:
`pip install pandas numpy matplotlib seaborn scikit-learn`

### How to Run
From inside the cloned repo or folder:
`jupyter notebook assignment_1.ipynb`
Rull all cells sequentially for full analysis.
