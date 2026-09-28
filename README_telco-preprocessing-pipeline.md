# Telco Preprocessing Pipeline

An automated data preprocessing pipeline built with Scikit-learn's `Pipeline` and `ColumnTransformer`, applied to the Telco Customer Churn dataset. This project was completed as Task 1 of the Machine Learning Engineer internship at Barakah TechLabs.

**Author** Ibtehaj Bin Zaheer

## Why this project exists

Raw data almost never arrives in a shape a model can use. Missing values, numbers stored as text and categorical columns all need attention before training can start, and doing that work by hand in scattered cells is a common source of data leakage. The goal here was to wrap every cleaning step into one reproducible pipeline that learns its rules from training data and applies them unchanged to anything new.

## What the pipeline does

- Repairs the `TotalCharges` column with a custom transformer. In this dataset it is stored as text, and 11 entries are blank, so they are converted to proper missing values.
- Fills missing numerical values with the median and scales them with `StandardScaler`.
- Fills missing categorical values with the most frequent category and converts them with `OneHotEncoder`, which ignores unseen categories instead of crashing.
- Routes numerical and categorical columns through separate branches using `ColumnTransformer`.

Running the full pipeline on the dataset turns 19 raw feature columns into a clean numerical matrix of 7,043 rows by 46 columns, ready for any model.

## Dataset

Telco Customer Churn, 7,043 customers with demographics, subscribed services, billing details and a churn label. The notebook loads it directly from a public repository, so no manual download is needed.

## Tech stack

Python, Pandas, NumPy, Scikit-learn, Google Colab

## How to run

1. Open `Task1_Preprocessing_Pipeline.ipynb` in Google Colab, or clone the repository and open it in Jupyter.
2. Run all cells from top to bottom.
3. The final cell prints the shape of the transformed data to confirm the pipeline works end to end.

## Repository structure

```
telco-preprocessing-pipeline/
  Task1_Preprocessing_Pipeline.ipynb
  requirements.txt
  README.md
```

## What I learned

Building the custom transformer showed me how far Scikit-learn's pipeline system can be extended when a dataset has its own quirks. It also made the idea of data leakage concrete, since keeping every step inside one pipeline is what stops information from the test set slipping into training.

## Related work

The same pipeline is reused in my churn prediction project, `telco-churn-classifier`.
