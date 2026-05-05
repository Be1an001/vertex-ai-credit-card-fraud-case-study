# Course Context

## Course

**EAI6020: AI Systems Technology**  
Northeastern University

## Project Fit

This project fits the course because EAI6020 was not only about building models. It also focused on how AI systems are used in business and organizational settings.

The course covered topics such as:

- AI adoption in business
- solution design
- machine learning workflow thinking
- model evaluation and optimization
- explainability and trust
- sustaining AI solutions
- business alignment for AI projects

In Module 4, the focus moved more directly into cost-aware machine learning workflow decisions, AutoML, trust in AI outputs, and practical evaluation choices.

## Why Vertex AI AutoML Was Used

I used Vertex AI AutoML because the assignment was not mainly about writing a custom classifier. The goal was to practice a cloud AI workflow and evaluate how the model output could support a business decision.

Vertex AI helped me work on:

- cloud-based model training
- selecting an optimization objective
- evaluating an imbalanced classification problem
- using precision-recall instead of relying only on accuracy
- reviewing model outputs visually
- thinking about implementation limits such as cloud resource quotas

## How the Project Connects to the Course

### Business Framing

Fraud detection has a clear trade-off between missed fraud and false alarms. This made it a useful case for thinking about AI as a business decision-support tool.

### Metric Selection

The dataset was highly imbalanced, so precision-recall evaluation was more appropriate than simple accuracy.

### AI System Thinking

The project included a cloud resource quota issue during training. That experience connected the model workflow to platform limits, cost, and planning.

### Trust and Explainability

The feature attribution output gave a way to review which fields the model relied on. This connected to the course discussion about trust and explainability, while still requiring careful interpretation.

## Learning Takeaway

This project helped me practice the idea that a useful AI project needs:

- a clear business problem
- an evaluation metric that fits the problem
- a threshold decision that matches the use case
- careful interpretation of model outputs
- realistic thinking about operational limits

## Related Files

- [Main README](../README.md)
- [Project Walkthrough](project-walkthrough.md)
- [Portfolio PDF](../portfolio/EAI6020_VertexAI_Credit_Card_Fraud_Portfolio_Cheng_Liu.pdf)
- [Original Assignment Report](../reports/EAI6020_Module_4_Assignment_Cheng_Liu.pdf)
- [Dataset Note](../data/README.md)
