# Data

## Important note

This public repository does **not** include the raw CSV dataset.

I used a Kaggle credit card fraud dataset for this project, and my working version in Vertex AI was a **20,000-row sample** that preserved the original class imbalance.

I am not republishing the raw dataset in this repository because I want to stay conservative about dataset redistribution rights.

## Original source

Kaggle dataset used in the project:

**Credit Card Fraud Detection**  
Author: **Bhadra Mohit**  
Source: Kaggle dataset page

## How to access the dataset

1. Go to the Kaggle dataset page for the project source.
2. Review the dataset terms and license on Kaggle.
3. Download the dataset directly from Kaggle to your local machine.
4. If you want to recreate the workflow, prepare a sampled version suitable for your own Vertex AI environment.

## Working dataset used in my assignment

My report describes a working dataset with:

- 20,000 rows
- 7 columns
- 1% fraud ratio
- target column: `IsFraud`

## Why the raw file is not included

This repository is intended as a **portfolio documentation repo**, not a dataset mirror.

I chose to provide the source and usage guidance instead of rehosting the CSV file here.