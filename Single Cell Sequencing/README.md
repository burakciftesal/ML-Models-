🔬 Interpretable Cell Type Classification in scRNA-seq using XGBoost + SHAP
📘 Overview
This project presents an end-to-end pipeline that combines unsupervised clustering, supervised machine learning, and model interpretation to analyze single-cell RNA sequencing (scRNA-seq) data.
Using the PBMC 20k dataset, we aim to:

Discover meaningful immune cell clusters

Train an XGBoost classifier to predict cluster identity from gene expression

Use SHAP values to understand which genes drive these predictions

Compare SHAP-selected features with traditional highly variable genes (HVGs)

🎯 Final goal: Biologically interpretable and compact feature selection using machine learning.

🧪 Dataset

## 📂 Dataset

This project uses the [PBMC 20k single-cell RNA-seq dataset](https://www.10xgenomics.com/resources/datasets/20-k-pbm-cs-from-a-healthy-donor-2-standard-3-1-chemistry-3-1-standard) provided by [10x Genomics](https://www.10xgenomics.com/).

- Format: `.h5ad` (converted from raw `.mtx`)
- Cells: ~20,000
- Application: Immune profiling, marker discovery
Source: 10X Genomics – Peripheral Blood Mononuclear Cells (PBMC) 20k dataset


Features: ~2,000 highly variable genes selected from raw count matrix

Annotation: Leiden clustering followed by SHAP-guided biological interpretation

🧠 Methodology
1. Preprocessing
Filtering low-quality genes and cells

Normalization and log transformation

Selection of top 2,000 highly variable genes

2. Clustering & Dimensionality Reduction
PCA → Neighbors → UMAP

Leiden algorithm for clustering (21 clusters)

3. Supervised Learning with XGBoost
Cluster labels from Leiden used as targets

XGBoost trained to predict cluster identity from gene expression

High per-cluster accuracy verified via confusion matrix

🔍 Note: Although Leiden is unsupervised, its cluster labels enable a supervised training setup.

4. Interpretability with SHAP
SHAP values computed to identify influential genes

Top SHAP genes selected per cluster and globally ranked

5. Comparison with HVGs
Overlap analysis between SHAP genes and HVGs

Identification of SHAP-only markers → used for model retraining

6. Retraining on SHAP-only Genes
New XGBoost model trained on reduced feature set

Maintained high accuracy, improving interpretability

AUC used to further rank SHAP-only genes

📊 Key Visuals
SHAP Summary Plot: Top genes influencing cluster predictions

Annotated UMAP: Color-coded clusters with biological annotations

Gene Expression UMAP + Histogram: e.g., S100A8 localization

SHAP vs HVG comparison bar plot

📈 Results
✅ XGBoost classifier achieved >90% accuracy across most clusters

✅ SHAP interpretation revealed known immune markers (e.g., S100A8, CD14, GNLY)

✅ SHAP-only gene model was compact yet biologically informative

✅ Final AUC ranking helped prioritize marker gene candidates

💡 Conclusion
This project demonstrates a powerful and interpretable ML pipeline for scRNA-seq analysis:

Combines unsupervised discovery with supervised understanding

Provides actionable gene insights for each cluster

Offers compact feature sets for downstream biology and research

📌 Ideal for researchers who want to go beyond clustering and extract biological meaning using explainable AI.

🛠️ Tech Stack
Python, Scanpy, XGBoost, SHAP, Scikit-learn, Seaborn, Matplotlib

🧬 Next Steps (Optional Ideas)
Use true biological labels (if available) instead of Leiden

Compare SHAP with other explainability tools (e.g., LIME)

Test transferability on another scRNA-seq dataset