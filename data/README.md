# Data

## Important note

This public repository does **not** include the raw CSV dataset.

I used a Kaggle credit card fraud dataset for this project, and my working version in Vertex AI was a **20,000-row sample** that preserved the original class imbalance.

I am not republishing the raw dataset in this repository because I want to stay conservative about dataset redistribution rights.

This repo documents the dataset choice and working setup, but it does **not** include the exact sampled working file or a fully rerunnable data-preparation workflow artifact.

## Original source

Dataset page:

- [Credit Card Fraud Detection - "Trends and Tactics in Modern Credit Card Fraud"](https://www.kaggle.com/datasets/bhadramohit/credit-card-fraud-detection/data)

Dataset author on Kaggle:

- **Bhadra Mohit**

## Short dataset introduction

This dataset is presented as a credit card fraud analysis dataset designed to simulate modern transaction behavior and fraud patterns.

According to the Kaggle dataset page, it focuses on:

- credit card fraud analysis and prevention
- transaction pattern study
- fraud detection modeling
- feature importance analysis
- practical ideas for fraud monitoring and prevention

The dataset description explains that it contains **100,000 simulated transactions** and includes fields such as:

- `TransactionID`
- `TransactionDate`
- `Amount`
- `MerchantID`
- `TransactionType`
- `Location`
- `IsFraud`

The main idea is to support analysis of fraud behavior, class imbalance, predictive modeling, and prevention-oriented thinking.

## How to access the dataset

You can view the dataset page directly here:

- [Open the Kaggle dataset page](https://www.kaggle.com/datasets/bhadramohit/credit-card-fraud-detection/data)

Suggested steps:

1. Open the Kaggle dataset page.
2. Review the dataset description and terms on Kaggle.
3. Download the dataset directly from the source page.
4. If you want to recreate a similar workflow, prepare a smaller sampled version if needed for your own Vertex AI environment.

## Working dataset used in my assignment

My report describes a working dataset with:

- 20,000 rows
- 7 columns
- 1% fraud ratio
- target column: `IsFraud`

This was a reduced working version used after my first full-data training attempt ran into cloud resource quota limits.

The exact sampled file used in the course workflow is not included in this public repo.

## Why the raw file is not included

This repository is intended as a **portfolio documentation repo**, not a dataset mirror.

I chose to provide the source link and usage guidance instead of rehosting the CSV file here.

## Related files

- [Project Walkthrough](../docs/project-walkthrough.md)
- [Portfolio PDF](../portfolio/EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf)
- [Original Assignment Report](../reports/EAI6020_Module_4_Assignment_Cheng_Liu.pdf)
