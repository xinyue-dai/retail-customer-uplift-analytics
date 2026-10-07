# Methodology

## Current validation

See notebooks/01_data_validation.ipynb for executed checks and outputs. CSVs are queried through DuckDB; pandas receives samples and aggregates only. Sampled type inference is provisional. Complete-row duplicate checks compare parsed values, not raw CSV bytes.

Verified: five small-table keys are unique and non-null/non-blank; train/test are disjoint and together cover clients; test/submission ID sets match; all purchase customer/product IDs match dimension tables; no identical parsed purchase rows were found. Experiment fields are binary and non-null.

## Provisional cleaning and aggregation rules

- Preserve source files and all customers.
- Preserve age as age_raw; define age_clean as ages 1–100, otherwise null; flag out-of-range ages for review. This is an analytical convention, not verified age truth.
- Exclude first_redeem_date and derived features from the primary model pending historical-availability confirmation. Do not use future-redemption status as a predictor.
- Use 2019-03-18 23:40:03, the last observed transaction, as a provisional historical reference cutoff, not a confirmed campaign date.
- Group candidate orders by client_id, transaction_id, store_id, transaction_datetime. After consistency validation, retain purchase_sum once per group using MIN or MAX; never sum it across detail rows.
- Keep zero quantities, missing attributes and negative point debits pending interpretation. Point fields require separate within-order consistency checks before aggregation.

These rules are documented but the cleaned data layer has not yet been implemented.

## Planned experiment and model evaluation

Confirm assignment mechanism, planned allocation ratio, campaign timing and outcome window from source material. Observed near-equal group sizes do not prove randomization. SRM conclusions require a justified expected allocation. Assess pre-treatment covariate balance before interpreting effects.

Split labeled experiment customers into training, validation and untouched final evaluation sets. Fit preprocessing on training data. Compare random, purchase-propensity and uplift policies on the same held-out customers and budget. Predicted uplift estimates conditional average effects, not observable individual causal labels.

Profitability calculations will use explicitly stated cost/margin scenarios; no post-campaign revenue is observed.
