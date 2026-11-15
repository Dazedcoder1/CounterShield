# Data

Raw and processed data are not stored in this repository. Module 1 downloads the datasets from Kaggle with `kagglehub`, using the `KAGGLE_API_TOKEN` Colab secret, and writes the harmonised files to `MyDrive/CounterShield/processed/`. The Kaggle handles are listed in the first code cell of Module 1.

| Dataset | Flows used | How Module 1 prepares it |
|---|---|---|
| BoT-IoT | 911,828 | A stratified sample of the full CSV release (73.4 M flows): at most 300,000 flows per attack category, random seed 42. All benign (9,543) and theft (1,587) flows are kept. |
| CIC-IDS2017 | 2,827,876 | All flows from the released CSV files after rows with NaN or infinite values are dropped. |
| UNSW-NB15 | 257,673 | The official training and test partitions, kept as they are. |

## Files here

- `provenance/provenance.json`: for each dataset, the source, version, download time and the SHA-256 hash of every file.
- `provenance/class_distribution.csv`: number of flows per split, attack family and class.

## Labels

Every dataset gets the same label columns:

- `y_binary`: 0 = benign, 1 = attack. This is the target used in all experiments.
- `y_class`: the dataset's own attack class, in lower-case snake_case.
- `y_family`: a coarse family shared across datasets: benign, ddos, dos, recon, brute_force, web_attack, botnet, exfiltration_theft, malware_backdoor, exploit or other.

## Original dataset papers

- N. Koroniotis, N. Moustafa, E. Sitnikova and B. Turnbull, "Towards the development of realistic botnet dataset in the Internet of Things for network forensic analytics: Bot-IoT dataset," *Future Generation Computer Systems*, vol. 100, pp. 779-796, 2019.
- I. Sharafaldin, A. H. Lashkari and A. A. Ghorbani, "Toward generating a new intrusion detection dataset and intrusion traffic characterization," in *Proc. ICISSP*, 2018, pp. 108-116.
- N. Moustafa and J. Slay, "UNSW-NB15: a comprehensive data set for network intrusion detection systems," in *Proc. MilCIS*, 2015.
