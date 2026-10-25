## Step B1

| Objective / Requirement ID | Evaluation Criterion | Capability Bucket | Measurement Method | Metric | Threshold | User / Business Outcome |
|---|---|---|---|---|---|---|
| O1 / FR1 / NFR1 / RAI1 | Flood identification correctness | Domain-specific | Evaluate predictions against ground-truth annotations. | F1-Score and Recall | >= 0.80 | Users receive reliable answers for flood-affected infrastructure assessment |
| O2 / FR3 / NFR4 | Visualization correctness | Generation | Test users’ understanding of XAI visualization. | Correct interpretations rate | >= 80% | Users can understand AI predictions through visual explanations. |
| O3 / FR5 | Out-of-Scope Refusal | Instruction-following | Test 20 requests involving real-time flood monitoring forecasting | Out-of-Scope compliance rate (%) | 100% | Users are not misled by unsupported real-time flood information. |

**Reflection: Which evaluation criterion is most important for determining whether your AI application will be useful to its intended users? Why?**

Flood identification correctness is the most important evaluation criterion because incorrect results can lead to poor decision-making by users, especially local authorities.
