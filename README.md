# Reproduction of Machine Learning Benchmarking Study for Elastic Properties of Materials

This project reproduces the core machine learning pipeline presented in the research paper:

> **Evaluating Generalized Feature Importance via Performance Assessment of Machine Learning Models for Predicting Elastic Properties of Materials**  
> Banik et al., ChemRxiv (2023)  
> DOI: https://doi.org/10.26434/chemrxiv-2023-07vcr-v2

The objective of this project is to reproduce the methodology and evaluate the performance of multiple machine learning regression models for predicting the elastic properties of crystalline materials using the Matbench Elastic dataset.

---

## Project Overview

Traditional Density Functional Theory (DFT) calculations provide accurate elastic properties but are computationally expensive for large-scale materials screening. This project demonstrates how machine learning can be used to predict elastic properties efficiently using structural descriptors extracted from crystal structures.

This work was completed as part of the **AI for Material Science (EP-208)** course at **Delhi Technological University**.

---

## Objectives

- Reproduce the machine learning workflow described in the original research paper.
- Extract physically meaningful descriptors from crystal structures.
- Rank features using correlation-based feature selection.
- Train and compare multiple regression models.
- Interpret model predictions using feature importance and SHAP analysis.
- Compare reproduced results with those reported in the original study.

---

## Dataset

**Dataset:** Matbench Elastic Benchmark Dataset

Loaded directly using the `matminer` library.

```python
from matminer.datasets import load_dataset

df = load_dataset("matbench_log_kvrh")
```

The dataset contains **10,987 crystalline materials** obtained from the Materials Project database.

Target variables:

- log10(K_VRH) – Bulk Modulus
- log10(G_VRH) – Shear Modulus

---

## Feature Engineering

The following structural descriptors were extracted from each crystal structure:

- Density
- Volume
- Number of Atomic Sites
- Lattice Parameters (a, b, c)
- Lattice Angles (α, β, γ)
- Mean Lattice Parameter
- Standard Deviation of Lattice Parameters
- Volume per Atom (VPA)
- Number of Elements
- Average Atomic Weight
- Formula Units

Correlation analysis was used to rank the features, and the top features were selected for model training.

---

## Machine Learning Models

The following regression models were evaluated:

- Linear Regression (LR)
- K-Nearest Neighbors (KNN)
- Support Vector Regression (SVR)
- Random Forest Regressor (RF)
- Kernel Ridge Regression (KRR)
- Gradient Boosting Regressor (GBM)

Model performance was evaluated using **Mean Absolute Error (MAE)**.

---

## Workflow

1. Load Matbench Elastic Dataset
2. Extract structural descriptors
3. Perform feature engineering
4. Rank important features
5. Select top features
6. Split dataset into training and testing sets
7. Train multiple regression models
8. Compare model performance
9. Analyze feature importance
10. Perform SHAP analysis
11. Generate learning curves

---

## Results

The reproduced workflow successfully captured the major findings of the original study.

Key observations:

- Random Forest achieved the best predictive performance.
- Volume per Atom (VPA) and Density emerged as the most influential descriptors.
- Feature importance analysis aligned closely with the published research.
- Learning curves demonstrated stable model convergence.

---

## Repository Structure

```
Elastic-property-prediction-replication-with-ML
│
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
│
├── notebook
│   └── Materials_ML_Replication.ipynb
│
├── report
│   └── Project_Report.pdf
│
└── results
    ├── correlation_matrix.png
    ├── feature_ranking.png
    ├── model_comparison.png
    ├── feature_importance.png
    └── learning_curve.png
```

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Matminer
- Pymatgen
- SHAP

---

## Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/Elastic-property-prediction-replication-with-ML.git
```

Install the required packages:

```bash
pip install -r requirements.txt
```

---

## How to Run

Open the notebook:

```
notebook/Materials_ML_Replication.ipynb
```

Run all cells sequentially to reproduce the complete machine learning workflow.

---

## Future Improvements

- Implement the original mRMR feature selection method.
- Benchmark additional ensemble learning models.
- Perform hyperparameter optimization.
- Extend the workflow to graph neural network models.
- Compare performance on additional Matbench datasets.

---

## Acknowledgements

This work is a reproduction study based on the research by **Banik et al. (2023)** and was completed as part of the **AI for Material Science (EP-208)** course at **Delhi Technological University**.

---

## Author

**Lokesh Sharma**

B.Tech Engineering Physics

Delhi Technological University

GitHub: https://github.com/LokeshSharma891
