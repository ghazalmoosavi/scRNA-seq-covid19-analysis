# Deep Learning for Single-Cell Analysis in Microfluidic Systems

### *(scRNA-seq Analysis of COVID-19 PBMCs: From Preprocessing to Predictive Modeling)*

## 📌 Overview

This repository presents a comprehensive single-cell RNA sequencing (scRNA-seq) analysis pipeline for studying immune responses in COVID-19 patients. The project integrates bioinformatics preprocessing, statistical analysis, and machine learning modeling to identify patterns associated with disease severity.

The primary goal is to transform high-dimensional transcriptomic data into interpretable and predictive models, with a strong emphasis on methodological rigor and avoiding data leakage.

---

## 🎯 Objectives

* Build an end-to-end scRNA-seq analysis pipeline
* Perform cell-type identification and biological interpretation
* Develop machine learning models for disease severity prediction
* Address data leakage and validation challenges
* Extract robust and generalizable biological insights

---

## 🧬 Dataset

* Source: GEO Dataset (Accession: GSE293707)
* Samples:

  * Healthy
  * Mild COVID-19
  * Severe COVID-19
  * Critical COVID-19
* Size:

  * ~72,000 cells
  * ~36,000 genes

Important limitation: Only one healthy sample leads to a risk of pseudo-replication and requires careful interpretation.

---

## ⚙️ Pipeline Overview

### 1. Data Preprocessing

* Quality Control (QC):

  * Gene count filtering
  * UMI count filtering
  * Mitochondrial percentage filtering
* Normalization (log transformation)
* Highly Variable Gene (HVG) selection (Top 3000 genes)

### 2. Dimensionality Reduction & Clustering

* PCA (Principal Component Analysis)
* Selection of ~20 principal components
* Leiden clustering with resolution tuning
* Visualization of cell distributions

### 3. Cell Type Annotation

Identified major immune cell types:

* CD4+ T Cells
* CD8+ T Cells
* NK Cells
* B Cells
* Monocytes
* Dendritic Cells
* Plasma Cells
* Megakaryocytes

### 4. Feature Engineering

* Differentially Expressed Genes (DEGs)
* Cell-type-specific gene expression profiles
* Aggregation for model input

### 5. Machine Learning Models

* Linear Discriminant Analysis (LDA)
* Logistic Regression
* Support Vector Machine (SVM - Linear Kernel)
* Multi-Layer Perceptron (MLP)

### 6. Validation Strategy (Key Contribution)

Leave-One-Severity-Out (LOSO) Cross-Validation:

* Prevents leakage across severity groups
* Improves generalization
* Provides more reliable evaluation

---

## 📊 Results

### Key Findings

* MLP achieved:

  * Accuracy: 0.964
  * AUC: 0.995
* Linear models performed competitively with deep learning
* Strong biological signal observed in immune cell populations

### Critical Insight

Initial results were artificially inflated due to data leakage. After correcting the pipeline, performance decreased to realistic levels, resulting in more reliable and scientifically valid conclusions.

---

## 🧠 Key Contributions

* Developed a robust and reproducible scRNA-seq pipeline
* Identified and corrected data leakage issues
* Designed a LOSO validation strategy
* Demonstrated that well-engineered features enable strong performance even with linear models

---

## 🛠️ Technologies Used

* Python
* Scanpy
* NumPy
* Pandas
* Scikit-learn
* PyTorch
* Matplotlib

---

## 🚀 How to Run

Clone the repository:
git clone https://github.com/your-username/repo-name.git
cd repo-name

Install dependencies:
pip install -r requirements.txt

Run the notebook:
jupyter notebook

---

## ⚠️ Limitations

* Limited biological replicates
* Potential residual feature-level leakage
* Results require careful biological interpretation

---

## 🔮 Future Work

* Add more biological samples
* Apply pseudo-bulk analysis
* Improve feature selection (e.g., ElasticNet)
* Explore advanced deep learning models
* Integrate multi-modal datasets


