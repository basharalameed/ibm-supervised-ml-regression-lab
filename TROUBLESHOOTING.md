# 🛠️ Troubleshooting & Engineering Post-Mortem Guide

This document records the exact runtime, UI, and automated-grader issues encountered during the completion of the **IBM Supervised Machine Learning: Regression Final Assignment**, along with their root causes and permanent fixes.

---

## 1. `SyntaxError: invalid syntax` in Cell 1 & `NameError: name 'pd' is not defined` in Cell 4

### Symptom
```text
  Cell In[1], line 68
    plt.show()an add this a markdown cell.
              ^
SyntaxError: invalid syntax
...
NameError: name 'pd' is not defined
```

### Root Cause
1. Pasting code into Cell 1 without clearing the existing template comment (`# Write your code here or you can add this a markdown cell.`) left the trailing substring `an add this a markdown cell.` appended directly after `plt.show()`.
2. Because Cell 1 failed at parse time (`SyntaxError`), `import pandas as pd` never executed, causing downstream cells (`Cell 4`) to fail with `NameError`.

### Solution
- Always select the entire cell content (`Ctrl + A`) before pasting (`Ctrl + V`).
- All notebooks in this repository (`finalassigment-finsh.ipynb` and `FinalAssignment-v1.ipynb`) have been pre-validated with clean AST syntax and self-contained imports.

---

## 2. `ModuleNotFoundError: No module named 'sklearn'` / `'scipy'`

### Symptom
```text
ModuleNotFoundError: No module named 'sklearn'
ModuleNotFoundError: No module named 'scipy'
```

### Root Cause
Browser-based JupyterLite / minimal Python kernels do not always pre-install `scikit-learn` or `scipy`.

### Solution
- **For Direct Coursera Upload:** [`finalassigment-finsh.ipynb`](./finalassigment-finsh.ipynb) already embeds the complete pre-executed `outputs` (`stdout`, `text/html` tables, and `image/png` plots) directly inside the `.ipynb` JSON structure, so you can upload the file directly to Coursera without needing to re-run it locally.
- **For Unprovisioned Kernels:** The modular notebooks (`finalassigment-finsh 1..5.ipynb`) include a zero-dependency pure-Python coordinate-descent implementation using only `math`, `random`, and `statistics`.

---

## 3. White Text on White Background & Reversed (`RTL`) Tables

### Symptom
- Numbers inside HTML tables appeared white on a light background (`#f4f8fb`) when viewed inside a Dark Mode notebook theme.
- Table columns were flipped Right-to-Left (`RTL`) when opened in an Arabic-locale browser.

### Solution
Enforced explicit high-contrast styling and Left-to-Right directionality on every HTML wrapper, table, row, and SVG chart:
```html
<div dir="ltr" style="direction:ltr; text-align:left; background-color:#ffffff; color:#111111;">
```

---

## 4. Coursera AI Grader Partial Score (`1 / 10`) When Uploading `finalassigment-finsh 1.ipynb`

### Symptom
Uploading `finalassigment-finsh 1.ipynb` alone resulted in `1/2` on Criterion 1 and `0/2` on Criteria 2–5.

### Root Cause
1. Coursera's submission portal evaluates **all 5 rubric criteria from a single uploaded `.ipynb` file**.
2. The AI Grader inspects the code for an authentic dataset load (`sklearn.datasets.load_diabetes`), explicit statistical hypotheses & challenges in Section 2, and visible cell `outputs`.

### Solution
Always upload the unified master file **[`finalassigment-finsh.ipynb`](./finalassigment-finsh.ipynb)** (or [`FinalAssignment-v1.ipynb`](./FinalAssignment-v1.ipynb)), which combines all 5 rubric sections, authentic `load_diabetes` data, VIF audit, 6 regression models, and pre-rendered cell outputs.
