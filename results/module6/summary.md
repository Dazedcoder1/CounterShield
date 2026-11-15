# Module 6 — Cross-dataset analysis

## Test performance (tuned thresholds)

| Dataset | Model | Macro-F1 [95% CI] | Precision | Recall | ROC-AUC | pAUC@1% | PR-AUC | FPR | FNR |
|---|---|---|---|---|---|---|---|---|---|
| bot_iot | random_forest | 0.9978 [0.9964, 0.9989] | 1.0000 | 0.9999 | 1.0000 | 1.0000 | 1.0000 | 0.0015 | 0.0001 |
| bot_iot | torch_mlp_128_64 | 0.9880 [0.9848, 0.9907] | 0.9999 | 0.9997 | 0.9998 | 0.9961 | 1.0000 | 0.0146 | 0.0003 |
| cic_ids2017 | hist_gb | 0.9985 [0.9983, 0.9986] | 0.9973 | 0.9974 | 0.9999 | 0.9956 | 0.9988 | 0.0005 | 0.0026 |
| cic_ids2017 | torch_mlp_128_64 | 0.9943 [0.9939, 0.9946] | 0.9872 | 0.9935 | 0.9999 | 0.9970 | 0.9995 | 0.0023 | 0.0065 |
| unsw_nb15 | hist_gb | 0.8544 [0.8521, 0.8569] | 0.8089 | 0.9795 | 0.9775 | 0.8545 | 0.9831 | 0.2835 | 0.0205 |
| unsw_nb15 | torch_mlp_256_128_64 | 0.8589 [0.8566, 0.8614] | 0.8119 | 0.9838 | 0.9809 | 0.8805 | 0.9860 | 0.2793 | 0.0162 |

## Generalization

| Dataset | Model | Val macro-F1 | Test macro-F1 | Gap |
|---|---|---|---|---|
| bot_iot | classical | 0.9978 | 0.9978 | +0.0000 |
| bot_iot | mlp | 0.9860 | 0.9880 | +0.0019 |
| cic_ids2017 | classical | 0.9980 | 0.9985 | +0.0005 |
| cic_ids2017 | mlp | 0.9964 | 0.9943 | -0.0021 |
| unsw_nb15 | classical | 0.9350 | 0.8544 | -0.0805 |
| unsw_nb15 | mlp | 0.9182 | 0.8589 | -0.0593 |

Adversarial validation (train vs test ROC-AUC): bot_iot 0.494 (none/weak); cic_ids2017 0.502 (none/weak); unsw_nb15 0.874 (strong)

Cross-dataset transfer on shared Argus features (dur, spkts, dpkts, sbytes, dbytes, rate, proto, state):

| Train on | Test on | Macro-F1 | ROC-AUC | FPR | FNR |
|---|---|---|---|---|---|
| bot_iot | bot_iot | 0.9893 | 0.9996 | 0.0080 | 0.0004 |
| bot_iot | unsw_nb15 | 0.3097 | 0.3458 | 0.6901 | 0.6892 |
| unsw_nb15 | bot_iot | 0.2572 | 0.1489 | 0.9555 | 0.6517 |
| unsw_nb15 | unsw_nb15 | 0.8467 | 0.9719 | 0.2917 | 0.0271 |

## Errors

- bot_iot: both models wrong on 7 rows; only classical wrong 5; only MLP wrong 59
- cic_ids2017: both models wrong on 160 rows; only classical wrong 104; only MLP wrong 816
- unsw_nb15: both models wrong on 9,088 rows; only classical wrong 2,330; only MLP wrong 1,978