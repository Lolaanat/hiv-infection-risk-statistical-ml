# HIV Infection Risk Analysis: Statistical Testing and Machine Learning

An academic computational biology project combining statistical analysis and machine learning classification to examine associations between selected demographic/behavioral variables and HIV infection status in a Kaggle secondary dataset.

> **Scope note:** The findings in this repository are specific to the analyzed dataset. The analysis is observational and should not be interpreted as establishing causal relationships or as a clinical prediction tool.

## Project Overview

This project analyzes a secondary dataset containing **2,139 observations and 23 variables**. The study focuses on three predictor variables:

- `age`
- `gender`
- `homo`

with `infected` as the target variable.

The analysis combines exploratory data analysis, statistical hypothesis testing, classification models, ROC analysis, and feature-importance analysis.

## Research Questions

1. Is gender statistically associated with HIV infection status in the analyzed dataset?
2. Is the `homo` variable statistically associated with HIV infection status in the analyzed dataset?
3. Does the age distribution differ between infected and non-infected observations?
4. How do different machine learning classifiers perform when predicting `infected` using the selected features?
5. How does feature contribution differ across classification algorithms?

## Methodology

### Statistical Analysis

The notebook applies:

- Exploratory data analysis (EDA)
- Pearson correlation for the numerical variables used in the analysis
- Chi-Square tests for categorical associations
- Mann-Whitney U test for age distribution differences

Reported statistical results include:

| Analysis | Statistic | p-value |
|---|---:|---:|
| Gender vs. Infected | χ² = 4.08 | 0.0434 |
| Homo vs. Infected | χ² = 6.04 | 0.0140 |
| Age vs. Infected | U = 454,583.50 | 0.0069 |

These results indicate statistically detectable associations/differences in this dataset at the 0.05 significance level. They do not, by themselves, establish causation.

### Machine Learning

Five classification algorithms are evaluated:

1. Logistic Regression
2. Support Vector Machine (SVM)
3. Decision Tree
4. Random Forest
5. K-Nearest Neighbors (KNN)

The notebook uses class weighting for Logistic Regression, SVM, Decision Tree, and Random Forest. Model evaluation includes:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- ROC curve / AUC
- Feature importance

## Classification Results

The reported test-set metrics are:

| Model | Accuracy | Precision | Recall | F1 |
|---|---:|---:|---:|---:|
| KNN | 0.73 | 0.29 | 0.11 | 0.16 |
| SVM | 0.60 | 0.26 | 0.38 | 0.31 |
| Logistic Regression | 0.52 | 0.27 | 0.61 | 0.37 |
| Random Forest | 0.51 | 0.22 | 0.45 | 0.30 |
| Decision Tree | 0.50 | 0.24 | 0.55 | 0.34 |

The results illustrate a clear trade-off between metrics: KNN reports the highest accuracy in the project evaluation, while Logistic Regression and Decision Tree report higher recall than KNN. No single model simultaneously maximizes all reported metrics.

The ROC analysis in the project also indicates limited class-discrimination performance, consistent with the restricted feature set.

## Feature Importance

Feature contribution differs across models:

- Logistic Regression: `gender` is the most prominent feature in the notebook's analysis.
- Random Forest: `age` is the most prominent feature.
- Decision Tree: `age` is the most prominent feature.
- KNN: `homo` has the largest reported contribution.
- SVM: `gender` and `homo` are more prominent than `age` in the notebook's feature-importance analysis.

These differences reflect that different algorithms measure or use feature contribution differently. Feature importance should therefore be interpreted in the context of the specific model and methodology used.

## Dataset

The notebook expects a file named:

```text
AIDS_Classification.csv
```

The original project describes the source as the Kaggle **AIDS Virus Infection Prediction Dataset**, with 2,139 records and 23 variables.

The raw CSV is **not included in this ZIP** because it was not among the source files provided for packaging. The notebook therefore serves as the reproducible analysis artifact, while the dataset must be obtained separately from its original source and placed in the project root if the notebook is rerun.

## Repository Structure

```text
hiv-infection-risk-statistical-ml/
├── README.md
├── LICENSE
├── .gitignore
├── notebooks/
│   └── hiv-infection-risk-analysis.ipynb
├── data/
│   └── README.md
└── docs/
    ├── project-report.docx
    ├── final-paper-turnitin.pdf
    └── presentation-link.md
```

## Tools & Libraries

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- SciPy
- Scikit-learn
- Jupyter Notebook

## Reproducibility

Install the required Python packages:

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter
```

Place `AIDS_Classification.csv` in the project root, then open:

```text
notebooks/hiv-infection-risk-analysis.ipynb
```

and run the notebook cells sequentially.

## Academic Context

This project was developed as a Computational Biology / statistics and machine learning academic project at BINUS University.

### Team

- Zahra Annisa Afandi
- Leora Natania Klarise Purba
- M. Aufa Mumtaza Ibadillah
- Satya Darma Padmakumara

## Presentation

The project presentation was prepared in Canva. The original project link is provided in:

`docs/presentation-link.md`

Before publishing the repository publicly, use a Canva **view-only** link rather than an edit link if the presentation is intended to be accessible to portfolio visitors.

## Limitations

Several limitations should be considered:

- The analysis uses a secondary, observational dataset.
- Only three predictors (`age`, `gender`, and `homo`) are used in the project models.
- The reported classification performance is not sufficient to treat the models as clinical diagnostic or screening systems.
- Statistical association does not imply causation.
- Results should not be generalized beyond the analyzed dataset without appropriate external validation.
- Some variables are sensitive and require careful interpretation to avoid stigmatizing conclusions or misuse.

## License

This repository is intended primarily as an academic portfolio artifact. See `LICENSE` for the repository license.
