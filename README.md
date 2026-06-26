
# 📊 Data Science Learning Portfolio

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0-green?style=flat&logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/ScikitLearn-1.3-orange?style=flat&logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow?style=flat)
![Notebooks](https://img.shields.io/badge/Notebooks-3-purple?style=flat&logo=jupyter)

---

## 👩‍💻 About This Repository

This repository documents my **Data Science learning journey** — from Statistics basics all the way to Machine Learning algorithms and a real-world project.

Every notebook is written with a consistent structure:
- 📖 **Theory first** — concept clearly explained in simple language
- 💻 **Code second** — hands-on practice with working examples
- 📊 **Visualization** — charts to understand every pattern
- ✅ **Key Takeaways** — summary at the end of every lesson

---

##  Repository Structure

```
data-science-learning/
│
├── 01_Statistics_EDA/
│   └── Statistics_EDA_Complete.ipynb
│
├── 02_Machine_Learning/
│   ├── ML_Complete_Notebook.ipynb
│   └── ML_Next_Topics_Notebook.ipynb
│
├── 03_Projects/
│   └── Online_Retail_Analysis.ipynb
│
└── README.md
``
---

##  Notebook 1 — Statistics & EDA

**File:** `01_Statistics_EDA/Statistics_EDA_Complete.ipynb`

| Lesson | Topic | Key Concepts |
|--------|-------|-------------|
| 1 | **Mean, Median, Mode** | Central tendency, when to use which, outlier effect |
| 2 | **Standard Deviation** | Variance, spread, outlier detection using SD |
| 3 | **Correlation** | Positive/Negative/No correlation, Heatmap, r value |
| 4 | **Distribution** | Normal distribution, 68-95-99.7 rule, Skewness, Log transform |
| 5 | **EDA** | Full exploratory analysis pipeline on real dataset |

**What I Practiced:**
- Detecting and handling outliers using Mean ± 3×SD rule
- Identifying skewed distributions and fixing with Log Transform
- Building Correlation Heatmaps for feature selection
- Complete EDA pipeline: overview → numeric → categorical → relationships → summary

---

##  Notebook 2 — Machine Learning (Part 1)

**File:** `02_Machine_Learning/ML_Complete_Notebook.ipynb`

| Algorithm | Type | Problem | Metric |
|-----------|------|---------|--------|
| **Linear Regression** | Regression | Predict exam marks (number) | R², MAE, RMSE |
| **Logistic Regression** | Classification | Predict Pass/Fail (binary) | Accuracy, Confusion Matrix |
| **Decision Tree** | Classification | Predict Grade A/B/C | Accuracy, Feature Importance |

**ML Pipeline followed every time:**
```python
# 1. Features (X) and Target (y) split
# 2. Train/Test Split (80/20)
# 3. Model .fit() on training data
# 4. Model .predict() on test data
# 5. Evaluate with the right metric
# 6. Visualize results
```

**Key Concepts Covered:**
- Train/Test Split — why we never test on training data
- Overfitting vs Underfitting — with visualization
- Confusion Matrix — TP, TN, FP, FN explained
- Feature Importance — which columns matter most

---

## 🤖 Notebook 3 — Machine Learning (Part 2)

**File:** `02_Machine_Learning/ML_Next_Topics_Notebook.ipynb`

| Topic | Type | Key Concept |
|-------|------|-------------|
| **Random Forest** | Ensemble | 100 trees ka vote → better than 1 tree |
| **Feature Scaling** | Preprocessing | StandardScaler & MinMaxScaler |
| **K-Nearest Neighbors** | Classification | Nearest neighbors se classify karo |
| **Cross Validation** | Evaluation | 5-Fold CV → reliable score |
| **Hyperparameter Tuning** | Optimization | GridSearchCV → best settings auto |
| **K-Means Clustering** | Unsupervised | Khud groups dhundho — no target needed |

**Advanced Pipeline:**
```python
scaler = StandardScaler()
X_train_sc = scaler.fit_transform(X_train)   # fit + transform
X_test_sc  = scaler.transform(X_test)        # sirf transform!

model = RandomForestClassifier()
scores = cross_val_score(model, X, y, cv=5)  # reliable evaluation

grid = GridSearchCV(model, param_grid, cv=5, n_jobs=-1)
grid.fit(X_train_sc, y_train)                # best params auto!
```

**Key Concepts Covered:**
- Why Random Forest beats a single Decision Tree (Bagging)
- Data Leakage — why `fit_transform()` only on training data
- K selection in KNN — using accuracy vs k curve
- Cross Validation vs simple train/test split
- GridSearchCV — automatic hyperparameter search
- Elbow Method — finding best k in K-Means

---

## 🛒 Notebook 4 — Real World Project

**File:** `03_Projects/Online_Retail_Analysis.ipynb`

**Dataset:** [Online Retail II UCI — Kaggle](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci)

A complete end-to-end data analysis project on a **1 million+ row real e-commerce dataset** from a UK-based online store (2009–2011).

### Data Cleaning (8 Steps):

| Step | Problem | Solution |
|------|---------|----------|
| Duplicates | Repeated rows | `drop_duplicates()` |
| Cancelled Orders | Invoice starting with 'C' | Flag + Remove |
| Description | Extra spaces, ALL CAPS | `str.strip()`, `str.title()` |
| Quantity | Negative & zero values | Filter `> 0` |
| Price | Zero & negative prices | Filter `> 0` |
| Customer ID | Float type, 243k missing | `fillna(0)`, `astype(int)` |
| InvoiceDate | Stored as text | `pd.to_datetime()` |
| Country | Old names (EIRE, RSA) | `.replace()` |

### Feature Engineering:
- `Revenue` = Price × Quantity
- Extracted Year, Month, Day of Week, Hour from InvoiceDate
- Created `Price_Tier` using `pd.cut()`
- Created `Is_Guest` flag for anonymous customers

### Business Insights Found:
- 📈 Revenue peaks in **November/December** (Christmas shopping!)
- 📅 Best day is **Thursday** — B2B customers order on weekdays
- 🕙 Peak hour is **10 AM – 2 PM**
- 🌍 Top countries (ex-UK): Netherlands, Ireland, Germany
- 👤 Registered customers spend **more per order** than guests

---

## 🛠️ Tools & Libraries

```python
import pandas as pd              # Data manipulation
import numpy as np               # Numerical operations
import matplotlib.pyplot as plt  # Basic plotting
import seaborn as sns            # Advanced visualization
from scipy import stats          # Statistics functions

# Machine Learning
from sklearn.preprocessing import StandardScaler, MinMaxScaler
from sklearn.model_selection import train_test_split, cross_val_score, GridSearchCV
from sklearn.linear_model import LinearRegression, LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.cluster import KMeans
from sklearn.metrics import accuracy_score, r2_score, confusion_matrix, silhouette_score
```

---

##  How to Run Any Notebook

1. Open [Google Colab](https://colab.research.google.com)
2. Click `File → Upload Notebook`
3. Upload the `.ipynb` file
4. Click `Runtime → Run All`

> **Note for Project Notebook:** Download the dataset from Kaggle and upload `online_retail_II.csv` to Colab before running.

---

##  Learning Roadmap

```
✅ Python Basics
✅ Pandas — Data Cleaning & Manipulation
✅ Statistics — Mean, SD, Correlation, Distribution
✅ EDA — Exploratory Data Analysis
✅ Linear Regression
✅ Logistic Regression
✅ Decision Tree
✅ Random Forest
✅ Feature Scaling (StandardScaler, MinMaxScaler)
✅ K-Nearest Neighbors (KNN)
✅ Cross Validation (K-Fold)
✅ Hyperparameter Tuning (GridSearchCV)
✅ K-Means Clustering (Unsupervised)
✅ Real World Project (1M+ rows, end-to-end)

⏳ SQL for Data Analysis
⏳ Power BI / Tableau
⏳ Deep Learning Basics
```

---

## 📈 Skills Demonstrated

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `Scikit-learn` · `Data Cleaning` · `Feature Engineering` · `EDA` · `Statistical Analysis` · `Linear Regression` · `Logistic Regression` · `Decision Tree` · `Random Forest` · `KNN` · `K-Means Clustering` · `Cross Validation` · `Hyperparameter Tuning` · `Feature Scaling` · `Data Visualization`

---

> *"Data cleaning takes 80% of the time — but it is what makes or breaks your analysis."*
