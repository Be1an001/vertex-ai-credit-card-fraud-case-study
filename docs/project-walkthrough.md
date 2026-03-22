# Project Walkthrough

## 1. Project Overview

This project was my Module 4 assignment for **EAI6020: AI Systems Technology**.

I used **Google Cloud Vertex AI AutoML** to build and evaluate a credit card fraud detection model. The goal was to study how a cloud AI tool can support a real business problem, especially when the data is highly imbalanced.

This public repo version is a cleaner portfolio version. It focuses on the problem, the workflow, the evaluation logic, and the final threshold decision.

## 2. Business Problem

Credit card fraud detection is a high-risk classification problem.

The key challenge is that fraudulent cases are rare, but missing them is expensive. At the same time, flagging too many valid transactions can hurt customer trust.

To make the project more practical, I used a simple business scenario:

- False Negative cost = $500
- False Positive cost = $50

This made threshold selection part of the project, not just model training.

## 3. Dataset

The original source was a public Kaggle dataset about credit card fraud detection.

For my Vertex AI workflow, I ultimately used a **20,000-row sample** that preserved the **1% fraud ratio** from the larger source.

Main fields included:

- `TransactionID`
- `TransactionDate`
- `Amount`
- `MerchantID`
- `TransactionType`
- `Location`
- `IsFraud`

## 4. Why Precision-Recall mattered

This was an imbalanced classification problem, so simple accuracy was not enough.

A model can appear strong overall while still performing poorly on the minority fraud class. That is why I focused on:

- Precision-Recall curve
- ROC curve
- confusion matrix
- threshold behavior

## 5. Workflow

My project flow looked like this:

1. Select a public fraud detection dataset
2. Define a simple business cost scenario
3. Upload and prepare data in Vertex AI
4. Train an AutoML tabular classification model
5. Review PR AUC, ROC AUC, F1, confusion matrix, and feature importance
6. Compare threshold trade-offs
7. Choose a better business threshold
8. Summarize lessons learned

## 6. Challenge during training

My first training attempt used the full dataset, but it failed because of a **QUOTA_FOR_INSTANCES** error.

To solve this, I created a smaller **20,000-row stratified sample** while keeping the original fraud ratio. This helped me complete the training and also taught me that AI projects involve cloud resource planning, not only model logic.

## 7. Model setup

My successful training setup used:

- **Target column:** `IsFraud`
- **Optimization objective:** `AUC PR`
- **Budget:** `1 node hour`

This setup was chosen because the main goal was to improve model usefulness for rare fraud cases.

## 8. Evaluation highlights

The main reported results were:

- **PR AUC = 0.989**
- **ROC AUC = 0.991**
- **Macro-average F1 at threshold 0.5 = about 0.498**

This taught me an important lesson: good overall ranking metrics do not automatically mean the default decision threshold is good enough for the actual business use case.

## 9. Threshold decision

The default threshold of **0.5** was not suitable.

I compared different threshold behaviors and selected **0.75** as a better balance point.

At this threshold, the model achieved approximately:

- **Precision = 96%**
- **Recall = 82%**

I chose this threshold because it gave a better balance between:

- catching fraud
- avoiding too many false alarms
- protecting customer experience

## 10. Feature importance note

The feature importance view showed that the strongest model signals included:

- Amount
- TransactionType
- TransactionID
- MerchantID
- Location
- TransactionDate

This part was useful because it made the project more interpretable and more aligned with explainable AI thinking.

## 11. Final takeaway

This project is not my best example of model coding, but it is one of my better examples of **AI systems thinking**.

It shows that I can:

- connect model evaluation with business trade-offs
- use cloud AI tools practically
- think carefully about rare-event classification
- explain results in a way that non-technical stakeholders can understand

That is why I believe this project is worth keeping in my portfolio.