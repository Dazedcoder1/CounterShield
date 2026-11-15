# Module 7 — CounterShield evaluation

CounterShield = per-dataset detector chosen on validation among classical (Module 4), MLP (Module 5) and their probability-average ensemble; operating points chosen on validation; everything below is on the held-out test split.

## Selected detectors

- **bot_iot**: classical — thresholds max_f1 0.6600, fpr_1pct 0.4933, fpr_0.1pct 0.9600
- **cic_ids2017**: classical — thresholds max_f1 0.7900, fpr_1pct 0.0045, fpr_0.1pct 0.4970
- **unsw_nb15**: classical — thresholds max_f1 0.4800, fpr_1pct 0.9094, fpr_0.1pct 0.9991

## Final results

| Dataset     | Operating point   |   Threshold |   Macro-F1 | Macro-F1 95% CI   |   Attack F1 |   Precision |   Recall |    MCC |   ROC-AUC |   PR-AUC |    FPR |    FNR |   Alerts / 100k benign |   Worst F1 drop (noise/dropout ≤ 0.25) | Note   |
|:------------|:------------------|------------:|-----------:|:------------------|------------:|------------:|---------:|-------:|----------:|---------:|-------:|-------:|-----------------------:|---------------------------------------:|:-------|
| bot_iot     | max_f1            |      0.6600 |     0.9978 | [0.9964, 0.9989]  |      1.0000 |      1.0000 |   0.9999 | 0.9956 |    1.0000 |   1.0000 | 0.0015 | 0.0001 |               145.8789 |                                 0.0567 |        |
| bot_iot     | fpr_1pct          |      0.4933 |     0.9982 | [0.9970, 0.9993]  |      1.0000 |      1.0000 |   1.0000 | 0.9963 |    1.0000 |   1.0000 | 0.0044 | 0.0000 |               437.6368 |                               nan      |        |
| bot_iot     | fpr_0.1pct        |      0.9600 |     0.9909 | [0.9882, 0.9932]  |      0.9998 |      1.0000 |   0.9996 | 0.9820 |    1.0000 |   1.0000 | 0.0007 | 0.0004 |                72.9395 |                               nan      |        |
| cic_ids2017 | max_f1            |      0.7900 |     0.9985 | [0.9983, 0.9986]  |      0.9974 |      0.9973 |   0.9974 | 0.9969 |    0.9999 |   0.9988 | 0.0005 | 0.0026 |                48.3244 |                                 0.2133 |        |
| cic_ids2017 | fpr_1pct          |      0.0045 |     0.9692 | [0.9684, 0.9700]  |      0.9483 |      0.9018 |   0.9999 | 0.9402 |    0.9999 |   0.9988 | 0.0196 | 0.0001 |              1964.4762 |                               nan      |        |
| cic_ids2017 | fpr_0.1pct        |      0.4970 |     0.9979 | [0.9977, 0.9981]  |      0.9965 |      0.9936 |   0.9993 | 0.9958 |    0.9999 |   0.9988 | 0.0012 | 0.0007 |               115.6206 |                               nan      |        |
| unsw_nb15   | max_f1            |      0.4800 |     0.8544 | [0.8521, 0.8569]  |      0.8861 |      0.8089 |   0.9795 | 0.7345 |    0.9775 |   0.9831 | 0.2835 | 0.0205 |             28351.3514 |                                 0.1257 |        |
| unsw_nb15   | fpr_1pct          |      0.9094 |     0.9156 | [0.9138, 0.9175]  |      0.9209 |      0.9550 |   0.8892 | 0.8339 |    0.9775 |   0.9831 | 0.0513 | 0.1108 |              5132.4324 |                               nan      |        |
| unsw_nb15   | fpr_0.1pct        |      0.9991 |     0.6782 | [0.6750, 0.6814]  |      0.6117 |      1.0000 |   0.4406 | 0.5113 |    0.9775 |   0.9831 | 0.0000 | 0.5594 |                 0.0000 |                               nan      |        |

## Robustness (primary operating point, worst macro-F1 drop)

- bot_iot: gaussian_noise worst drop +0.2024; feature_dropout worst drop +0.1443; threshold_shift worst drop +0.0003
- cic_ids2017: gaussian_noise worst drop +0.3637; feature_dropout worst drop +0.3358; threshold_shift worst drop +0.0001
- unsw_nb15: gaussian_noise worst drop +0.1252; feature_dropout worst drop +0.2410; threshold_shift worst drop +0.0211

## Reproducibility audit: 50 pass, 0 warn, 0 fail