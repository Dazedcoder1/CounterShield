# Module 2 — Data cleaning & audit summary

Run: 2026-11-14T13:27:20+00:00. Settings: drop conflicting duplicates = True; deduplicate UNSW-NB15 test = False.

| Dataset | Rows in | Rows out | Removed | Exact dups | Conflicting | Features | Attack rate | Classes |
|---|---|---|---|---|---|---|---|---|
| bot_iot | 911,828 | 903,922 | 0.87% | 5,897 | 2,009 | 20 | 0.990 | 5 |
| cic_ids2017 | 2,827,876 | 2,198,595 | 22.25% | 546,577 | 82,704 | 69 | 0.153 | 15 |
| unsw_nb15 | 257,673 | 181,600 | 29.52% | 45,545 | 30,528 | 42 | 0.512 | 10 |

## Flags from the label audit

- **cic_ids2017**: classes with < 100 rows: infiltration (36), web_attack_sql_injection (21), heartbleed (11)

UNSW-NB15: 5,881 official-test rows (7.1%) have identical features in train.