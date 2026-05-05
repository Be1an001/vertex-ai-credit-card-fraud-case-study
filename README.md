# Vertex AI Credit Card Fraud Case Study

## Short Summary

This project is an individual course-based portfolio case study about credit card fraud detection using Google Cloud Vertex AI AutoML. The focus is not custom model code. The focus is business framing, imbalanced classification evaluation, threshold selection, and feature attribution in a cloud AutoML workflow.

The repository is best understood as a documentation package for the completed workflow. It includes reports, notes, and Vertex AI screenshots, but it does not include the raw dataset, exact sampled working file, model artifact, training script, or threshold-comparison artifact.

## Project Type / Status / Tools

| Item | Description |
|---|---|
| Project type | Applied machine learning decision-support case study |
| Course context | EAI6020: AI Systems Technology, Northeastern University |
| Status | Portfolio documentation package, not a fully rerunnable pipeline |
| Main tool | Google Cloud Vertex AI AutoML |
| Supporting source | Public Kaggle credit card fraud dataset |
| Main focus | PR/ROC evaluation, threshold tuning, feature attribution, and business-cost framing |

Evidence:

- [Project Walkthrough](docs/project-walkthrough.md)
- [Course Context](docs/course-context.md)
- [Portfolio PDF](portfolio/EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf)
- [Original Assignment Report](reports/EAI6020_Module_4_Assignment_Cheng_Liu.pdf)

## Business Problem

Credit card fraud detection is an imbalanced classification problem. Fraud cases are rare, but missing them can be expensive. At the same time, flagging too many valid transactions can create customer friction and support costs.

This project treats the model output as a decision-support problem. The main question is not only whether the model can rank fraud risk, but also what threshold gives a reasonable balance between missed fraud and false alarms in a case-study setting.

The project used a simple cost scenario:

- False negative cost: $500
- False positive cost: $50

These values are scenario assumptions from the assignment. They should not be read as measured business impact or real bank operating costs.

## Project Objective

The goal was to use Vertex AI AutoML to train and evaluate a fraud-classification model, then interpret the model results through a business-aware threshold decision.

The analysis focused on:

- setting up a tabular classification task in Vertex AI AutoML
- using `IsFraud` as the target column
- selecting `AUC PR` as the optimization objective
- reviewing PR AUC, ROC AUC, F1, and the confusion matrix
- comparing threshold behavior
- reviewing Vertex AI feature attribution
- explaining the false-positive / false-negative trade-off clearly

## Dataset and Scope

The repository documents a public Kaggle credit card fraud dataset. According to the dataset notes, the original dataset contains 100,000 simulated transactions.

For the Vertex AI workflow, the project used a documented 20,000-row stratified working sample that preserved the original 1% fraud ratio. The working sample is described as having 7 columns:

- `TransactionID`
- `TransactionDate`
- `Amount`
- `MerchantID`
- `TransactionType`
- `Location`
- `IsFraud`

The exact raw dataset and exact sampled CSV are not included in this repository. Reported data quality notes, such as no missing values or no duplicate transaction IDs in the uploaded sample, come from the portfolio documentation and cannot be independently verified from this repository alone.

Dataset details are documented in [data/README.md](data/README.md).

## My Role / Contribution

This was an individual course-based project. My work focused on:

- selecting a fraud-detection dataset
- framing the business-cost trade-off
- adapting the workflow after a Vertex AI quota issue
- using a 20,000-row stratified working sample
- training and evaluating the AutoML model in Vertex AI
- reviewing PR/ROC curves, confusion matrix behavior, and feature attribution
- documenting the final threshold decision and limitations

The model training was done through the Vertex AI interface. This repository should not be interpreted as a custom model-code project.

## Methodology

1. Selected a public credit card fraud dataset.
2. Defined a simple false-negative and false-positive cost scenario.
3. Attempted Vertex AI AutoML training on the full dataset.
4. Adjusted to a smaller 20,000-row stratified working sample after a quota issue.
5. Trained a Vertex AI AutoML tabular classification model.
6. Used `IsFraud` as the target and `AUC PR` as the optimization objective.
7. Reviewed evaluation metrics, PR/ROC curves, and confusion matrix behavior.
8. Compared threshold trade-offs and selected a documented threshold of 0.75.
9. Reviewed feature attribution to understand which fields the model relied on.
10. Documented limitations and future improvements.

## Key Findings

According to the report, portfolio PDF, and Vertex AI screenshots:

