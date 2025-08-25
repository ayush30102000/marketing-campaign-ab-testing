# Marketing Campaign Analysis (A/B Testing)

This project evaluates the effectiveness of two digital advertising channels — Facebook and Google AdWords — across 2019 using a daily time-series dataset. It is designed to demonstrate analytical depth and business storytelling aligned to Product Analyst, Business Analyst, and Data Analyst roles.

## Why this project matters
- **Business goal**: Allocate spend to the higher ROI channel and understand when/why performance shifts.
- **Key questions**:
  - Which channel delivers more conversions and at what efficiency (CPC, conversion rate, cost per conversion)?
  - Do higher clicks translate to higher conversions consistently?
  - Is Facebook statistically better than AdWords for conversions?
  - How do conversions and CPC evolve across weekdays and months?
  - Is there a stable long-term relationship between spend and conversions?

## Dataset
- File: `ABmarketing_campaign.csv` (365 daily records for 2019)
- Metrics (selected):
  - Views, Clicks, Conversions for Facebook and AdWords
  - Cost per ad, CTR, Conversion Rate, Cost per Click (CPC)
- Target variable(s): Conversions

## Methods and techniques
- Exploratory analysis: distribution plots, descriptive statistics
- Correlation analysis: clicks ↔ conversions, per channel
- Hypothesis testing: Welch’s t-test for mean conversions (Facebook > AdWords)
- Predictive modeling: Simple Linear Regression (Facebook clicks → conversions)
- Time analysis: weekday and monthly conversions, CPC trend
- Cointegration test: Long-term equilibrium between cost and conversions

## Tools and libraries
- Python, Jupyter Notebook
- pandas, numpy, seaborn, matplotlib
- scipy (stats), scikit-learn (LinearRegression, metrics)
- statsmodels (cointegration, seasonal utilities)

## Business-focused highlights
- **Effectiveness**: Facebook shows higher average conversions and a strong correlation between clicks and conversions (≈0.87) vs AdWords (≈0.45).
- **Statistical validity**: Welch’s t-test strongly rejects the null hypothesis (p ≪ 0.05), supporting Facebook’s superior conversions.
- **Predictability**: Linear regression explains ≈76% of variance in Facebook conversions from clicks (R² ≈ 0.76).
- **Seasonality and timing**: Mondays/Tuesdays and several months show stronger conversion totals; CPC varies across months, with opportunities in May and November.
- **Budget strategy**: Evidence supports shifting incremental spend to Facebook while monitoring monthly CPC fluctuations and weekday behavior.

## Reproducibility
- Notebook: `Marketing Campaigns AB Testing.ipynb`
- Relative file path is used to load the CSV after pushing to GitHub.

### Environment setup
```bash
python -m venv .venv
. .venv/Scripts/activate  # Windows PowerShell
pip install -r requirements.txt
```
Optional kernel registration for Jupyter:
```bash
python -m ipykernel install --user --name marketing-campaign-venv --display-name "Python (marketing-campaign)"
```

### Run the analysis
```bash
jupyter notebook "Marketing Campaigns AB Testing.ipynb"
```
The notebook reads `ABmarketing_campaign.csv` from the repo root.

## Results at a glance
- Descriptive stats show higher central tendency for Facebook conversions.
- Correlation: Facebook (≈0.87), AdWords (≈0.45).
- Hypothesis test: Facebook conversions > AdWords conversions (p-value extremely small).
- Regression (Facebook): R² ≈ 76.35%, MSE ≈ 2.02; example predictions for 50/80 clicks provided in notebook.
- Time trends: Consistent weekday performance with peaks on Mon/Tue; CPC fluctuates monthly with lower CPC in May/Nov.
- Cointegration: Strong evidence of long-term equilibrium between spend and conversions.

## How this maps to analyst competencies
- **Product sense**: Clear hypotheses tied to outcomes (conversions, CPC, ROI) and actionable recommendations.
- **Experimentation & inference**: Appropriate test (Welch’s t-test) for unequal variances; interprets p-values and practical significance.
- **Data storytelling**: Visuals and narrative connect insights to decisions (allocation, timing, optimization).
- **Modeling**: Uses simple regression for directional forecasting and expectation setting.
- **Time-based reasoning**: Identifies weekday/monthly patterns for planning and budgeting.
- **Stakeholder alignment**: Frames insights for marketing and growth stakeholders; emphasizes trade-offs and next steps.

## Decisions and recommendations
- Shift incremental budget to Facebook given higher and more predictable conversions.
- Exploit lower CPC months (e.g., May, November) and stronger weekdays (Mon/Tue) for campaigns.
- Continue monitoring AdWords; investigate creative/targeting changes to close the gap.
- Establish recurring performance reviews and simple predictive targets (clicks → expected conversions) to guide pacing.

## Assumptions and caveats
- Historical performance may not generalize under major creative/audience/auction changes.
- Linear model is intentionally simple and univariate; multivariate drivers (seasonality, spend levels, targeting) could improve predictions.
- Dataset quality (missing or formatted percent/currency fields) is cleaned within the notebook.

## Potential extensions
- Uplift modeling and budget optimization under constraints
- Mixed-effects or time-series models for seasonality and trends
- Propensity scoring or causal methods for more rigorous channel impact
- Dashboarding with Plotly/Streamlit for stakeholders

## Project structure
- `Marketing Campaigns AB Testing.ipynb` — main analysis notebook
- `ABmarketing_campaign.csv` — dataset
- `requirements.txt` — dependencies
- `.gitignore`, `.gitattributes`, `LICENSE`, `README.md`

## Contact
If this project aligns with your needs, I’d be glad to discuss the approach, assumptions, and how I’d adapt this workflow to your product or business context.
