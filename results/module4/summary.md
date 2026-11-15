# Module 4 — Classical ML results

Binary detection (benign vs attack). Models compared on validation after training on a stratified 300,000-row subsample of train; the selected model is retrained on train + val (cap 1,000,000) and evaluated once on test. Seed 42.

## Validation (model comparison)

| Dataset | logreg | random_forest | hist_gb | mlp |
|---|---|---|---|---|
| bot_iot | 0.8957 | 0.9974 | 0.9943 | 0.9900 |
| cic_ids2017 | 0.9566 | 0.9972 | 0.9977 | 0.9944 |
| unsw_nb15 | 0.9061 | 0.9333 | 0.9343 | 0.9164 |

Values are validation f1_macro.

## Held-out test (selected model)

| Dataset | Model | Threshold | Macro-F1 | Attack F1 | Precision | Recall | MCC | ROC-AUC | PR-AUC | FPR | FNR |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bot_iot | random_forest | 0.500 | 0.9982 | 1.0000 | 1.0000 | 1.0000 | 0.9963 | 1.0000 | 1.0000 | 0.0044 | 0.0000 |
| bot_iot | random_forest | 0.660 | 0.9978 | 1.0000 | 1.0000 | 0.9999 | 0.9956 | 1.0000 | 1.0000 | 0.0015 | 0.0001 |
| cic_ids2017 | hist_gb | 0.500 | 0.9979 | 0.9965 | 0.9936 | 0.9993 | 0.9958 | 0.9999 | 0.9988 | 0.0012 | 0.0007 |
| cic_ids2017 | hist_gb | 0.790 | 0.9985 | 0.9974 | 0.9973 | 0.9974 | 0.9969 | 0.9999 | 0.9988 | 0.0005 | 0.0026 |
| unsw_nb15 | hist_gb | 0.500 | 0.8590 | 0.8888 | 0.8147 | 0.9777 | 0.7409 | 0.9775 | 0.9831 | 0.2725 | 0.0223 |
| unsw_nb15 | hist_gb | 0.480 | 0.8544 | 0.8861 | 0.8089 | 0.9795 | 0.7345 | 0.9775 | 0.9831 | 0.2835 | 0.0205 |

## Attack classes detected below 90% on test (tuned threshold)

- cic_ids2017 / bot: 0.667 of 210 rows
- cic_ids2017 / heartbleed: 0.500 of 2 rows
- cic_ids2017 / infiltration: 0.600 of 5 rows
- unsw_nb15 / fuzzers: 0.894 of 6,062 rows