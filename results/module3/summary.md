# Module 3 — Preprocessing & splits summary

Scaler: quantile; one-hot cap 20; seed 42. All preprocessors fitted on the training split only.

| Dataset | Train | Val | Test | Input features | Model features | Attack rate (train) | Train/test identical rows |
|---|---|---|---|---|---|---|---|
| bot_iot | 632,744 | 135,589 | 135,589 | 20 | 46 | 0.990 | 3 (0.0%) |
| cic_ids2017 | 1,539,015 | 329,790 | 329,790 | 69 | 69 | 0.153 | 44 (0.01%) |
| unsw_nb15 | 84,377 | 14,891 | 82,332 | 42 | 81 | 0.480 | 5,162 (6.27%) |