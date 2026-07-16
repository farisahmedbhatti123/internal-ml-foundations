# Day 4 Applied AI Workshop Notebooks

This package supports **Day 4: Classification, Data Preparation, and Unsupervised Learning** of the Applied AI Design Workshop for Faculty. It contains four Jupyter notebooks and three synthetic engineering datasets designed for short, instructor-guided activities.

The notebooks emphasize a transparent applied machine-learning workflow:

> frame the problem → inspect the data → establish a baseline → prepare features → train or discover structure → evaluate → interpret limitations

The examples use manufacturing-style process data, but the methods can be transferred to research, education, laboratory, administrative, and other disciplinary datasets.

---

## Package Contents

```text
Day4_Applied_AI_Notebooks/
├── README.md
├── requirements.txt
├── 01_session1_classification_sklearn.ipynb
├── 02_session2_complete_workflow.ipynb
├── 03_session3_data_preparation_feature_engineering.ipynb
├── 04_session4_unsupervised_learning_discovery.ipynb
├── classification_workshop.csv
├── raw_process_quality_data.csv
└── engineering_operating_regimes.csv
```

Keep the notebooks and CSV files in the same directory. The notebooks use relative file paths and expect the dataset filenames shown above.

---

## Session Guide

### Session 1 — Classification Fundamentals

**Notebook:** `01_session1_classification_sklearn.ipynb`  
**Dataset:** `classification_workshop.csv`

Introduces a minimal binary-classification workflow using process measurements to predict whether a run is defective.

Topics include:

- defining inputs and a binary target;
- creating a stratified train/test split;
- establishing a majority-class baseline;
- fitting logistic regression in a scikit-learn pipeline;
- standardizing numerical features;
- interpreting a confusion matrix, accuracy, precision, recall, and F1 score.

**Participant output:** A concise interpretation of whether the model improves on the baseline and which error type matters most.

---

### Session 2 — Complete Baseline Modeling Workflow

**Notebook:** `02_session2_complete_workflow.ipynb`  
**Dataset:** `classification_workshop.csv`

Extends Session 1 into a complete first-pass applied machine-learning workflow.

Topics include:

- inspecting rows, columns, data types, and target balance;
- visualizing the target and selected features;
- defining the prediction question and unit of observation;
- splitting the data consistently;
- comparing a simple baseline with logistic regression;
- evaluating held-out predictions;
- documenting limitations and recommended next steps.

**Participant output:** A first-pass model card describing the problem, dataset, baseline, model, metrics, limitations, and next action.

---

### Session 3 — Data Preparation and Feature Engineering

**Notebook:** `03_session3_data_preparation_feature_engineering.ipynb`  
**Dataset:** `raw_process_quality_data.csv`

Uses an intentionally imperfect dataset to demonstrate how data preparation affects the credibility of a machine-learning result.

The dataset contains realistic issues such as:

- duplicate records;
- missing values;
- inconsistent category labels;
- numerical values stored as text;
- implausible sensor readings;
- identifier and metadata columns;
- variables that would introduce target leakage.

Topics include:

- conducting a structured data audit;
- correcting data types and category labels;
- handling duplicates and missing values;
- reviewing outliers using domain-informed plausibility limits;
- identifying and removing leakage variables;
- creating domain-informed features;
- applying imputation, scaling, and one-hot encoding;
- using `Pipeline` and `ColumnTransformer`;
- comparing a prepared logistic-regression model with a baseline;
- examining exploratory permutation importance.

**Participant output:** A preprocessing decision record that documents each transformation, its rationale, and the largest remaining data risk.

---

### Session 4 — Unsupervised Learning for Discovery

**Notebook:** `04_session4_unsupervised_learning_discovery.ipynb`  
**Dataset:** `engineering_operating_regimes.csv`

Explores whether unlabeled process measurements contain meaningful operating regimes or unusual observations.

Topics include:

- framing an unsupervised-learning question;
- imputing and standardizing numerical features;
- using principal component analysis for visualization;
- selecting and fitting k-means clusters;
- interpreting inertia and silhouette scores;
- applying hierarchical clustering and reading a dendrogram;
- identifying dense groups and noise with DBSCAN;
- comparing clustering methods;
- profiling clusters in the original engineering units;
- distinguishing mathematical clusters from scientifically validated categories.

The column `known_operating_condition` is reference metadata for workshop interpretation. It should not be used as a clustering input.

**Participant output:** A cluster-interpretation record describing the selected method, possible domain meaning, unusual runs, validation evidence, and limitations.

---

## Dataset Summary

| Dataset | Rows | Primary purpose | Target or reference field |
|---|---:|---|---|
| `classification_workshop.csv` | 220 | Introductory classification and baseline modeling | `defect` |
| `raw_process_quality_data.csv` | 242 | Data cleaning, leakage prevention, and feature engineering | `defect` |
| `engineering_operating_regimes.csv` | 240 | Clustering, PCA, and anomaly discovery | `known_operating_condition` is post-hoc reference metadata |

All datasets are synthetic and intended for instruction. They should not be interpreted as validated industrial process data.


## Required Packages

- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- SciPy
- Jupyter

SciPy is required by Session 4 for hierarchical clustering and dendrogram generation.

---

## Recommended Execution Order

1. Run `01_session1_classification_sklearn.ipynb`.
2. Continue with `02_session2_complete_workflow.ipynb`.
3. Use `03_session3_data_preparation_feature_engineering.ipynb` to examine how preprocessing changes the modeling workflow.
4. Finish with `04_session4_unsupervised_learning_discovery.ipynb`.

Use **Kernel → Restart Kernel and Run All Cells** before distributing or demonstrating a notebook. This verifies that results do not depend on variables left in memory from an earlier run.

---

## Interpretation Guidelines

These notebooks support methodological practice rather than deployment.

- A model that does not outperform a simple baseline is not yet useful.
- Accuracy alone may be misleading when classes are imbalanced.
- Preprocessing must not learn information from the held-out test data.
- Features recorded after an outcome can create data leakage.
- Feature importance does not establish causality.
- A visually distinct cluster is not automatically a scientifically meaningful category.
- Results from synthetic data should not be generalized to real systems without independent validation.



