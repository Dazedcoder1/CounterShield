# Module 5 — MLP experiments

PyTorch MLPs on GPU Tesla T4; 3 experiments × 3 seeds per dataset, early stopping on validation macro-F1 (patience 6), class-balanced BCE. Final model retrained on train + val for its best epoch count.

## Validation macro-F1 (mean ± std over seeds)

| Experiment | bot_iot | cic_ids2017 | unsw_nb15 |
|---|---|---|---|
| mlp_128_64 | 0.9688 ± 0.0085 | 0.9961 ± 0.0001 | 0.9157 ± 0.0019 |
| mlp_256_128_64 | 0.9644 ± 0.0044 | 0.9959 ± 0.0000 | 0.9193 ± 0.0016 |
| mlp_512_256 | 0.9588 ± 0.0045 | 0.9955 ± 0.0002 | 0.9177 ± 0.0012 |

## Test: MLP vs classical (tuned thresholds)

| Dataset | Classical | MLP | Classical F1 | MLP F1 | Δ F1 [95% CI] | MLP FPR | Classical FPR | McNemar p |
|---|---|---|---|---|---|---|---|---|
| bot_iot | random_forest | mlp_128_64 | 0.9978 | 0.9880 | -0.0098 [-0.0128, -0.0072] | 0.0146 | 0.0015 | 3.47e-11 |
| cic_ids2017 | hist_gb | mlp_128_64 | 0.9985 | 0.9943 | -0.0042 [-0.0045, -0.0038] | 0.0023 | 0.0005 | 1.63e-121 |
| unsw_nb15 | hist_gb | mlp_256_128_64 | 0.8544 | 0.8589 | +0.0045 [+0.0029, +0.0061] | 0.2793 | 0.2835 | 8.91e-08 |