# AI Opportunity Report — Cynbit Lead Intelligence Copilot

## Executive summary
This report proposes a lightweight lead-triage copilot as one possible AI opportunity for Cynbit. The goal is to help a team review incoming project inquiries consistently by highlighting service fit, urgency, stated budget, and clarity of the requested outcome. The prototype is a demonstration of the workflow, not a claim that Cynbit currently has this internal problem.

## Company and industry context
Cynbit's public website describes AI automation and software services. Its services content discusses AI agents that help manage leads and coordination, as well as CRM automation. This makes inquiry triage a plausible adjacent use case. Public CRM products also offer lead scoring, so explainability, ease of integration, and transparent human oversight are important considerations.

Reference links:
- Cynbit Services: https://www.cynbit.in/services
- Cynbit homepage: https://www.cynbit.in/
- Cynbit CRM automation article: https://www.cynbit.in/blog/best-crm-automation-strategies
- HubSpot lead scoring overview: https://www.hubspot.com/
- Apollo lead scoring product: https://www.apollo.io/product/lead-scoring-software

## Candidate opportunities
1. **Lead qualification and routing:** rank inquiries by fit, urgency, and completeness; suggest a human follow-up.
2. **Support inquiry classification:** categorize requests and route them to the right service team.
3. **Proposal/requirements summarization:** turn long project briefs into structured requirements and clarifying questions.
4. **Internal knowledge assistant:** help staff find approved answers in company documents with citations.

## Selected opportunity
**Lead Intelligence Copilot.** A user submits a project inquiry and receives:
- an explainable priority score from 0–100;
- a High, Medium, or Low tier;
- the signals that influenced the score;
- a recommended next action;
- a draft follow-up message; and
- a downloadable JSON result.

## Expected value and users
Potential users include sales, client-success, and project-intake staff. Potential benefits to validate include faster first review, more consistent routing, less manual triage, and clearer follow-up. These are hypotheses, not measured results from this prototype.

## Scope and assumptions
- Uses synthetic examples only.
- No CRM connection, user accounts, database, or external API.
- Score is produced by transparent heuristic rules, not a trained model.
- The tool supports human judgment; it does not autonomously accept/reject customers.

## Success criteria for a future pilot
- Compare the baseline against historical labeled outcomes.
- Measure precision and recall for sales-qualified leads, F1, PR-AUC where appropriate, and review time.
- Ask staff to rate whether explanations and recommended actions are useful.
- Track human overrides and investigate errors across lead types.
- Set thresholds with business owners before deployment.

## Risks and mitigations
- **Misranking:** display reasons and keep a human in the loop.
- **Bias from proxy signals:** avoid sensitive attributes and test across relevant segments.
- **Sparse or noisy data:** do not train until labels and data quality are reviewed.
- **Privacy:** use synthetic data in this demo; secure and minimize any future customer data.
- **Overclaiming:** clearly label scores as heuristic until validated.

## Recommendation
Treat this as a discovery prototype. If Cynbit confirms the workflow is useful, conduct stakeholder interviews, define labels and data access, and compare the baseline with a supervised model before any production integration.
