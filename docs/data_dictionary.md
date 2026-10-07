# Data Dictionary

Source: X5 RetailHero files supplied locally. Types below are sampled DuckDB inferences, not enforced schemas. Meanings not established by the supplied competition README are marked provisional.

## Table inventory

| File | Rows | Columns | Grain / key |
|---|---:|---:|---|
| clients | 400,162 | 5 | Customer; client_id unique |
| products | 43,038 | 11 | Product; product_id unique |
| purchases | 45,786,568 | 13 | Purchase detail; unique detail key not established |
| uplift_train | 200,039 | 3 | Experiment customer; client_id unique |
| uplift_test | 200,123 | 1 | Competition scoring customer; client_id unique |
| uplift_sample_submission | 200,123 | 2 | Example prediction per test customer |

## Clients

| Field | Inferred type | Meaning / qualification |
|---|---|---|
| client_id | VARCHAR | Customer identifier; preserve as text |
| first_issue_date | TIMESTAMP | First card issue date; precise card lifecycle definition unconfirmed |
| first_redeem_date | TIMESTAMP | First redemption date; timing and missing-value meaning need confirmation |
| age | BIGINT | Reported age; reference date unconfirmed; contains implausible values |
| gender | VARCHAR | Observed codes U, F, M; retain U as unknown pending source confirmation |

## Products

| Field | Inferred type | Meaning / qualification |
|---|---|---|
| product_id | VARCHAR | Product identifier |
| level_1, level_2, level_3, level_4 | VARCHAR | Encoded hierarchy levels; business category names unavailable |
| segment_id | DOUBLE | Category/segment identifier; not a continuous measure; coding pending review |
| brand_id | VARCHAR | Encoded brand identifier |
| vendor_id | VARCHAR | Encoded vendor identifier |
| netto | DOUBLE | Product net-content attribute; definition and units unconfirmed |
| is_own_trademark | BIGINT | Provisional own-brand flag; observed values 0 and 1 |
| is_alcohol | BIGINT | Provisional alcohol flag; observed values 0 and 1 |

## Purchases

The supplied README identifies this file as purchase history before the SMS campaign.

| Field | Inferred type | Meaning / qualification |
|---|---|---|
| client_id | VARCHAR | Customer identifier |
| transaction_id | VARCHAR | Transaction identifier; not globally unique as an order key |
| transaction_datetime | TIMESTAMP | Transaction timestamp; timezone unconfirmed |
| store_id | VARCHAR | Store identifier |
| product_id | VARCHAR | Product identifier |
| purchase_sum | DOUBLE | Amount consistent within candidate orders; currency, discounts and accounting definition unconfirmed |
| product_quantity | DOUBLE | Recorded quantity; units unconfirmed; includes zero and extreme values |
| regular_points_received | DOUBLE | Provisional regular points credited |
| express_points_received | DOUBLE | Provisional express points credited |
| regular_points_spent | DOUBLE | Provisional regular points debited; observed values non-positive |
| express_points_spent | DOUBLE | Provisional express points debited; observed values non-positive |
| trn_sum_from_iss | DOUBLE | Definition unconfirmed; do not infer from abbreviation |
| trn_sum_from_red | DOUBLE | Definition unconfirmed; 93.3532% null |

Candidate order grain: (client_id, transaction_id, store_id, transaction_datetime), yielding 8,045,229 groups. Each has one distinct purchase_sum. This is an analytical definition, not a source-system guarantee.

## Experiment and submission

| Field | Inferred type | Meaning |
|---|---|---|
| treatment_flg | BIGINT | 1: communication; 0: no communication |
| target | BIGINT | 1: purchase afterward; 0: no purchase afterward; outcome-window length unconfirmed |
| uplift | DOUBLE | Example submission prediction; not observed causal ground truth |

Train contains client_id, treatment_flg, target; test contains only client_id; the submission example contains client_id and uplift.
