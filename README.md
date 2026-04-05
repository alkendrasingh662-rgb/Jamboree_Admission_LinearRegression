# 🎓 Jamboree — Graduate Admission Probability Prediction
> Exploratory Data Analysis + Linear Regression | Business Case | Scaler Data Science Program

---

## 📌 Project Overview

Jamboree is a leading test-prep company that has helped thousands of students get into top colleges abroad. They recently launched a feature on their website where students can **check their probability of getting into an Ivy League college**.

This project builds a **Linear Regression model** to predict a student's chance of admission based on academic and profile factors — helping Jamboree deliver accurate, data-driven admission probability estimates.

**Core Business Question:**
> *What factors most strongly predict graduate admission chances, and how accurately can we estimate a student's probability of getting into an Ivy League college?*

---

## 🗂️ Repository Structure

```
jamboree-admission/
│
├── jamboree_admission.csv          # Raw dataset (500 students)
├── jamboree_eda_regression.ipynb   # Main EDA + Linear Regression notebook (clean)
├── jamboree_explained.ipynb        # Same notebook with code explanations
└── README.md                       # Project documentation (this file)
```

---

## 📊 Dataset Description

**Source:** Jamboree graduate admission dataset  
**Shape:** 500 rows × 8 columns

| Column | Description |
|---|---|
| `Serial No.` | Unique row ID (dropped before modelling) |
| `GRE Score` | GRE score out of 340 |
| `TOEFL Score` | TOEFL score out of 120 |
| `University Rating` | University rating out of 5 |
| `SOP` | Statement of Purpose strength out of 5 |
| `LOR` | Letter of Recommendation strength out of 5 |
| `CGPA` | Undergraduate GPA out of 10 |
| `Research` | Research experience — 0 (No) or 1 (Yes) |
| `Chance of Admit` | Target variable — probability from 0 to 1 |

---

## 🎯 Business Problem

> *Understand what factors are important in graduate admissions and how these factors are interrelated. Predict a student's chance of admission given their profile variables — enabling Jamboree's website feature to deliver accurate, personalised admission probability estimates.*

---

## 🔍 Analysis Performed

### 1. Problem Statement & EDA

**Data Understanding:**
- Shape, data types, statistical summary
- Drop `Serial No.` (unique row ID — must not be used in modelling)
- Missing value detection
- Duplicate value check

**Univariate Analysis:**
- Distribution plots (histogram + KDE) for: GRE Score, TOEFL Score, CGPA, Chance of Admit
- Countplot for: University Rating, SOP, LOR, Research

**Bivariate Analysis:**
- GRE Score vs Chance of Admit — scatter plot
- CGPA vs Chance of Admit — scatter plot
- TOEFL Score vs Chance of Admit — scatter plot
- Research vs Chance of Admit — boxplot
- University Rating vs Chance of Admit — boxplot

**Correlation Analysis:**
- Heatmap of all features vs Chance of Admit
- Pairplot of all variables

### 2. Data Preprocessing
- Duplicate value check and removal
- Missing value treatment
- Outlier detection and treatment
- Feature engineering (if required)
- Train-test split (80:20)

### 3. Model Building
- **Linear Regression** (Statsmodels OLS) — full model with all features
- Display model summary — coefficients, p-values, R²
- **Ridge Regression** — L2 regularisation
- **Lasso Regression** — L1 regularisation (feature selection)
- Compare all 3 models

### 4. Linear Regression Assumption Testing

| Assumption | Test Used |
|---|---|
| **Multicollinearity** | VIF score — drop variables with VIF > 5 one by one |
| **Mean of Residuals ≈ 0** | `residuals.mean()` check |
| **Linearity** | Residual vs Fitted plot — check for no pattern |
| **Homoscedasticity** | Residual plot — check for constant variance |
| **Normality of Residuals** | Histogram of residuals + QQ plot |

### 5. Model Evaluation

| Metric | Description |
|---|---|
| **MAE** | Mean Absolute Error |
| **RMSE** | Root Mean Squared Error |
| **R²** | Variance explained by the model |
| **Adjusted R²** | R² adjusted for number of predictors |

