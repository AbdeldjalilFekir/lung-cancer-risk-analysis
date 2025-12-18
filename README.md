# Lung Cancer Risk Factors Analysis

A concise, results‑focused analysis of a lung cancer risk factor dataset to discover patient segments, uncover frequent co‑occurring risk patterns, and build a simple predictive model. All work is in `Cancer_Risk_Factors_Analysis.ipynb`.

## Abstract
- Dataset: `cancer patient data sets.csv` (1,000 × 26).
- Target: `Level` ∈ {Low, Medium, High}; distribution ≈ Low 30.3%, Medium 33.2%, High 36.5%.
- Approach: data auditing, EDA, engineered exposure/symptom scores, KMeans clustering with silhouette selection, Apriori association rules, Decision Tree classification.
- Outcome: two clear patient segments (low vs. high exposure/symptom burden); strong association rules; Decision Tree achieved 1.00 test accuracy on an 80/20 stratified split.

## Methods
- Data preparation: type checks, duplicate removal (0 found), range validation; no missing values detected.
- Feature engineering: `Is_Male`, `Total_Exposure_Score`, `Total_Symptom_Score`.
- Feature ranking: mutual information vs. `Level` to highlight strongest predictors.
- Clustering: KMeans on standardized features; k chosen by silhouette; clusters profiled by feature means and visualized with boxplots.
- Association rules: ordinal scales discretized into Low/Med/High; Apriori mined frequent itemsets; rules filtered by support and lift; rules predicting `Level` highlighted.
- Classification: Decision Tree with stratified train/test split; evaluation via accuracy, report, and confusion matrix; feature importances reported.

## Results (current run)
- Signals: highest MI in `Total_Exposure_Score`, `Total_Symptom_Score`, plus risks such as `Passive_Smoker`.
- Clustering: k=2 with silhouette ≈ 0.332; one segment shows markedly higher exposure and symptom totals (slightly older), the other lower on both.
- Association rules: multiple high‑lift patterns among discretized risks/symptoms; a subset directly predicts `Level`.
- Classification: Decision Tree accuracy = 1.00 on test; top importances include `Passive_Smoker`, `Wheezing`, `Obesity`, `Snoring`, `Dry_Cough`.

## Reproduce (Windows PowerShell)
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install pandas numpy scikit-learn matplotlib seaborn mlxtend


## Repository
- `Cancer_Risk_Factors_Analysis.ipynb` — analysis notebook.
- `cancer patient data sets.csv` — dataset.
- `README.md` — this document.

## Notes
- Association rules use discretized ordinal scales to keep rule consequents/antecedents human‑interpretable.
- The Decision Tree baseline is intentionally simple and interpretable.

