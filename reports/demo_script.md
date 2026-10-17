# Two-minute demo and interview notes

## Demo walkthrough
1. “This is a proof of concept for a potential lead-triage workflow aligned with Cynbit's public AI automation and CRM focus.”
2. Choose **High-intent AI project** and click **Evaluate inquiry**.
3. Point out the score, priority tier, and the individual reasons.
4. Show the recommended next action and follow-up draft.
5. Download the JSON result.
6. Switch to the low-urgency website example and compare the output.
7. Close with: “This version uses transparent rules because we don't have labeled historical data. The next step would be to compare this baseline with supervised models using precision, recall, F1, and business outcomes.”

## Likely interview questions
**Why this use case?** It is a plausible fit with Cynbit's public emphasis on AI automation and CRM workflows, and it can be demonstrated without needing confidential systems.

**Is this a machine-learning model?** Not yet. It is an explainable rule-based baseline. I would not claim a trained model without a valid dataset and evaluation.

**How would you improve it?** Define a qualified-lead label, collect governed historical data, establish a baseline, compare logistic regression and tree-based models, evaluate precision/recall and business outcomes, then pilot with human review.

**Why Streamlit?** It enables a working Python demo quickly and keeps the UI, processing, and deployment simple for a proof of concept.

**What are the limitations?** Keywords lack context, the score is not a conversion probability, and the weights/thresholds have not been calibrated against outcomes.

**How would you use an LLM?** Optionally use it to extract structured requirements or draft responses with schema validation and human approval. I would first assess privacy, cost, reliability, and whether rules or a trained classifier already meet the need.
