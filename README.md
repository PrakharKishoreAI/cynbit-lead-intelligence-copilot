# Cynbit Lead Intelligence Copilot

A lightweight Streamlit proof of concept exploring lead triage as a potential AI opportunity aligned with Cynbit's public focus on AI automation and CRM workflows.

## What it does
- Accepts a customer/project inquiry or loads a synthetic example.
- Produces a transparent score from 0–100 and a High/Medium/Low tier.
- Explains the rule signals, recommends a next action, and drafts a follow-up.
- Lets users download the assessment as JSON.

## Important scope note
This version uses an **explainable rule-based baseline**, not a trained ML model. No historical labeled dataset was provided, so claiming a trained model would be misleading. The report describes how to validate this baseline and evaluate a supervised model as a future step.

## Run locally
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
pip install -r requirements.txt
streamlit run app.py
```

## Deploy
1. Push this repository to GitHub.
2. Sign in at https://share.streamlit.io/ using GitHub.
3. Create an app, select this repository, branch `main`, and file `app.py`.
4. Deploy and test the generated `streamlit.app` URL.

## Repository structure
- `app.py` — Streamlit interface and scoring baseline
- `requirements.txt` — dependency
- `reports/ai_opportunity_report.md` — opportunity analysis
- `reports/technical_approach.md` — architecture, evaluation, and plan
- `reports/demo_script.md` — demo and interview notes

## Privacy
Only use synthetic sample data in this public demo. Do not enter real or confidential customer information.