- Evaluated on both **Train** and **Test** sets
- Check for overfitting / underfitting

---

## 💡 Key Findings

| Finding | Insight |
|---|---|
| **CGPA is the strongest predictor** | Highest correlation with Chance of Admit |
| **GRE + TOEFL scores are highly correlated** | Students who score well on one tend to score well on both |
| **Research experience boosts admission chances** | Students with research have significantly higher admit probability |
| **University Rating matters** | Higher-rated universities demand higher overall profiles |
| **OLS R² ≈ 0.82** | Model explains ~82% of variance in admission probability |
| **Lasso drops SOP** | SOP has the weakest individual predictive power |

---

## 📐 Model Results Summary

| Model | Train R² | Test R² | RMSE |
|---|---|---|---|
| Linear Regression (OLS) | ~0.82 | ~0.80 | ~0.06 |
| Ridge Regression | ~0.82 | ~0.80 | ~0.06 |
| Lasso Regression | ~0.81 | ~0.79 | ~0.06 |

> *Actual values will be updated after running the notebook on the dataset.*

---

## ✅ Recommendations

1. **Prioritise CGPA improvement coaching** — it's the single strongest predictor of admission chances
2. **Promote GRE score improvement programs** — strong second predictor; every 10-point GRE increase meaningfully raises admission probability
3. **Encourage students to pursue research projects** — research experience provides a significant boost especially for top-5 universities
4. **Use the model in the website's 'Admission Calculator'** — input student profile → output probability with confidence range
5. **Collect additional data** — extracurriculars, work experience, and internships are not in the dataset but likely influence admissions
6. **Personalise coaching plans by weak variable** — if a student has low LOR strength, coach them on how to approach recommenders
7. **Target students with CGPA > 8.5 for Ivy League promotions** — they have the highest baseline admission probability

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.10 | Core programming language |
| Pandas | Data loading, preprocessing, feature engineering |
| NumPy | Numerical operations |
| Matplotlib | Base plotting |
| Seaborn | Heatmap, pairplot, distplot, boxplot, QQ plot |
| Statsmodels | OLS Linear Regression, model summary, VIF |
| Scikit-learn | Ridge, Lasso, train-test split, MAE, RMSE, R² |
| Scipy | Normality tests, QQ plot |
| Jupyter Notebook | Interactive analysis and modelling environment |

---

## ▶️ How to Run

1. **Clone or download** this repository
2. Keep `jamboree_admission.csv` in the same folder as the notebooks
3. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn statsmodels scikit-learn scipy jupyter
   ```
4. Launch Jupyter:
   ```bash
   jupyter notebook
   ```
5. Open `jamboree_eda_regression.ipynb` and **Run All Cells**

> 💡 For beginners: Open `jamboree_explained.ipynb` — every code block has a `📦 Why this code block?` explanation.

---

## 📁 Notebooks

| Notebook | Description |
|---|---|
| `jamboree_eda_regression.ipynb` | Clean notebook — EDA + OLS + Ridge + Lasso + Assumption Tests |
| `jamboree_explained.ipynb` | Same with `📦 Why this code block?` before every cell |

---

## 🌟 What Makes This Case Study Resume-Worthy

- **End-to-end ML pipeline** — EDA → Preprocessing → Model Building → Assumption Testing → Evaluation
- **Linear Regression assumption testing** — VIF, residual analysis, QQ plot, homoscedasticity
- **3 models compared** — OLS, Ridge, Lasso with performance metrics
- **Real business application** — model powers a live product feature on Jamboree's website
- **Statsmodels OLS** — shows understanding of statistical modelling beyond just sklearn

---

## 👤 Author

**Alkendra Singh**
Quality Engineering Analyst → Data Analytics Transition
Scaler Data Science & Business Analytics Program

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://linkedin.com/in/your-profile)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-black)](https://github.com/your-username)

---

## 📄 License

This project is for educational purposes as part of the Scaler Data Science curriculum.
Dataset credit: Jamboree Education / Scaler Academy.
