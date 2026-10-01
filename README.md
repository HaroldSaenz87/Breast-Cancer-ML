# Breast Cancer Diagnosis with Machine Learning

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HaroldSaenz87/Breast-Cancer-ML/blob/main/breast_cancer_ml.ipynb)

A machine learning project that predicts whether a breast tumor is **malignant** (cancerous) or **benign** (not cancerous) from measurements of cell nuclei in a tissue sample.

**Problem type:** supervised learning, binary classification

## Dataset

[Breast Cancer Wisconsin (Diagnostic)](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic) from the UCI Machine Learning Repository (CC BY 4.0).

- **569 patients**: 357 benign, 212 malignant
- **30 features** computed from digitized images of a fine needle aspirate (FNA) of a breast mass
- **10 nucleus measurements:** radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension
- Each measurement is summarized 3 ways:

| Suffix | Meaning |
|---|---|
| `_avg` | average across all cells in the image |
| `_variation` | how much the cells differ (standard error) |
| `_largest` | average of the 3 largest values, the most abnormal cells |

## Project Steps

1. **Load the data:** add column names to the raw file
2. **Explore:** check shape, data types, and missing values
3. **Clean:** drop the ID column and encode the diagnosis (M = 1, B = 0)
4. **Visualize:** class balance, feature distributions, correlation with diagnosis
5. **Prepare:** 80/20 stratified train/test split and feature scaling
6. **Train:** Logistic Regression and Random Forest
7. **Evaluate:** accuracy, recall, classification report, confusion matrix
8. **Predict:** test patients and new patients loaded from a CSV file

## Results

| Model | Accuracy | Recall (malignant) |
|---|---|---|
| Logistic Regression | 96.5% | 92.9% |
| Random Forest | 97.4% | 92.9% |

- **Recall** is the key metric: it measures how many actual cancers the model catches. Missing a cancer is worse than a false alarm.
- The strongest predictors were tumor size (`radius`, `perimeter`, `area`) and shape irregularity (`concave_points`, `concavity`).
- The model returns a **probability**, not just a label. Values near 0.5 are uncertain cases that need closer review.

## Files

| File | Description |
|---|---|
| `breast_cancer_ml.ipynb` | Notebook with code, charts, and results |
| `breast_cancer_ml.py` | Plain Python version of the code |
| `wdbc.data` | The dataset |
| `new_patients.csv` | The new patients you want to predict |

## How to Run

1. Click the **Open in Colab** badge at the top of this page
2. Download `wdbc.data` from this repository, then upload it using the **Files** panel in Colab
3. Select **Runtime → Run all**


## Tools

Python, pandas, NumPy, Matplotlib, Seaborn, scikit-learn, Google Colab

---

*This is an educational project and is not a medical diagnostic tool.*
