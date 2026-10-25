## Architecture Decision Record (ADR)

| Decision | Requirement / Constraint | Alternatives Considered | Selected Option | Trade-off Accepted |
|---|---|---|---|---|
| Use SpaceNet8 dataset | FR1 / NFR1 / RAI1 | User-uploaded imagery; existing dataset | Existing SpaceNet8 dataset | Simpler data handling, but limited by available dataset coverage. |
| Include inspection prioritization | O3 / FR2 | Detection only; rule-based prioritization | Rule-based prioritization component | Additional processing, but supports preliminary inspection decisions. |
| Include XAI explanations | O3 / FR3 / NFR4 | Predictions only; XAI explanations | XAI component | Additional complexity, but improves interpretability. |
| Include scope restrictions | FR4 / FR5 | Disclaimer only; explicit restrictions | Preliminary assessment labels and scope restrictions | Limited functionality, but reduces misleading outputs. |

## Initial Requirements Traceability Matrix

| Objective | Requirement | Evaluation Criterion | Architecture Element | Later Evidence |
|---|---|---|---|---|
| O2 | FR1 / NFR1 / RAI1 | Flood identification correctness | SpaceNet8 dataset and deep learning model | F1-score and Recall ≥ 0.80 |
| O3 | FR2 | Inspection priority consistency | Prioritization component | Inspection priorities checked against defined criteria |
| O3 | FR3 / NFR4 | Visualization correctness | XAI component | Correct interpretation rate ≥ 80% |
| O3 | FR5 | Out-of-scope refusal | Scope restrictions | 100% compliance across 20 test requests |
| O3 | FR4 | Preliminary assessment labeling | Dashboard output labels | Results correctly labeled as preliminary assessments |
