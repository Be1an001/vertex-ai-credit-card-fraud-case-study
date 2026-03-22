\# Vertex AI Credit Card Fraud Case Study



A portfolio case study from \*\*EAI6020: AI Systems Technology\*\* at Northeastern University.



This project shows how I used \*\*Google Cloud Vertex AI AutoML\*\* to work on a \*\*credit card fraud detection\*\* problem with an imbalanced dataset. The main focus of this project is not hand-written model code. Instead, it is about \*\*business framing, model evaluation, threshold selection, and explainability\*\* in a cloud AI workflow.



\## Why I included this project



I included this project in my portfolio because it shows a different side of my work.



Many of my other projects are more code-heavy. This one is more about:



\- defining a real business problem

\- choosing an appropriate evaluation method for imbalanced data

\- using Vertex AI AutoML in a practical way

\- understanding false positive vs. false negative trade-offs

\- interpreting model outputs and feature importance

\- making a threshold decision based on business impact



\## Project summary



For this assignment, I used a public Kaggle credit card fraud dataset and built a fraud detection model in Vertex AI AutoML.



My first training attempt used the full dataset, but it failed because of a cloud resource quota issue. I then created a smaller \*\*20,000-row stratified sample\*\* that kept the original \*\*1% fraud ratio\*\* and retrained the model successfully.



The final project focused on:



\- \*\*Precision-Recall evaluation\*\*

\- \*\*ROC and confusion matrix review\*\*

\- \*\*threshold tuning\*\*

\- \*\*feature importance interpretation\*\*

\- \*\*business cost trade-off thinking\*\*



\## Key results



According to my assignment report and Vertex AI evaluation screenshots:



\- \*\*PR AUC:\*\* 0.989

\- \*\*ROC AUC:\*\* 0.991

\- \*\*Default confidence threshold:\*\* 0.5

\- \*\*Macro-average F1 at default threshold:\*\* about 0.498

\- \*\*Selected threshold:\*\* 0.75

\- \*\*Approximate precision at selected threshold:\*\* 96%

\- \*\*Approximate recall at selected threshold:\*\* 82%



This showed me that a strong overall model score does not automatically mean the default decision threshold is good for a business problem like fraud detection.



\## Business scenario



I used a simple cost scenario to evaluate business impact:



\- \*\*False Negative cost:\*\* $500  

&#x20; Missing a fraudulent transaction creates direct financial loss.



\- \*\*False Positive cost:\*\* $50  

&#x20; Incorrectly flagging a valid transaction creates customer friction and support cost.



This helped me explain why threshold choice matters. A fraud model should not be judged only by technical scores. It should also be judged by how well it balances financial risk and customer experience.



\## Why Vertex AI AutoML



I used Vertex AI AutoML because this course module focused on AI systems thinking, cost-aware ML workflow decisions, trust in AI, and AutoML as part of practical business adoption.



This project helped me practice:



\- cloud-based model training

\- choosing an optimization objective

\- evaluating model behavior beyond accuracy

\- using built-in visual tools for model interpretation

\- thinking about AI as a business system, not only as an algorithm



\## Repository structure



```text

.

├── README.md

├── .gitignore

├── reports/

│   ├── README.md

│   └── EAI6020\_Module\_4\_Assignment\_Cheng\_Liu.pdf

├── portfolio/

│   ├── README.md

│   └── EAI6020\_VertexAI\_Credit\_Card\_Fraud\_Portfolio\_Cheng\_Liu.pdf

├── assets/

│   ├── README.md

│   └── images/

│       ├── vertex-ai-evaluation-details.png

│       ├── vertex-ai-pr-roc-curves.png

│       ├── vertex-ai-confusion-matrix.png

│       └── vertex-ai-feature-importance.png

├── docs/

│   ├── README.md

│   ├── course-context.md

│   └── project-walkthrough.md

└── data/

&#x20;   └── README.md

