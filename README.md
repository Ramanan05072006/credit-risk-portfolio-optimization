# Credit Risk & Portfolio Optimization System

> **Status:** In development  
> **Focus:** Financial Analytics | Data Analytics | Business Intelligence | Applied Data Science

## 1. Project Overview

Financial institutions must estimate the risk of borrower default while balancing expected returns, potential losses, and the cost of deploying capital. Investors face a related challenge: allocating capital across assets while accounting for volatility, drawdowns, and trading costs.

This project develops an analytical decision-support system with two separate financial modules:

- **Module A — Credit Risk Intelligence:** estimate credit default risk, evaluate imbalanced classification models, explain individual predictions, and calculate expected credit loss.
- **Module B — Portfolio Optimization:** compare asset allocation strategies, evaluate risk-adjusted performance, and simulate portfolio rebalancing after transaction fees and slippage.
- **Reporting Layer:** use Python, SQL, and an interactive dashboard to communicate financial insights and actionable recommendations.

The project is intended for educational and portfolio demonstration purposes. It is not a production lending system or investment advisory service.

## 2. Project Objectives

- Perform reproducible data cleaning, validation, and exploratory analysis.
- Build and compare baseline and tree-based credit-risk models.
- Prevent data leakage during preprocessing, validation, and resampling.
- Evaluate imbalanced classification using precision, recall, PR-AUC, and calibration.
- Explain predictions using SHAP.
- Estimate expected credit loss using probability of default, loss given default, and exposure at default.
- Construct and compare portfolio allocation strategies.
- Account for transaction costs and slippage during rebalancing.
- Communicate findings through SQL analysis, Python visualizations, and a dashboard.

## 3. Technology Stack

| Area | Tools |
|---|---|
| Programming | Python |
| Data processing | pandas, NumPy |
| Machine learning | scikit-learn, imbalanced-learn |
| Explainable AI | SHAP |
| Statistical analysis | SciPy, scikit-learn |
| Financial calculations | NumPy, pandas |
| Visualization | Matplotlib, Plotly |
| Database analysis | SQL |
| Dashboard | Streamlit initially; Power BI planned |
| Development | Anaconda, Jupyter, Git, GitHub |

## 4. Module A — Credit Risk Intelligence

### Business problem

How can a lender identify applicants with elevated default risk while understanding model errors and the potential financial impact of credit losses?

### Planned workflow

1. Acquire a documented public credit-risk dataset.
2. Audit the data dictionary, missing values, duplicates, target balance, and feature availability.
3. Perform exploratory data analysis and identify potential leakage.
4. Establish a logistic regression baseline.
5. Compare class-weighted and training-fold-only resampling approaches.
6. Evaluate a tree-based model against the baseline.
7. Plot precision-recall curves and select a decision threshold using explicit business-cost assumptions.
8. Assess probability calibration.
9. Generate global and individual SHAP explanations.
10. Estimate expected credit losses under clearly stated assumptions.

### Key evaluation metrics

- Precision and recall
- F1-score
- Average precision and precision-recall curve
- Confusion matrix
- Probability calibration
- Expected credit loss

### Expected credit loss

**Expected Loss = Probability of Default × Loss Given Default × Exposure at Default**

Any assumptions about recovery rates, exposure, and loss severity will be documented separately from model predictions.

## 5. Module B — Portfolio Optimization

### Business problem

How do different allocation strategies perform when market risk and realistic trading costs are considered?

### Planned workflow

1. Acquire and validate historical adjusted price data.
2. Calculate asset returns, volatility, and correlations.
3. Establish an equal-weight benchmark.
4. Construct a constrained portfolio optimization strategy.
5. Define a rebalance schedule and use only information available at each rebalance.
6. Deduct a 0.1% transaction fee on traded notional.
7. Include configurable slippage assumptions.
8. Compare gross and net portfolio performance.
9. Evaluate the strategy on out-of-sample periods.

### Key performance metrics

- Annualized return
- Annualized volatility
- Sharpe ratio
- Maximum drawdown
- Cumulative net returns
- Turnover and transaction costs

Portfolio optimization results will be treated as historical simulations, not predictions of guaranteed future performance.

## 6. Data Leakage and Validation Policy

- Split the data before fitting preprocessing or resampling steps.
- Apply SMOTE only within training folds when it is appropriate for the feature types.
- Compare resampling with class weighting and an unmodified baseline.
- Keep validation and test sets at their natural class distribution.
- Check that predictors would have been available at the intended prediction time.
- Use time-aware evaluation when the data supports it.
- Keep portfolio optimization and backtesting free from future-information leakage.
- Report limitations, uncertainty, and relevant fairness concerns.

## 7. Repository Structure

```text
credit-risk-portfolio-optimization/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
├── src/
│   ├── credit_risk/
│   └── portfolio/
├── sql/
├── reports/
│   ├── figures/
│   └── model_cards/
├── dashboard/
├── tests/
├── requirements.txt
├── .gitignore
└── README.md
```

Large raw datasets, secrets, and generated files will be excluded from version control where appropriate.

## 8. Planned Deliverables

- Reproducible data audit
- Exploratory data analysis
- Credit-risk modeling pipeline
- Model evaluation and explainability reports
- Expected credit loss analysis
- Portfolio allocation and backtesting engine
- SQL business analysis
- Interactive Python dashboard
- Power BI dashboard
- Final technical report and model limitations

## 9. Development Roadmap

- [ ] Select and document the credit-risk dataset
- [ ] Complete the raw data audit
- [ ] Build the initial credit-risk baseline
- [ ] Implement leakage-safe validation and class-imbalance comparisons
- [ ] Add precision-recall evaluation and calibration
- [ ] Integrate SHAP explanations
- [ ] Complete expected credit loss analysis
- [ ] Implement portfolio optimization
- [ ] Add transaction fees and slippage
- [ ] Build SQL analyses and the Python dashboard
- [ ] Develop the Power BI dashboard
- [ ] Document results, limitations, and reproducibility

## 10. Intended Learning Outcomes

This project is designed to demonstrate skills relevant to financial analyst, data analyst, business analyst, and data scientist roles, including data preparation, statistical reasoning, machine learning, model interpretation, financial calculations, SQL, and business communication.

## 11. Data Sources and Attribution

The final dataset selection, source URLs, licenses, attribution requirements, and download dates will be documented here before analysis begins.

## Disclaimer

This is an educational analytics project. Historical model performance does not guarantee future performance. Credit predictions require appropriate validation, fairness assessment, and governance before any real-world use. Portfolio backtests are sensitive to data quality, assumptions, trading costs, and market conditions.
