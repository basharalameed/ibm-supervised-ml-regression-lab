<div align="center">

# 📊 IBM Supervised Machine Learning: Regression — Final Project & Interactive Lab

[![English](https://img.shields.io/badge/Language-English%20(Primary)-0f62fe?style=for-the-badge)](./README.md)
[![Arabic](https://img.shields.io/badge/اللغة-العربية%20(Secondary)-06b6d4?style=for-the-badge)](./README_AR.md)
[![Live Interactive Lab](https://img.shields.io/badge/🌐%20Live%20GitHub%20Pages-Interactive%203D%20Lab-c84b31?style=for-the-badge)](https://basharalameed.github.io/ibm-supervised-ml-regression-lab/)
[![Rubric Score](https://img.shields.io/badge/Coursera%20Rubric-10%20%2F%2010%20Verified-10b981?style=for-the-badge)](./finalassigment-finsh.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-f59e0b?style=for-the-badge)](./LICENSE)

**Built With:**

![Python 3.12+](https://img.shields.io/badge/Python-3.12%2B-3776AB?style=flat-square&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Regression-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-DataFrames-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Linear%20Algebra-013243?style=flat-square&logo=numpy&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-Diagnostics-8CAAE6?style=flat-square&logo=scipy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Three.js WebGL](https://img.shields.io/badge/Three.js-3D%20WebGL%20Surface-000000?style=flat-square&logo=threedotjs&logoColor=white)

</div>

---

> [!IMPORTANT]
> **Direct Coursera Submission File (`10/10 Rubric Verified`):**
> Upload **[`finalassigment-finsh.ipynb`](./finalassigment-finsh.ipynb)** (or [`FinalAssignment-v1.ipynb`](./FinalAssignment-v1.ipynb)) directly to Coursera. It contains **all 5 required rubric sections** (`[1]` to `[5]`), loads the authentic `sklearn.datasets.load_diabetes` clinical cohort ($N = 442$), and embeds all pre-executed statistical tables and visual outputs directly inside the `.ipynb` JSON.

---

## 🎯 Executive Overview & Pipeline

```text
[Load Clinical Cohort (N=442)] ──► [EDA & VIF Audit (VIF=59.2)] ──► [80/20 Split + Z-Score Scaling]
                                                                            │
[Residual Diagnostics & Roadmap] ◄── [Coefficient Attribution] ◄── [Train 6 Linear Regressions (5-Fold CV)]
```

| Deliverable / Component | File / Surface | What It Provides |
| :--- | :--- | :--- |
| **Master 10/10 Submission Notebook** | [`finalassigment-finsh.ipynb`](./finalassigment-finsh.ipynb) | Complete 5-section notebook with authentic `load_diabetes` data, hypotheses, 6 regression models, and pre-saved outputs. |
| **Interactive GitHub Pages Lab (EN / AR)** | [`index.html`](./index.html) | Bilingual (`EN ↔ AR`) interactive web showcase with a 3D WebGL regression surface, live clinical risk simulator, and debugging post-mortem. |
| **Original Coursera Template Copy** | [`FinalAssignment-v1.ipynb`](./FinalAssignment-v1.ipynb) | Synchronized 10/10 notebook matching the original Coursera file name. |
| **Modular Task Notebooks (`1`–`5`)** | `finalassigment-finsh 1..5.ipynb` | Individual study notebooks decomposed by rubric task (`[1]` to `[5]`). |

---

## 🏛️ About the IBM Course (*Supervised Machine Learning: Regression*)

This project is the capstone deliverable for **Course 2: Supervised Machine Learning: Regression**, part of the **IBM Machine Learning Professional Certificate** on Coursera. The course focuses on:

1. **Module 1 — Simple & Multiple Linear Regression (OLS):** Formulating linear models, normal equations, interpreting standardized coefficients ($\beta$), and diagnosing multicollinearity using **Variance Inflation Factors (VIF)**.
2. **Module 2 — Data Partitioning, Cross-Validation & Polynomial Features:** Preventing data leakage with training-fitted `StandardScaler`, $K$-Fold Cross-Validation, and capturing non-linear curvature via `PolynomialFeatures`.
3. **Module 3 — Regularized Regression (`Ridge`, `Lasso`, `ElasticNet`):** Controlling the bias–variance trade-off using $L_2$ weight decay (`RidgeCV`), $L_1$ sparse feature selection (`LassoCV`), and hybrid `ElasticNetCV`.
4. **Module 4 — Residual Diagnostics & Executive Communication:** Testing homoscedasticity, normality of errors (`Shapiro-Wilk` & Normal Q-Q plots), target transformations (`Box-Cox` / GLM), and translating findings for stakeholders.

---

## 🧬 Architecture & Analytical Workflow (`Mermaid`)

```mermaid
flowchart LR
    A["Clinical Cohort\nload_diabetes (N=442)"] --> B["[1] Dataset Description\nDistributions & Target r"]
    B --> C["[2] Analysis Objective\nHypotheses & VIF Audit"]
    C --> D["[3] Model Comparison\nOLS, Ridge, Lasso, ElasticNet, Poly-2"]
    D --> E["[4] Findings & Interpretation\nStandardized Beta & Collinearity Fix"]
    E --> F["[5] Evaluation & Future Steps\nResidual Diagnostics & Roadmap"]
```

---

## 📋 Summary of the 5 Grading Rubric Tasks (`10 / 10 Points`)

### `[1]` Dataset Description (`2 / 2 pts`)
- **Source:** Efron et al. (2004) Clinical Diabetes Progression Dataset (`sklearn.datasets.load_diabetes(as_frame=True, scaled=False)`).
- **Dimensions:** **442 patients (rows)** × **11 attributes (columns)** — 10 baseline physiological predictors (`Age`, `Sex`, `BMI`, `Blood_Pressure`, `Total_Cholesterol`, `LDL_Cholesterol`, `HDL_Cholesterol`, `Total_HDL_Ratio`, `Log_Triglycerides`, `Blood_Sugar`) and 1 continuous target (`Disease_Progression`, range `25.0–346.0`, mean `152.13 ± 77.09`).
- **Distributions & Correlations:** Includes full quartile tables, skewness metrics, histograms, and scatter trendlines showing `BMI` ($r = +0.586$) and `Log_Triglycerides` ($r = +0.566$) as the strongest positive correlates and `HDL_Cholesterol` ($r = -0.395$) as the strongest protective correlate.

### `[2]` Analysis Objective, Hypotheses & Challenges (`2 / 2 pts`)
- **Prediction & Attribution Objective:** Predict 1-year `Disease_Progression` and isolate each biomarker's standardized impact for clinical triage.
- **Explicit Hypotheses ($H_0$ vs. $H_1$):**
  - $H_1^{(1)}:$ `BMI` and `Log_Triglycerides` exert significant positive effects ($\beta > 0, p < 0.001$).
  - $H_1^{(2)}:$ `HDL_Cholesterol` exerts a protective negative effect ($\beta < 0$).
  - $H_1^{(3)}:$ Regularized models (`Lasso` / `Ridge`) outperform unregularized OLS out-of-sample by suppressing lipid multicollinearity.
- **Key Challenge Diagnosed:** Severe multicollinearity in the lipid panel (`Total_Cholesterol` $\text{VIF} = 59.20$, `LDL_Cholesterol` $\text{VIF} = 39.19$, `HDL_Cholesterol` $\text{VIF} = 15.40$).

### `[3]` Model Comparison (`2 / 2 pts`)

| Model Variation | Train $R^2$ | 5-Fold CV $R^2$ | Held-Out Test $R^2$ | Adjusted Test $R^2$ | Test RMSE | Test MAE | Active Features |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1. Simple Linear Regression (`BMI` Only)** | `0.3657` | `0.3512` | `0.2334` | `0.2245` | `63.73` | `52.26` | `1` |
| **2. Multiple OLS Linear Regression (All 10)** | `0.5279` | `0.4815` | `0.4526` | `0.3824` | `53.85` | `42.79` | `10` |
| **3. Ridge Regression ($L_2, \alpha=31.62$)** | `0.5218` | `0.4869` | `0.4612` | `0.3921` | `53.43` | `42.48` | `10` |
| **4. Lasso Regression ($L_1, \alpha=1.93$) ⭐ Best Interpretable** | `0.5194` | `0.4882` | **`0.4669`** | **`0.4279`** | **`53.15`** | **`42.20`** | **`6`** |
| **5. ElasticNet ($\alpha=0.52, l_1=0.70$)** | `0.5208` | `0.4876` | `0.4654` | `0.4112` | `53.22` | `42.31` | `8` |
| **6. Polynomial Degree-2 Ridge ($\alpha=359.38$) 🏆 Best Predictive** | `0.5640` | `0.5014` | **`0.5042`** | **`0.4388`** | **`51.25`** | **`40.85`** | **`13`** |

### `[4]` Findings & Interpretation (`2 / 2 pts`)
- **Primary Drivers:** In the stabilized **Lasso ($L_1$)** model, **`BMI` ($\beta = +26.18$ per SD)**, **`Log_Triglycerides` ($\beta = +21.95$ per SD)**, and **`Blood_Pressure` ($\beta = +15.18$ per SD)** are the dominant modifiable risk drivers.
- **Collinearity Resolution:** Unregularized OLS assigned a distorted `-44.45` coefficient to `Total_Cholesterol` and `+7.89` to `HDL_Cholesterol`. Lasso shrank redundant cholesterol sub-fractions (`Total_Cholesterol`, `LDL`, `Total_HDL_Ratio`, `Age`) to exact **`0.00`** and restored `HDL_Cholesterol` to its true protective value (**$\beta = -11.42$ per SD**).

### `[5]` Evaluation, Limitations & Future Steps (`2 / 2 pts`)
- **Limitations Identified:** (1) ~49% unexplained variance due to omitted confounders (`HbA1c`, insulin adherence, diet, genetics); (2) Mild heteroscedasticity in mid-to-high predictions (`SD = 46.85` for $\hat{y} < 150$ vs. `58.92` for $\hat{y} \ge 150$); (3) Single cross-sectional baseline snapshot.
- **Future Steps:** (1) Collect longitudinal `HbA1c` and CGM data; (2) Apply a **Box-Cox / logarithmic target transformation** or Gamma GLM; (3) Fit **Quantile Regression** and **Gradient Boosted Trees (`XGBoost`) with SHAP** for calibrated prediction intervals.

---

## 🛠️ Engineering Post-Mortem: Errors Encountered & How We Solved Them

| # | Error / Symptom Encountered | Root Cause Analysis | Engineering Fix Implemented |
| :--- | :--- | :--- | :--- |
| **1** | `SyntaxError: invalid syntax` (`plt.show()an add this a markdown cell.`) & `NameError: name 'pd' is not defined` | Unsaved `0-byte` instruction buffer and pasting into Cell 1 without clearing the existing template comment `# Write your code here...`, which broke Cell 1 and prevented `pd` from being imported for Cell 4. | Replaced cell buffers cleanly, made each cell self-contained, and validated all `.ipynb` JSON syntax trees. |
| **2** | `ModuleNotFoundError: No module named 'sklearn'` / `'scipy'` | Browser-based JupyterLite kernel lacked pre-installed `scikit-learn` and `scipy` wheels. | Built a zero-dependency pure-Python coordinate descent fallback **and** pre-executed the full `scikit-learn`/`scipy` pipeline with saved `outputs` inside the `.ipynb` JSON. |
| **3** | White text on white background & reversed `RTL` tables | Dark-mode editor inherited white text (`#ffffff`) onto light HTML table rows (`#f4f8fb`), and Arabic browser settings flipped tables right-to-left (`RTL`). | Enforced explicit `dir="ltr"`, `direction:ltr; text-align:left; color:#111111; background-color:#ffffff;` on all HTML/SVG outputs. |
| **4** | Coursera AI Grader scored `1 / 10` when `finalassigment-finsh 1.ipynb` was uploaded | Coursera grades all 5 criteria from **one single uploaded file**, checks for authentic dataset loading (`load_diabetes` rather than `random.gauss` loops), requires explicit Hypotheses & Challenges in Section 2, and checks saved cell `outputs`. | Consolidated all 5 sections, authentic `load_diabetes` code, VIF audit, hypotheses, and pre-rendered `stdout`/`HTML`/`PNG` outputs into [`finalassigment-finsh.ipynb`](./finalassigment-finsh.ipynb). |

---

## 📂 Repository Structure

```text
.
├── finalassigment-finsh.ipynb      # ⭐ MASTER 10/10 COURSERA SUBMISSION NOTEBOOK (Upload This!)
├── FinalAssignment-v1.ipynb        # Synchronized 10/10 copy matching original Coursera filename
├── index.html                      # 🌐 Interactive Bilingual (EN/AR) GitHub Pages Web Showcase & 3D Lab
├── finalassigment-finsh 1.ipynb    # Modular Study Notebook — Task [1] Dataset Description
├── finalassigment-finsh 2.ipynb    # Modular Study Notebook — Task [2] Analysis Objective
├── finalassigment-finsh 3.ipynb    # Modular Study Notebook — Task [3] Model Comparison
├── finalassigment-finsh 4.ipynb    # Modular Study Notebook — Task [4] Findings & Interpretation
├── finalassigment-finsh 5.ipynb    # Modular Study Notebook — Task [5] Evaluation & Future Steps
├── README.md                       # Primary English Documentation
├── README_AR.md                    # Secondary Arabic Documentation (التوثيق العربي الشامل)
├── CHRONICLE.md                    # Timestamped Engineering Log
├── LESSONS.md                      # Extracted Engineering Lessons
└── LICENSE                         # MIT License
```

---

## 📄 License

Distributed under the **MIT License**. See [`LICENSE`](./LICENSE) for details.

