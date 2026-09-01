# Comparing Bank Marketing Classifiers

This project compares four classification models for predicting whether a bank client will subscribe to a term deposit:

- Logistic Regression
- K-Nearest Neighbors
- Decision Tree
- Support Vector Machine

The full analysis is in [Assignment17_1.ipynb](./Assignment17_1.ipynb).

## Business Goal

The bank wants to identify clients who are most likely to subscribe before making a marketing call. The models are intended to rank a call list so the bank can focus its outreach on the most promising clients.

## Data

The data comes from a Portuguese bank's direct marketing campaigns. It contains 41,188 client-contact records from 17 campaigns.

The analysis excludes `duration` because call length is only known after a call takes place and would leak target information into the model.

## Project Contents

```text
Assignment17_1.ipynb                Main analysis notebook
data/bank-additional-full.csv       Bank marketing dataset
```

## Methods

The notebook:

1. Loads and explores the data with pandas and Seaborn.
2. Checks data types, missing values, and descriptive statistics.
3. Encodes categorical features and creates training and testing sets.
4. Establishes a majority-class baseline.
5. Compares Logistic Regression, KNN, Decision Tree, and SVM models.
6. Uses three-fold cross-validation and ROC AUC for model comparison.
7. Tunes KNN and Decision Tree hyperparameters with `GridSearchCV`.
8. Reviews Logistic Regression coefficients, a confusion matrix, and a classification report.

## Results

- The majority-class baseline accuracy was **88.7%**.
- Logistic Regression had the best test accuracy at **90.2%**.
- Logistic Regression and the tuned Decision Tree were effectively tied on ROC AUC at about **0.81**.
- The tuned Decision Tree improved substantially over the unpruned tree.
- The unpruned Decision Tree overfit the training data.
- SVM was competitive on accuracy but took much longer to train.
- Logistic Regression correctly identified about 22% of actual subscribers at the default threshold, but about 70% of the clients it flagged did subscribe.

## Recommendation

Use Logistic Regression to score and rank the call list. It performs about as well as the tuned Decision Tree, trains quickly, and is easier to explain to a business audience.

The final decision threshold should be selected using the cost of a marketing call and the value of a new subscription. Precision and recall should be reviewed before deploying a model.

## Running the Notebook

Open [Assignment17_1.ipynb](./Assignment17_1.ipynb) in Jupyter Notebook or VS Code and run all cells. The notebook was tested with Python 3.12 and requires:

- pandas
- matplotlib
- seaborn
- scikit-learn
