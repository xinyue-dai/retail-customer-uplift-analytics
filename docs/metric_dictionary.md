# Metric Dictionary

## Validated data metrics

| Metric | Definition | Result |
|---|---|---:|
| Customer records | Rows in clients; key uniqueness verified | 400,162 |
| Product records | Rows in products; key uniqueness verified | 43,038 |
| Purchase detail rows | Rows in purchases | 45,786,568 |
| Candidate orders | Distinct four-field order groups | 8,045,229 |
| Control customers | treatment_flg = 0 | 100,058 |
| Treatment customers | treatment_flg = 1 | 99,981 |

## Planned business and experiment metrics

| Metric | Definition / qualification |
|---|---|
| Historical recorded order amount | purchase_sum retained once per validated order group; accounting definition pending |
| Average order amount | Total recorded order amount / candidate order count; zero-amount policy must be explicit |
| Treatment conversion | Treated purchasers / treated customers |
| Control conversion | Control purchasers / control customers |
| Absolute lift | Treatment conversion minus control conversion; report in percentage points |
| Relative lift | Absolute lift / control conversion, if control conversion > 0 |
| Estimated incremental purchasers | Absolute lift × treated customer count; estimate, not directly observed people |
| Null percentage | 100 × parsed NULL count / row count |
| Duplicate excess rows | Sum of occurrence count minus one over repeated groups |
| Scenario ROI | (Estimated incremental purchasers × assumed margin per purchaser − campaign cost) / campaign cost; cost must be positive |

Effect estimates, uncertainty and targeting metrics are planned; they are not yet finalized. Different Qini/AUUC conventions must be documented before comparing results.
