# Retail Customer Analytics & Incremental Marketing Optimization

An end-to-end business analytics project using customer transactions and a randomized marketing experiment to evaluate campaign effectiveness and design a data-driven customer targeting strategy.

## 1. Project Overview

Retail companies often have limited marketing budgets and cannot send promotional communications to every customer. The key business challenge is not simply predicting who will make a purchase, but identifying customers whose purchase behavior can be incrementally influenced by a marketing intervention.

This project combines:

- Customer and transaction analysis
- Customer segmentation and value analysis
- A/B test evaluation
- Uplift modeling
- Marketing targeting policy optimization
- Business dashboard and executive recommendations

## 2. Business Problem

The company needs to answer four questions:

1. Who are the most valuable and strategically important customers?
2. Did the marketing communication cause an increase in purchase conversion?
3. Which customer segments responded positively or negatively to the campaign?
4. Under a limited campaign budget, which customers should be targeted to maximize incremental purchases?

## 3. Dataset

This project uses the public **X5 RetailHero Uplift Modeling** dataset.

The dataset contains:

- `clients.csv`: customer demographic and loyalty-program information
- `products.csv`: product hierarchy and product attributes
- `purchases.csv`: pre-campaign transaction history
- `uplift_train.csv`: treatment assignment and post-campaign purchase outcome
- `uplift_test.csv`: customers without publicly available outcomes

Dataset source:  
https://ods.ai/competitions/x5-retailhero-uplift-modeling/data

Raw data is not included in this repository because of file size and data usage considerations. Download instructions will be provided in `data/README.md`.

## 4. Analytical Framework

### Phase 1 — Data Quality and Business Understanding

- Validate table keys, missing values and duplicate records
- Examine customer, transaction and product coverage
- Build a documented data dictionary
- Identify potential data leakage and analytical limitations

### Phase 2 — Customer and Transaction Analytics

- Analyze revenue, purchase frequency and basket behavior
- Build customer-level behavioral features
- Perform RFM-style customer segmentation
- Examine product, store and loyalty-program behavior
- Identify commercially meaningful customer segments

### Phase 3 — A/B Test Evaluation

- Validate treatment and control group allocation
- Conduct sample-ratio mismatch and covariate-balance checks
- Estimate absolute and relative conversion lift
- Calculate confidence intervals and statistical significance
- Evaluate heterogeneous treatment effects across customer segments
- Assess statistical power and minimum detectable effect

### Phase 4 — Uplift Modeling

- Build baseline and machine-learning uplift models
- Estimate individual treatment effects
- Evaluate models using Qini, AUUC and uplift-at-k
- Compare uplift targeting with propensity-based targeting

### Phase 5 — Business Policy Optimization

Compare alternative campaign policies:

- Treat all customers
- Random targeting
- Target customers with high purchase propensity
- Target customers with high predicted uplift
- Target only customers with positive expected uplift

The final policy will be evaluated based on incremental purchases, targeting efficiency and scenario-based campaign economics.

## 5. Planned Deliverables

- Reproducible SQL and Python data pipeline
- Customer and transaction analysis notebooks
- A/B testing report
- Uplift modeling and policy evaluation
- Tableau business dashboard
- Executive summary with recommendations
- Documented assumptions, metrics and limitations

## 6. Technology Stack

- **SQL / DuckDB** — data transformation and analytical tables
- **Python** — pandas, NumPy, SciPy and statistical analysis
- **Machine Learning** — scikit-learn, LightGBM and scikit-uplift
- **Visualization** — Matplotlib, Seaborn and Tableau
- **Version Control** — Git and GitHub

## 7. Repository Structure

```text
retail-customer-uplift-analytics/
├── data/          # Data access instructions and local data folders
├── sql/           # SQL transformations and analytical marts
├── notebooks/     # Exploratory analysis, experimentation and modeling
├── src/           # Reusable Python modules
├── dashboard/     # Tableau workbook and dashboard screenshots
├── reports/       # Executive report, figures and final recommendations
├── docs/          # Data dictionary, metrics, methodology and limitations
├── requirements.txt
└── README.md
```

## 8. Project Status

- [x] Repository and project structure created
- [ ] Raw data downloaded and validated
- [ ] SQL analytical tables constructed
- [ ] Customer and transaction analysis completed
- [ ] A/B test evaluated
- [ ] Uplift models developed and compared
- [ ] Targeting policy optimized
- [ ] Tableau dashboard completed
- [ ] Executive report completed

## 9. Important Interpretation Note

The transaction table contains pre-campaign purchase history, while the experimental outcome is a binary post-campaign purchase indicator. Therefore, actual post-campaign revenue and profit cannot be directly observed.

Any campaign profitability analysis in this project will be clearly labeled as scenario-based and will not be presented as an observed causal revenue effect.