# Lead Scoring Case Study

## Project Overview
This project develops a lead-conversion scoring model for **X Education** using Python and logistic regression. The goal is to estimate the likelihood that a lead converts, helping a sales team prioritize follow-up efforts.

The analysis covers data cleaning, exploratory analysis, feature preparation, feature selection, model development, probability-threshold tuning, and test-set evaluation.

## Business Problem
Sales teams may have more leads than they can follow up with equally. A conversion-probability score can help organize leads by estimated likelihood of conversion. This notebook builds a baseline model for that purpose; it does not measure an actual increase in sales or conversion rates.

## Tools and Libraries
- Python
- pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn
- statsmodels
- Jupyter Notebook

## Workflow

1. **Load and inspect data** — read `Leads.csv`, inspect columns, data types, summary statistics, and missing values.
2. **Clean the data** — remove columns with more than 3,000 missing values, review fields containing `Select`, and remove several low-information columns.
3. **Explore patterns** — visualize selected variables and compare feature distributions by the `Converted` target.
4. **Prepare features** — encode categorical variables, scale numerical features, and split the data into training and test sets (70/30, `random_state=100`).
5. **Select and refine features** — use Recursive Feature Elimination (RFE) with logistic regression, then review statistical significance and multicollinearity with statsmodels and VIF.
6. **Train and evaluate** — generate conversion probabilities, inspect the ROC curve, and tune the probability cutoff to balance sensitivity and specificity.
7. **Score leads** — use predicted probabilities to classify leads as likely or unlikely to convert at the selected cutoff.

## Reported Model Results

The notebook's saved outputs report the following results:

- **ROC-AUC:** 0.86, as stated in the notebook for the training-set ROC curve.
- **Test-set accuracy:** 78.66% at a probability cutoff of 0.44.
- **Test-set confusion matrix at cutoff 0.44:**

  | | Predicted not converted | Predicted converted |
  |---|---:|---:|
  | Actual not converted | 801 | 195 |
  | Actual converted | 213 | 703 |

At this cutoff, the model correctly classified 801 non-converted leads and 703 converted leads in the saved test-set output. It also made 195 false-positive and 213 false-negative predictions.

**Interpretation:** These are model-evaluation results, not evidence of a real-world conversion-rate increase. The ROC-AUC value is reported for the training ROC analysis in the notebook; it should not be described as test-set ROC-AUC without calculating it on the test set.

## How to Run

1. Download or clone this repository.
2. Obtain the `Leads.csv` dataset used by the notebook and place it in the notebook's working directory. Do not upload the dataset unless its sharing terms permit it.
3. Install the libraries if required:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn statsmodels jupyter
   ```

4. Open `Lead Scoring Case Study.ipynb` in Jupyter Notebook or Google Colab.
5. Run the cells in order and review the results.

## Limitations and Next Steps

- Validate the data-cleaning choices and handling of missing or placeholder values.
- Fit preprocessing steps on training data only to avoid information leakage.
- Calculate ROC-AUC, precision, recall, and a classification report on the held-out test set.
- Compare performance against a simple baseline model.
- Choose a decision threshold based on the business cost of false positives versus false negatives.
- Validate the model on newer leads before using it for operational decisions.
- Track actual sales outcomes before claiming that the model improves conversion rates.

## Repository Structure

```text
lead-scoring-case-study/
├── README.md
└── Lead Scoring Case Study.ipynb
```

## Author
Krishna — Data Analytics Portfolio Project
