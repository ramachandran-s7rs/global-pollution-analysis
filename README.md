# Global Pollution Analysis and Energy Recovery

Classifying countries into pollution severity categories (**Low / Medium / High**) using Multinomial Naive Bayes, K-Nearest Neighbors and a Decision Tree, and exploring how pollution relates to energy recovery.

## Project Workflow

**Phase 1 – Data Preprocessing**
- Load and clean the dataset (duplicates, missing values)
- Median imputation and IQR-based outlier capping
- Feature scaling (StandardScaler; MinMaxScaler for Naive Bayes)
- `LabelEncoder` for Country and Year
- Feature engineering: energy consumption per capita and year-over-year CO2 change per country

**Phase 2 – Classification**
- **Multinomial Naive Bayes** – tuned smoothing (`alpha`)
- **K-Nearest Neighbors** – tuned `K` (1–30), distance weighting and metric
- **Decision Tree** – tuned `max_depth`, `min_samples_split`, `min_samples_leaf`, criterion
- All models use a stratified 80/20 split and 5-fold stratified cross-validation (on the training set only)
- Metrics: Accuracy, Precision, Recall, F1-score, Confusion Matrix

**Phase 3 – Reporting and Insights**
- Model comparison with confusion matrices and classification reports
- Feature importance, most/least polluted countries, and pollution vs. energy recovery
- Policy recommendations

## How the Severity Label Is Built

The dataset has no ready-made severity column, so a composite pollution score is created from the **air, water and soil pollution indices** (average of their z-scores) and split into three equal-sized groups: Low, Medium and High.

Because the label is computed from those three indices, they are **excluded from the model inputs by default** to prevent data leakage. This can be changed with `INCLUDE_INDICES_IN_FEATURES` at the top of the notebook. Imputation, outlier capping and scaling are fitted on training data only.

## Results

*(Fill in after running the notebook on the real dataset.)*

| Model | Accuracy | Precision (macro) | Recall (macro) | F1 (macro) |
|---|---|---|---|---|
| Naive Bayes | – | – | – | – |
| KNN | – | – | – | – |
| Decision Tree | – | – | – | – |

Majority-class baseline accuracy: –

## Limitations

- The severity label is derived from the dataset's own pollution indices rather than an official classification, so results depend on how it is defined.
- The dataset is small, so test-set scores can vary noticeably between splits.
- Findings on energy recovery and policy are correlations, not proof of cause and effect.

## Dataset

`Global_Pollution_Analysis.csv` should be placed in the project root next to the notebook.
Download link: https://drive.google.com/file/d/1AEMcCWzJ24fc26Q761SEOa1sOsZiJBC5/view?usp=sharing
