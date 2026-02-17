# LaLonde Job Training Program — Causal Impact Analysis

This project analyzes the LaLonde / National Supported Work (NSW) job training dataset to estimate whether participating in a job training program (`treat = 1`) improved earnings in 1978 (`re78`) for disadvantaged workers.

## Research Question
**Does the job training program increase 1978 earnings (`re78`) compared to not receiving training?**

## Dataset
The dataset includes:
- **Treatment indicator:** `treat` (1 = participated, 0 = did not)
- **Outcome:** `re78` (earnings in 1978)
- **Covariates:** age, education, race indicators (`black`, `hispan`), marital status (`married`), degree status (`nodegree`), prior earnings (`re74`, `re75`)

## What I Did
1. **Exploratory analysis (EDA)**
   - Summary statistics
   - Distribution plots for key variables

2. **Naive comparison**
   - Difference in means/medians for `re78`
   - Two-sample **t-test** for treated vs control earnings

3. **Causal inference with Propensity Scores**
   - Estimated propensity scores using:
     - Logistic Regression (statsmodels Logit)
     - Decision Tree
     - Random Forest
   - Visualized propensity score distributions (before/after matching)
   - **Nearest-neighbor matching** on propensity scores
   - Computed **ATT** (Average Treatment effect on the Treated)
   - Checked covariate balance with **ASMD/SMD**

4. **Model comparison**
   - ROC curves + AUC for propensity score models
   - Discussion of overfitting (e.g., suspiciously perfect AUC)

## Key Takeaways (High-Level)
- A simple treated vs control comparison does **not** prove causality because groups can differ at baseline.
- Propensity score matching helps create a more comparable control group, but results depend on:
  - balance quality
  - model choice
  - overlap in propensity scores

## Repo Structure
- `notebooks/` — analysis notebook(s)
- `report/` — PDF write-up
- `outputs/figures/` — plots generated from the notebook (optional)

## How to Run
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
