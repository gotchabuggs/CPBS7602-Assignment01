# CPBS 7602 Assignment 01 – Cluster Analysis on Gene Expression Data

**Course:** CPBS 7602 – Introduction to Big Data in the Biomedical Sciences  
**Instructor:** Milton Pividori  
**Student:** Saloni Dixon  
**Date:** December 2, 2025

---

## Objective

This assignment explores the use of unsupervised clustering techniques on transcriptomic data from the GTEx v8 dataset to determine whether gene expression profiles can recover the tissue of origin. It assesses both clustering performance and biological interpretability through internal/external metrics and gene-level analysis.

---

## Data Preprocessing

- **Source:** GTEx v8 "Bulk Tissue Expression" & Sample Metadata.
- **Filtering Steps:**
  - Selected top 10 tissues based on number of available samples (`SMTS` column).
  - Selected top 5,000 most variable genes by computing variance across samples.
- **Standardization:** Expression data were scaled using `StandardScaler()` to zero mean and unit variance.
- **Final shape of input data:**  
  - **Samples:** ~19,616  
  - **Genes:** 5,000  
  - **Labels:** 10 tissue types

---

## Clustering Methods

We applied two clustering algorithms using `scikit-learn`:

1. **KMeans Clustering**
   - Parameter sweep: `k = 5 to 15`
   - Random state set for reproducibility
2. **Agglomerative Clustering**
   - Same parameter sweep for consistency

For both methods, we computed:
- **Internal metric:** Silhouette Score
- **External metric:** Adjusted Rand Index (ARI), comparing clusters to known tissue labels

---

## Clustering Evaluation & Results

### Internal Evaluation (Silhouette Score)

- **KMeans** peaked at **k = 10**, aligning with the number of tissue types.
- Scores declined for higher k, consistent with potential over-fragmentation.
- Suggests that expression data has distinguishable structure aligning with tissue origin.

### External Evaluation (ARI)

- **KMeans @ k=10** gave the best alignment with true tissue labels.
- **Agglomerative clustering** also performed reasonably well, with slightly lower ARI.

---

## Dimensionality Reduction and Visualization
- UMAP and PCA was attempted but encountered environment issues; not included.

---

## Gene Importance Analysis

To identify which genes drive clustering results:

### Cluster-Specific Gene Expression
- Calculated **mean expression per cluster**.
- Identified top 10 genes per cluster with highest average expression.
- Created a **heatmap** of selected genes across clusters.

### Biological Interpretation
- Some top-expressed genes were tissue-specific (e.g., neural genes enriched in Brain clusters).
- Validates the biological signal driving clustering beyond statistical similarity.

---

## Reproducibility

- All random seeds are fixed via `random_state=42` across clustering models and data selection.
- Environment dependencies are listed in `requirements.txt`.
- Code is organized in a single Jupyter notebook, annotated and reproducible.

---

## Conclusion

Unsupervised clustering of GTEx gene expression data reveals strong alignment with tissue of origin. 
- KMeans at `k=10` best recovered biological labels.
- Internal and external metrics support this result.
- Gene-level interpretation provided biologically meaningful insights into tissue identity.

---

## Files Included

- `assignment_1.ipynb` – Jupyter notebook with complete pipeline
- `report.md` – This file
- `README.md` – Project overview and usage
- `requirements.txt` – Python environment dependencies

---

