# AI Ethics: Personalized Budget Predictor

This Udacity project builds an AI model for IDOOU, a hypothetical activity-recommendation app. The model predicts whether a user's activity budget is at least $300, then evaluates whether that prediction treats education groups fairly.

## What this project covers

- Exploratory analysis of representation, missing data, correlations, and dataset bias.
- Gaussian Naive Bayes and Logistic Regression model comparison.
- AIF360 fairness evaluation using statistical parity, disparate impact, average odds, equal opportunity, and the Theil index.
- Model interpretation with permutation importance.
- Bias mitigation with AIF360 Reweighing.
- Performance and fairness cohort analysis by education level.
- A complete, styled model card covering intended use, risks, limitations, and business consequences.

## Key results

The source dataset is severely biased toward users with bachelor's or master's degrees. Its statistical parity difference is `-0.9837`, and its disparate impact is `0.0089`.

The selected Logistic Regression model initially achieved `0.9980` balanced accuracy but reproduced that disparity. After AIF360 Reweighing:

- Balanced accuracy remained high at `0.9831`.
- Average odds difference improved from `-0.5278` to `-0.0111`.
- Equal opportunity difference improved from `-1.0000` to `0.0000`.
- Statistical parity difference improved only modestly to `-0.9522`, so the remaining risk is clearly documented rather than hidden.

## Repository contents

- `AI_Ethics_Project.ipynb` is the completed and executed analysis.
- `udacity_ai_ethics_project_data.csv` is obtained from the Udacity workspace and kept local rather than redistributed from this public repository.
- `images/` contains all generated visualizations.
- `model_card.html` is the final model card.
- `requirements.txt` pins the tested Python dependencies.

## Run locally

Python 3.12 is recommended.

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab
```

Download `udacity_ai_ethics_project_data.csv` from the Udacity workspace into the repository root. Then open `AI_Ethics_Project.ipynb`, select the `.venv` kernel, and run all cells from top to bottom.

## Responsible-use note

This model is a learning artifact, not a production decision system. A budget estimate must never be used for credit, insurance, employment, housing, pricing, eligibility, or other high-stakes decisions. A real IDOOU product should prioritize a budget entered directly by the user and provide correction, explanation, privacy, and opt-out controls.
