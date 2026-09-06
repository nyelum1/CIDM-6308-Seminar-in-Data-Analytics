# Decision Trees for Credit Card Fraud Detection

## Explanation of the Tutorial Notebook

This document explains the structure, purpose, and key takeaways of the `Decision_tree_tutorial(1).ipynb` notebook, which walks through building and interpreting a decision tree model for detecting fraudulent credit card transactions.

---

## 1. Purpose

The notebook is a complete, self-contained tutorial that teaches how to:

- Load and explore a credit card transaction dataset
- Prepare data for a decision tree classifier
- Train a decision tree to distinguish fraudulent from legitimate transactions
- Visualize and interpret the tree's decision rules
- Evaluate model performance using metrics suited to imbalanced classification problems
- Translate model results into business/regulatory insights

---

## 2. Dataset

- **Source:** A 10,000-row subset of the well-known ULB/Worldline European credit card transactions dataset (original has 284,807 rows), compiled to be easier to use in Google Colab.
- **Target variable:** `Class` — `1` = fraud, `0` = legitimate.
- **Features:** 30 total — `Time`, `Amount`, and 28 anonymized PCA components (`V1`–`V28`) that preserve statistical relationships while protecting cardholder privacy.
- **Class imbalance:** Only 4.92% of transactions are fraudulent (492 of 10,000), which is realistic for fraud detection but requires special handling (e.g., `class_weight='balanced'`, stratified splitting).

> **Note:** The notebook's data-loading cell currently points to a `telecom_churn_data.csv` URL rather than the credit card fraud CSV described in the text. If you run the notebook as-is, update that URL to the actual fraud dataset (`cc_transactions_10000.csv` from the source referenced in the markdown) so the `Class`, `V1`–`V28`, `Time`, and `Amount` columns exist.

---

## 3. Notebook Walkthrough

### Section 1–2: Introduction

Explains what a decision tree is (a flowchart of yes/no questions ending in a class prediction) and why it's well-suited for fraud detection: interpretability, no need for feature scaling/encoding, ability to capture non-linear patterns, and built-in feature importance.

### Section 3: Install & Import Packages

Installs and imports `scikit-learn`, `pandas`, `numpy`, `matplotlib`, `seaborn`, `graphviz`, and `tabulate` — the core libraries for data handling, modeling, and visualization.

### Section 4: Load and Explore the Dataset

- Loads the CSV into a DataFrame.
- Prints dataset shape, feature count, and target variable.
- Displays the first 5 rows.
- Checks data types (all numeric — ideal for decision trees), missing values (none), and the class distribution (highlighting the 95%/5% imbalance).
- Builds a summary table (using `tabulate`) consolidating transaction counts, fraud/non-fraud counts, and missing values.

### Section 5: Feature Analysis

- Separates features (`X`) from the target (`y`).
- Computes correlation of each feature with `Class`, identifying `V14`, `V12`, and `V17` as the strongest fraud indicators.
- Performs an 80/20 **stratified** train/test split so both sets preserve the ~5% fraud rate, ensuring fair evaluation.

### Section 6: Building the Decision Tree

Trains a `DecisionTreeClassifier` with:

- `criterion='gini'` — splitting quality measure
- `max_depth=3` — keeps the tree shallow and interpretable
- `class_weight='balanced'` — compensates for class imbalance
- `min_samples_split=10`, `min_samples_leaf=5` — guards against overfitting to noise
- `random_state=42` — reproducibility

Reports the resulting tree depth and number of leaves.

### Section 7: Decision Tree Visualization

Uses `plot_tree` and `export_text` to render the tree graphically and as text rules (e.g., "If `V14 <= -1.81`..."), showing exactly how the model reaches each fraud/non-fraud prediction.

### Section 8: Feature Importance and Model Performance

- Ranks features by importance — `V14` dominates (~86% of splitting power), with `V4`, `V8`, `V10`, `V12`, `V20` contributing smaller amounts; most features are unused.
- Evaluates the model on the test set with accuracy, a classification report (precision/recall/F1 per class), and a confusion matrix.
- Key results: ~96% overall accuracy, 92% fraud recall (catches most fraud), 57% fraud precision (moderate false-alarm rate) — a reasonable trade-off for a simple, transparent model.

### Section 9: Performance Visualization

Combines four plots into one figure: feature importance bar chart, confusion matrix heatmap, precision/recall bar chart, and predicted class distribution pie chart.

### Section 10–11: Results Interpretation & Conclusion

Summarizes findings in business terms:

- The model automatically identified the most predictive features (especially `V14`) without manual feature engineering.
- The shallow, rule-based structure is fully explainable — important for regulatory/compliance needs in financial services.
- Strengths: interpretability, speed, automatic feature selection.
- Limitations: a single tree may miss complex fraud patterns, risk of overfitting with deeper trees, false positives still require human review.
- Suggests this model serves as a strong, explainable baseline that could be extended with ensemble methods (e.g., random forests, gradient boosting) for higher performance.

---

## 4. Key Takeaways

1. **Decision trees offer transparency** — every prediction can be traced through explicit if-then rules, which matters for auditability in fraud detection.
2. **Class imbalance must be addressed explicitly** — via stratified splitting and `class_weight='balanced'`, otherwise the model would default to always predicting "non-fraud."
3. **Feature importance reveals dominant signals** — a small number of PCA components (especially `V14`) drive nearly all splitting decisions.
4. **Precision/recall trade-offs matter more than raw accuracy** in imbalanced problems like fraud detection, since accuracy alone can be misleading (a model predicting "no fraud" for everything would still be ~95% accurate).
5. **Shallow trees (max_depth=3) balance interpretability and performance**, though deeper trees or ensembles could improve accuracy at the cost of some explainability.
