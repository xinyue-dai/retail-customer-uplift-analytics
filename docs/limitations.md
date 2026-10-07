# Limitations and Open Questions

## Observed data quality issues

- Age: 1,187 customers flagged (age <= 0 or > 100); values 115 and 119 account for 802. Cause is unknown; no age correction is inferred.
- First redemption: 35,469 missing; 536 earlier than card issue; 44,953 classified after the provisional cutoff. Classification is mutually exclusive and gives sequence violations priority.
- Gender U: 185,706 customers (46.4077%); F/M distributions alone do not represent all customers.
- Products: each hierarchy level has 3 nulls; segment_id 1,572; brand_id 5,200; vendor_id 34; netto 3. Matching product IDs does not imply complete attributes.
- Purchases: trn_sum_from_red has 42,743,212 nulls; quantity is zero in 2,707,278 detail rows, maximum 14,941; purchase_sum is zero in 620 detail rows. Detail counts are not order counts.
- There are 28 transaction IDs with multiple customers and 28 with multiple stores, times and amounts. Equal counts alone do not establish identical affected ID sets.

## Interpretation limits

The supplied local README and baseline do not establish randomization mechanics, intended allocation ratio, campaign dates, outcome-window duration, currency, quantity units, or full amount/point definitions. These remain pending source verification.

Loyalty metadata contains dates later than the transaction window and can leak future information. Historical snapshot completeness and attribute availability are not established. The age reference date is also unknown.

Test outcomes and assignments are not public. Use held-out labeled training customers for evaluation, not submission example values. Individual counterfactual outcomes are unobservable; customer causal types are not known labels.

Only binary post-communication purchase outcomes are available. Historical transaction amounts cannot establish post-campaign causal revenue or profit. Any ROI is scenario-based.

No claim that all validation is complete: point grain, numeric edge-case interpretation, identifier normalization, experiment design and historical feature availability remain open. No raw data is redistributed by this repository; the code license does not grant rights to the source dataset.
