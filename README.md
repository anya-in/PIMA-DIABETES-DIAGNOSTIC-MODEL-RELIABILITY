# Diagnostic Model Reliability: Evaluating Consistency in Predictive Healthcare Models

This project assesses the **test-retest reliability**, **diagnostic agreement**, and **threshold performance** of logistic and boosted models on the Pima Indians Diabetes Dataset. It was completed for the **CS675: Introduction to Data Science** course at Pace University.

---

## Objective

To measure how reliably and consistently a diagnostic model can predict diabetes over repeated trials using metrics like:
- ROC-AUC
- Intraclass Correlation Coefficient (ICC)
- Bland-Altman analysis
- Optimal classification thresholds

---

## Dataset

**Pima Indians Diabetes Dataset**  
Source: [UCI Machine Learning Repository](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)  
- 768 records
- 8 medical predictor variables
- Binary outcome (`Outcome`: 1 = diabetic, 0 = non-diabetic)

---

## Tools & Libraries

- `pandas`, `numpy`: Data manipulation  
- `scikit-learn`: Modeling & evaluation  
- `matplotlib`, `seaborn`: Visualization  
- `pingouin`: ICC computation  
- `statsmodels`: Bland-Altman plotting  

---

## Steps Followed

### Step 1: Load & Explore Data
- Checked for missing values and data balance.
- Inspected variable distributions using histograms and boxplots.

### Step 2: Preprocess the Dataset
- Replaced zeroes in critical columns (`Glucose`, `BloodPressure`, etc.) with NaNs.
- Imputed missing values using median strategy.

### Step 3: Split Dataset
- Split into 80% training and 20% test sets.
- Stratified to preserve class balance.

### Step 4: Build Baseline Logistic Regression
- Trained and evaluated using ROC-AUC and confusion matrix.

### Step 5: Apply Bootstrapping (Boosted Model)
- Repeated logistic regression training on multiple bootstrapped samples.
- Averaged predictions to reduce variance and test robustness.

### Step 6: Compute ROC Curve & AUC
- Calculated and plotted ROC curves.
- Identified AUC scores for both models.

### Step 7: Determine Optimal Thresholds
- Used **Youden’s J statistic** to choose optimal cutoff points for classification.

### Step 8: Recalculate Metrics at Optimal Thresholds
- Computed updated confusion matrix and classification report.

### Step 9: Test-Retest Reliability using ICC
- Ran 3 repeated simulations on test data.
- Measured **Intraclass Correlation Coefficient (ICC)** for predicted probabilities.

### Step 10: Bland-Altman Analysis
- Plotted Bland-Altman graph to analyze agreement between baseline and boosted model predictions.

---

##  Summary of Results

| Metric                      | Logistic Model | Boosted Model |
|----------------------------|----------------|----------------|
| AUC                        | ~0.82          | ~0.82          |
| ICC (3-day repeat test)    | > 0.98         | > 0.98         |
| Accuracy (Optimal Threshold) | 74%            | 71%            |
| Recall (for class 1)       | 89%            | 96%            |

- Logistic regression had better precision; boosted model had higher recall.
- ICC and Bland-Altman plots confirm **high consistency** in predictions.
- Framework supports **reproducible diagnostics** essential in clinical models.

---

## Skills Demonstrated

- Diagnostic reliability & agreement analysis  
- Threshold tuning via Youden’s J  
- Statistical reproducibility using Python  
- Data visualization for interpretability  
- ROC, ICC, Bland-Altman expertise

---

## Future Scope

This framework can be extended for:
- More granular longitudinal healthcare datasets
- Comparing different classification algorithms
- Integrating probabilistic confidence estimates
- Deploying reproducible diagnostics in real clinical systems

---

##  Course Info

- **Course:** CS675 - Introduction to Data Science  
- **Institution:** Pace University  
- **Instructor:** Dr. Begimai Zhumakova  
- **Term:** Spring 2025  

---

## Contributing

If you'd like to add new metrics, test other datasets, or improve the modeling framework, feel free to fork and submit a PR!


