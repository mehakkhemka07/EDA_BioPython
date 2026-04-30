# Breast Cancer Diagnosis – Exploratory Data Analysis

Uncovering patterns in tumour morphology features that distinguish malignant from benign breast masses using the UCI Breast Cancer Wisconsin dataset.

---

## Repository Structure

```
breast-cancer-eda/
├── Breast_Cancer_Diagnosis.csv   # Dataset (569 records, 32 features)
├── EDA_Breast_Cancer.py          # Full EDA script
└── README.md
```

---

## Dataset

| Property | Details |
|---|---|
| **Source** | UCI Machine Learning Repository – Breast Cancer Wisconsin |
| **Records** | 569 |
| **Features** | 30 numerical + 1 ID + 1 target (Diagnosis) |
| **Target classes** | B – Benign (357, 63%) / M – Malignant (212, 37%) |
| **Missing values** | None |

Features are computed from digitised fine needle aspirate (FNA) biopsy images. Mean, standard error, and worst values of 10 measurements (radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension) are recorded per nucleus.

---

## Setup

```bash
pip install numpy pandas matplotlib seaborn
```

```bash
python EDA_Breast_Cancer.py
```

---

## EDA Workflow

| Step | Description |
|---|---|
| 01 | Data loading and cleaning — inspected shape, dtypes, null counts; no imputation needed |
| 02 | Descriptive statistics — mean, median, mode, SD; identified high-variance and skewed features |
| 03 | Visualisation — countplot, histograms, boxplots, scatter, violin, heatmap, pairplot |
| 04 | Insight extraction — class separation, multicollinearity, and discriminative features identified |

---

## Visualisations

| Plot | Key Takeaway |
|---|---|
| Diagnosis distribution (countplot) | Benign majority — 63 vs 37% |
| Radius mean (histogram) | Clear bimodal split between classes |
| 6 mean features (boxplot) | Malignant tumours larger across all features |
| Radius vs texture (scatter) | Partial but visible linear class separation |
| Area mean (violin) | Malignant distribution has heavier upper tail |
| Mean features (heatmap) | radius, perimeter, and area near-perfectly correlated |
| 4 features (pairplot) | Strong inter-feature clustering by class |

---

## Key Insights

1. **Size features are the strongest separators** — malignant tumours consistently show larger radius, perimeter, and area across all samples.
2. **Extreme multicollinearity** — radius_mean, perimeter_mean, and area_mean correlate at r > 0.99; using all three in a linear model will cause instability.
3. **Concavity and concave points are highly discriminative** — shape irregularity features show the widest gap between benign and malignant classes.
4. **Mild class imbalance** (63/37) — worth addressing with stratified sampling or SMOTE in any downstream classification model.
5. **Outliers present** in area_mean and perimeter_mean among malignant samples, likely representing aggressive tumour subtypes.
6. **No data quality issues** — no nulls, no duplicates, dtypes are correct throughout.

---

## Tools

Python, NumPy, Pandas, Matplotlib, Seaborn
