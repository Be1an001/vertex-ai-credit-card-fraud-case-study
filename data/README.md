# Data

## Important Note

This public repository does not include the raw CSV dataset or the exact 20,000-row sampled working file used in Vertex AI.

The repository documents the dataset source and working setup, but it is not a dataset mirror and it is not a fully rerunnable data-preparation package. I kept the raw data out of the repository to stay conservative about dataset redistribution rights.

## Original Source

Dataset page:

- [Credit Card Fraud Detection - "Trends and Tactics in Modern Credit Card Fraud"](https://www.kaggle.com/datasets/bhadramohit/credit-card-fraud-detection/data)

Dataset author on Kaggle:

- Bhadra Mohit

## Dataset Description

The Kaggle page describes the dataset as a credit card fraud analysis dataset designed to simulate modern transaction behavior and fraud patterns.

According to the dataset description referenced in this project, the original dataset contains 100,000 simulated transactions and includes fields such as:

- `TransactionID`
- `TransactionDate`
- `Amount`
- `MerchantID`
- `TransactionType`
- `Location`
- `IsFraud`

The dataset supports analysis of fraud behavior, class imbalance, predictive modeling, and prevention-oriented thinking.

## Working Dataset Used in the Assignment

The original report and portfolio documentation describe a working dataset with:

- 20,000 rows
- 7 columns
- 1% fraud ratio
- target column: `IsFraud`

This was a reduced working version used after the first full-data Vertex AI training attempt ran into cloud resource quota limits.

The exact sampled file is not included in this public repository.

## Data Quality Notes

The portfolio PDF reports that the uploaded working sample had no missing values and no duplicate transaction IDs. Because the raw data and exact sample file are not included, those checks cannot be independently verified from this repository alone.

`TransactionID` also appears in the feature attribution screenshot. That should be treated carefully in future work because ID-style fields can create leakage or generalization concerns.

## How to Access the Dataset

To recreate a similar workflow, review the dataset terms and download the data directly from Kaggle:

1. Open the Kaggle dataset page.
2. Review the dataset description and usage terms.
3. Download the dataset directly from Kaggle.
4. Prepare your own sampled working file if needed for your Vertex AI environment.

## Reproducibility Notes

This repository does not include:

- raw CSV data
- the exact 20,000-row sampled CSV
- a sampling script
- a notebook
- a Vertex AI training pipeline
- a model artifact
- the threshold-comparison artifact

The project results should be read through the reports, walkthrough, and Vertex AI screenshots.

## Related Files

- [Main README](../README.md)
- [Project Walkthrough](../docs/project-walkthrough.md)
- [Portfolio PDF](../portfolio/EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf)
- [Original Assignment Report](../reports/EAI6020_Module_4_Assignment_Cheng_Liu.pdf)
