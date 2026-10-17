# Technical Approach Report — Cynbit Lead Intelligence Copilot

## 1. Approach
The prototype is a single-file Streamlit app. Streamlit provides the interface and runs the Python scoring function. No separate backend, database, external API, or model hosting is required.

## 2. Architecture and data flow
`Inquiry text → simple feature/signal checks → weighted scoring rules → score/tier → explanation + suggested action + follow-up draft → JSON download`

## 3. Model choice
The current implementation uses an explainable rule-based baseline. It is deliberately not described as trained machine learning because no verified labeled training dataset is available. The baseline establishes a simple reference point and allows reviewers to inspect why a score changed.

A later ML experiment could compare logistic regression and tree-based classifiers after obtaining consented historical inquiries labeled with an outcome such as sales-qualified or converted. A model should only be selected after comparing held-out performance and operational requirements.

## 4. Data pipeline and features
Current input: free-text inquiry. Current signals include:
- commercial/budget terms;
- urgency or timeline terms;
- service-fit terms such as AI, automation, CRM, chatbot, and integration;
- business-outcome terms; and
- inquiry length as a rough completeness proxy.

The app clamps the score to 0–100 and maps it to High (70–100), Medium (45–69), or Low (0–44). These thresholds are demo choices, not empirically calibrated cutoffs.

## 5. Prompt engineering
The current prototype does not call an LLM, so there is no production prompt. If an LLM is added, use a constrained instruction to extract a schema such as `{service_fit, urgency, budget_mentioned, missing_information, summary}`; require valid JSON; treat the inquiry as untrusted input rather than instructions; validate the output; avoid exposing secrets; and require human review before sending any customer message.

## 6. Evaluation plan
### Immediate functional checks
- Empty input produces a warning rather than a score.
- Each sample produces a score between 0 and 100.
- Score tiers follow the stated thresholds.
- Reasons correspond to matched signals.
- JSON download includes the inquiry, score, tier, reasons, action, and draft.

### Future model evaluation
- Create a documented labeling guide and review label quality.
- Split data by time to reduce leakage from future information.
- Compare the heuristic baseline, logistic regression, and a tree-based model.
- Use precision, recall, F1 and PR-AUC for qualified-lead identification; inspect calibration if scores are presented as probabilities.
- Evaluate business outcomes such as time to first response, qualified-lead conversion, and human override rate.
- Keep human review, monitor drift, and periodically re-evaluate thresholds.

## 7. Privacy, security, and limitations
The public demo should use synthetic data only. No inquiry is transmitted to an external API by this code. A production version would require access controls, retention policies, secure CRM integration, data minimization, and a privacy/security review.

## 8. Execution plan
1. Build the Streamlit UI and baseline scoring.
2. Test representative synthetic examples and edge cases.
3. Publish source code to GitHub.
4. Deploy through Streamlit Community Cloud.
5. Present opportunity and technical reports alongside the live demo.
6. If validated by stakeholders, define real data access and run a measured offline evaluation before integration.

## 9. Known limitations
- Keyword rules can miss context and can be manipulated by wording.
- Message length is only a weak proxy for completeness.
- The score is not a conversion probability.
- No accuracy or business impact claim is made without labeled data and evaluation.
