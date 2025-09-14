
# Practical Application 17.1 — Comparing Classifiers (Bank Marketing)

**Notebook:** [Practical_Application_17_1_Bank_Marketing.ipynb](Practical_Application_17_1_Bank_Marketing.ipynb)

## Summary of Findings
This project compares **KNN**, **Logistic Regression**, **Decision Tree**, and **SVM** to predict whether a client will subscribe to a term deposit (`y`) from the UCI Bank Marketing dataset.

- **Business goal:** Improve call efficiency by prioritizing customers with higher subscription propensity.
- **Primary metric:** **ROC AUC** (rank-ordering ability). Secondary: **Recall**, **Precision**, **F1**, **Accuracy**.
- **Result overview:** After cross-validated grid search, the top-performing model (by AUC) is identified in the results table. ROC curves and confusion matrices are provided. Threshold tuning shows the precision/recall trade-off to meet campaign goals.
- **Key drivers:** Logistic coefficients and tree importances highlight features associated with higher conversion likelihood (e.g., contact type, prior outcome, month). Consider treatment of **`duration`** carefully due to potential leakage if used before a call is completed.

## Data & Preparation
- Dataset: `bank-additional-full.csv` (UCI Bank Marketing).
- Steps: Missing value checks, type handling, one-hot encoding for categoricals, standardization for numerics via a `ColumnTransformer` in a pipeline.
- Split: Stratified train/test (80/20).

## Modeling Approach
- Models: KNN, Logistic Regression, Decision Tree, SVM.
- Validation: 5-fold cross-validated **GridSearchCV** on pipelines for fair preprocessing across models.
- Evaluation: AUC comparison + secondary metrics at default and tuned probability thresholds.

## Visualizations
- Seaborn EDA: target distribution, categorical counts, continuous distributions, boxplots, correlation heatmap, and subplots.
- Model diagnostics: ROC curves and confusion matrices.

## Actionable Insights
- **Targeting:** Focus outbound effort on segments with higher predicted probabilities.
- **Operations:** Select a threshold aligned with budgeted call volume and desired recall of positives.
- **Policy:** Monitor fairness across key demographics; adjust targeting rules as needed.

## Next Steps
1. Incorporate **cost-sensitive** thresholding (expected value vs. call costs).
2. Add **calibration** for better probability estimates.
3. Use **time-based splits** to reflect campaign chronology.
4. Track **data drift** and re-tune quarterly.
5. Provide **explanations** to agents (top features per lead).

---

> To run: open the notebook, place `bank-additional-full.csv` alongside it or at `/mnt/data/`, and run all cells.
