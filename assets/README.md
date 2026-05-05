# Assets

This folder contains the Vertex AI screenshots used as evidence for the project.

Because the model work was completed mainly through Vertex AI AutoML, these screenshots are important documentation artifacts. They help show the evaluation metrics, PR/ROC views, confusion matrix behavior, and feature attribution used in the case study.

## Included Screenshots

| File | Purpose |
|---|---|
| [vertex-ai-evaluation-details.png](images/vertex-ai-evaluation-details.png) | Shows reported Vertex AI evaluation metrics at the default confidence threshold. |
| [vertex-ai-pr-roc-curves.png](images/vertex-ai-pr-roc-curves.png) | Shows PR and ROC curve views for the imbalanced classification task. |
| [vertex-ai-confusion-matrix.png](images/vertex-ai-confusion-matrix.png) | Shows confusion matrix behavior used in the threshold discussion. |
| [vertex-ai-feature-importance.png](images/vertex-ai-feature-importance.png) | Shows Vertex AI feature attribution for the trained AutoML model. |

## Preview

### Evaluation Details

[![Evaluation details](images/vertex-ai-evaluation-details.png)](images/vertex-ai-evaluation-details.png)

### PR and ROC Curves

[![PR and ROC curves](images/vertex-ai-pr-roc-curves.png)](images/vertex-ai-pr-roc-curves.png)

### Confusion Matrix

[![Confusion matrix](images/vertex-ai-confusion-matrix.png)](images/vertex-ai-confusion-matrix.png)

### Feature Importance

[![Feature importance](images/vertex-ai-feature-importance.png)](images/vertex-ai-feature-importance.png)

## Interpretation Notes

- The evaluation details screenshot supports the reported model metrics, but it is not a complete training artifact.
- The PR/ROC curves are useful for explaining why imbalanced fraud detection should not rely only on accuracy.
- The confusion matrix is useful for discussing default-threshold behavior, but it should not be treated as the final selected operating policy.
- The feature importance screenshot is useful for model review, but `TransactionID` appearing as an important feature should be treated carefully because ID-style fields can create leakage or generalization concerns.

## Related Files

- [Main README](../README.md)
- [Project Walkthrough](../docs/project-walkthrough.md)
- [Portfolio PDF](../portfolio/EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf)
- [Original Assignment Report](../reports/EAI6020_Module_4_Assignment_Cheng_Liu.pdf)
