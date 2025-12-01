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
**GTEx v8 Bulk Tissue Expression**

&nbsp; Source: \[GTEx Portal](https://gtexportal.org/home/datasets) → \*Open Access Data → Gene TPMs\*



**Sample Metadata**

&nbsp; Used for extracting tissue labels (column: `SMTS`) and filtering top tissues.



---

## Methods Summary

### 1. Data Preprocessing
- Extracted the **top 10 tissues** by sample count.
- Selected **top 5,000 most variable genes** (based on variance).
- Matched sample metadata to expression matrix.
- Standardized expression data (`StandardScaler`).

### 2. Clustering
- Performed clustering with:

&nbsp; - **KMeans**

&nbsp; - **Agglomerative Clustering**

- Explored **k=5 to 15** for each method.

- Evaluated clustering using:

&nbsp; - Internal: Silhouette Score

&nbsp; - External: Adjusted Rand Index (vs true tissue)



### 3. Cluster Evaluation \& Interpretation

- Identified top genes using:

&nbsp; - Variance across clusters

&nbsp; - Cluster-specific expression profiles

- Visualized:

&nbsp; - Heatmaps of gene expression by cluster

&nbsp; - (Optional: UMAP and PCA cluster visualization)



---

## Results

- KMeans showed the highest silhouette and ARI scores at `k = 10`, which matched the number of tissue types used.
- Specific genes enriched in each cluster supported known tissue markers (e.g. brain-specific expression).
- Cluster-to-tissue alignment validated the biological relevance of unsupervised clusters.


---


## File Structure