- The working sample preserved a rare fraud class of about 1%.
- The reported PR AUC was 0.989.
- The reported ROC AUC was 0.991.
- The default confidence threshold was 0.5.
- The reported macro-average F1 at the default threshold was about 0.498.
- The selected threshold was documented as 0.75.
- The selected threshold was documented as approximately 96% precision and 82% recall.
- Feature attribution showed `Amount` and `TransactionType` as the strongest visible signals.
- `TransactionID` also appeared in the feature importance view, which should be treated carefully because ID-style fields can create leakage or generalization concerns.

The threshold result should be read as a documented case-study recommendation, not as an independently reproducible operating policy from this repository alone.

## Visual Highlights

| Visual | What it supports |
|---|---|
| [Evaluation details](assets/images/vertex-ai-evaluation-details.png) | Reported Vertex AI metrics at the default confidence threshold. |
| [PR and ROC curves](assets/images/vertex-ai-pr-roc-curves.png) | Model evaluation view for an imbalanced fraud-classification case. |
| [Confusion matrix](assets/images/vertex-ai-confusion-matrix.png) | Default-threshold behavior that helped motivate threshold review. |
| [Feature importance](assets/images/vertex-ai-feature-importance.png) | Vertex AI feature attribution, including the need to treat `TransactionID` carefully. |

More context for the screenshots is available in [assets/README.md](assets/README.md).

## Model Evaluation Note

The project documents strong ranking metrics, but the default threshold was not treated as automatically suitable. This is important because imbalanced fraud problems can look strong on some summary metrics while still needing careful threshold review.

The selected threshold should be interpreted with caution because the raw data, exact sampled file, model artifact, and threshold-comparison artifact are not included. The available evidence is the original report, portfolio PDF, and Vertex AI screenshots.

## Repository Structure

```text
.
|-- README.md
|-- .gitattributes
|-- .gitignore
|-- reports/
|   |-- README.md
|   `-- EAI6020_Module_4_Assignment_Cheng_Liu.pdf
|-- portfolio/
|   |-- README.md
|   `-- EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf
|-- assets/
|   |-- README.md
|   `-- images/
|       |-- vertex-ai-evaluation-details.png
|       |-- vertex-ai-pr-roc-curves.png
|       |-- vertex-ai-confusion-matrix.png
|       `-- vertex-ai-feature-importance.png
|-- docs/
|   |-- README.md
|   |-- course-context.md
|   `-- project-walkthrough.md
`-- data/
    `-- README.md
```

## How to Review This Project

This repository does not support a full local rerun of the model workflow. A good review path is:

1. Start with this README for the project summary and limitations.
2. Read the [Project Walkthrough](docs/project-walkthrough.md) for the workflow.
3. Review the [Portfolio PDF](portfolio/EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf) for the shorter visual version.
4. Review the [Original Assignment Report](reports/EAI6020_Module_4_Assignment_Cheng_Liu.pdf) for the original course deliverable.
5. Check the [Dataset Note](data/README.md) and [Asset Guide](assets/README.md) for source and screenshot context.

## Limitations

- The raw Kaggle dataset is not included.
- The exact 20,000-row sampled working file is not included.
- No runnable notebook, script, training pipeline, or model artifact is included.
- The exact threshold-comparison artifact is not included.
- Results are documented through reports and Vertex AI screenshots.
- The project is not a production fraud detection system.
- The project is not a deployed app, dashboard, SQL project, GenAI project, or full MLOps project.
- The cost values are assignment assumptions, not measured business savings.
- Feature attribution should be interpreted carefully, especially because `TransactionID` appears as an important feature.
- Reported data quality checks cannot be independently verified from the repository without the raw or sampled data file.

## Future Improvements

- Add a reproducible sampling script with a fixed random seed.
- Add a small data dictionary for the documented columns.
- Add a threshold-vs-cost comparison table based on saved evaluation outputs.
- Re-test the model without `TransactionID` as a feature.
- Add clearer notes about how Vertex AI confidence thresholds were interpreted.
- Add a short recreation checklist for readers who download the dataset directly from Kaggle.

## Related Files

- [Project Walkthrough](docs/project-walkthrough.md)
- [Course Context](docs/course-context.md)
- [Dataset Note](data/README.md)
- [Asset Guide](assets/README.md)
- [Portfolio PDF](portfolio/EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf)
- [Original Assignment Report](reports/EAI6020_Module_4_Assignment_Cheng_Liu.pdf)
- [Reports Folder](reports/README.md)
- [Portfolio Folder](portfolio/README.md)
