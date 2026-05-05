# Project Walkthrough

## Project Overview

This project was my Module 4 assignment for **EAI6020: AI Systems Technology**. I used **Google Cloud Vertex AI AutoML** to build and evaluate a credit card fraud detection model.

The goal was to study how a cloud AutoML workflow can support an imbalanced classification problem. This repository is a cleaned portfolio version of that work. It documents the business problem, dataset scope, model evaluation, threshold decision, feature attribution, and limitations.

It is not a fully rerunnable end-to-end build package. The raw data, exact sampled file, model artifact, and threshold-comparison artifact are not included.

## Business Problem

Credit card fraud detection is a rare-event classification problem. Most transactions are legitimate, but missed fraud can create direct financial loss. False alarms also matter because they can create customer friction and support costs.

For this assignment, I used a simple cost scenario:

- False negative cost = $500
- False positive cost = $50

This made threshold selection part of the analysis. The model needed to be evaluated as a decision-support tool, not only as a technical score.

## Dataset and Scope

The original source was a public Kaggle credit card fraud dataset. The repository documentation describes the original dataset as 100,000 simulated transactions.

For the Vertex AI workflow, I used a documented 20,000-row stratified working sample that preserved the original 1% fraud ratio. The exact sampled CSV is not included in this repository.

Main fields documented for the project:

- `TransactionID`
- `TransactionDate`
- `Amount`
- `MerchantID`
- `TransactionType`
- `Location`
- `IsFraud`

The target column was `IsFraud`.

See the full dataset note here:

- [Dataset Note](../data/README.md)

## Methodology

The project followed this workflow:

1. Selected a public fraud detection dataset.
2. Defined a simple business-cost scenario.
3. Uploaded and prepared data in Vertex AI.
4. Attempted AutoML training on the full dataset.
5. Adjusted to a 20,000-row stratified sample after a `QUOTA_FOR_INSTANCES` error.
6. Trained an AutoML tabular classification model.
7. Used `IsFraud` as the target column.
8. Used `AUC PR` as the optimization objective.
9. Reviewed PR AUC, ROC AUC, F1, confusion matrix behavior, and feature attribution.
10. Compared threshold behavior and documented a selected threshold.
11. Summarized the business trade-off and project limitations.

This project is more about evaluation judgment and business-aware threshold reasoning than writing custom model code from scratch.

## Why Precision-Recall Mattered

Simple accuracy is not enough for this problem because the fraud class is rare. A model could look good overall while still missing the cases that matter most.

That is why the evaluation focused on:

- Precision-Recall curve
- ROC curve
- macro-average F1
- confusion matrix behavior
- threshold trade-offs

The PR curve was especially important because it focuses more directly on the trade-off between precision and recall for the minority fraud class.

## Vertex AI Training Setup

The successful training setup documented in the project used:

- Target column: `IsFraud`
- Optimization objective: `AUC PR`
- Budget: `1 node hour`
- Working sample: 20,000 rows with the documented 1% fraud ratio

The first training attempt used the full dataset but failed because of a cloud quota issue. This was useful because it showed that cloud AI work can be affected by resource limits, not only modeling choices.

## Evaluation Details

The main reported metrics were:

- PR AUC = 0.989
- ROC AUC = 0.991
- Macro-average F1 at threshold 0.5 = about 0.498

### Evaluation Screenshot

[![Evaluation details](../assets/images/vertex-ai-evaluation-details.png)](../assets/images/vertex-ai-evaluation-details.png)

This screenshot supports the model evaluation summary at the default confidence threshold. It should be read together with the report and portfolio PDF, because the repository does not include the full model artifact or training records.

## PR Curve and ROC Curve

[![PR and ROC curves](../assets/images/vertex-ai-pr-roc-curves.png)](../assets/images/vertex-ai-pr-roc-curves.png)

The PR and ROC views show the model's ranking performance in Vertex AI. For the fraud use case, the PR curve is more useful than accuracy because it focuses on minority-class detection.

## Confusion Matrix

[![Confusion matrix](../assets/images/vertex-ai-confusion-matrix.png)](../assets/images/vertex-ai-confusion-matrix.png)

The confusion matrix helped show why a default threshold should not be accepted without review. It is useful evidence for the threshold discussion, but it should not be interpreted as the final selected operating policy.

## Threshold Decision

The default threshold of 0.5 was not treated as suitable for the fraud-screening decision. The project documents a selected threshold of 0.75 as a better balance point.

At this threshold, the report documents approximately:

- Precision = 96%
- Recall = 82%

This threshold should be interpreted carefully. It is a documented case-study recommendation based on the original report and Vertex AI workflow, not an independently reproducible threshold policy from this repository alone. The exact threshold-comparison artifact is not included.

## Feature Attribution

[![Feature importance](../assets/images/vertex-ai-feature-importance.png)](../assets/images/vertex-ai-feature-importance.png)

The feature attribution view showed the strongest visible model signals as:

- `Amount`
- `TransactionType`
- `TransactionID`
- `MerchantID`
- `Location`
- `TransactionDate`

Feature attribution is useful for reviewing model reliance, but it is not causal evidence. `TransactionID` appearing as an important feature should be treated carefully because ID-style fields can create leakage or generalization concerns.

## Final Takeaway

This project is best understood as a cloud AutoML case study about evaluating an imbalanced fraud-classification model. The main value is the connection between model evaluation and business threshold reasoning.

The project shows:

- how Vertex AI AutoML can support a tabular classification workflow
- why PR-focused evaluation matters for rare-event problems
- why a default threshold may not match the business use case
- how feature attribution can support model review
- why documentation should be clear about limits and evidence

## Limitations

- The raw dataset is not included.
- The exact sampled working file is not included.
- No custom model code, notebook, or runnable training pipeline is included.
- The exact threshold-comparison artifact is not included.
- The selected threshold is documented from the course workflow, not independently reproducible from this repo alone.
- This is not a production fraud system or deployed app.
- The cost assumptions are scenario values, not measured business savings.
- Feature attribution should be interpreted carefully, especially for `TransactionID`.

## Related Files

- [Main README](../README.md)
- [Course Context](course-context.md)
- [Dataset Note](../data/README.md)
- [Asset Guide](../assets/README.md)
- [Portfolio PDF](../portfolio/EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf)
- [Original Assignment Report](../reports/EAI6020_Module_4_Assignment_Cheng_Liu.pdf)
