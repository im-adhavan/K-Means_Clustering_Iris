# K-Means Clustering on the Iris Dataset

## Overview
This repository presents a structured and analytical implementation of **K-Means clustering** applied to the classical **Iris dataset**. The objective is not merely to demonstrate the algorithm, but to critically examine its behavior, assumptions, and limitations in a low-dimensional, well-understood setting.

Although the Iris dataset includes ground-truth class labels, clustering is performed in a strictly **unsupervised** manner. Labels are used only for post-hoc evaluation and interpretation.

---

## Motivation
K-Means is often introduced as a simple clustering baseline, yet its assumptions are strong and frequently violated in real-world data:

- Clusters are assumed to be spherical
- Feature scales strongly influence distance computations
- Cluster assignments depend on Euclidean geometry

By applying K-Means to the Iris dataset, this project highlights:
- When K-Means succeeds due to favorable geometry
- Where it fails due to overlapping class structure
- Why preprocessing and evaluation choices matter

This analysis emphasizes **understanding over performance**.

---

## Dataset
The Iris dataset consists of:
- 150 samples
- 4 continuous features:
  - Sepal length
  - Sepal width
  - Petal length
  - Petal width
- 3 species (labels used only for evaluation)

The dataset is loaded directly from `scikit-learn`, ensuring reproducibility and consistency.

---

## Methodology

### Preprocessing
- Features are standardized using `StandardScaler`
- Standardization is critical due to K-Means’ reliance on Euclidean distance

### Clustering
- K-Means is applied with:
  - `k = 3` clusters
  - Fixed random seed for reproducibility
- Cluster centroids are learned in standardized feature space

### Evaluation
- Clustering quality is assessed using the **Silhouette Score**
- This metric evaluates intra-cluster cohesion versus inter-cluster separation
- A silhouette score of approximately **0.48** indicates moderate structure, consistent with known overlap in the dataset

### Visualization
- Principal Component Analysis (PCA) is used **only for visualization**
- Data is projected into two dimensions
- Cluster assignments and centroids are visualized in PCA space

---

## Key Observations
- One Iris species is cleanly separated, aligning well with K-Means assumptions
- The remaining two species exhibit significant overlap, limiting clustering performance
- Cluster labels are arbitrary up to permutation and carry no semantic meaning
- PCA aids interpretability but does not influence clustering itself

These results illustrate that K-Means performance is governed more by **data geometry** than algorithmic complexity.

---

## Repository Structure

├── k-means-clustering.ipynb # Main analysis notebook

├── requirements.txt # Minimal dependencies

├── .gitignore

└── README.md

---

## Reproducibility

### Installation
```bash
pip install -r requirements.txt
