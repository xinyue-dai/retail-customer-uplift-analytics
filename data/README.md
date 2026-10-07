# Data Access

Obtain the X5 RetailHero Uplift Modeling dataset from the competition source:
https://ods.ai/competitions/x5-retailhero-uplift-modeling/data

Place these six files in data/raw: clients.csv, products.csv, purchases.csv, uplift_train.csv, uplift_test.csv, uplift_sample_submission.csv. Follow the source's access and usage terms; the repository MIT license applies to project code, not the dataset.

Raw data, processed datasets and local databases are excluded from Git. purchases.csv is approximately 4.26 GiB; query it with DuckDB rather than loading it fully into pandas. Local intermediates belong in data/processed.

See docs/data_dictionary.md and notebooks/01_data_validation.ipynb for verified structure and validation. Example submission scores are not observed outcomes.
