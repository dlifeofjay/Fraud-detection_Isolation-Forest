# 🏦 Bank Fraud Detection with Isolation Forest

Unsupervised anomaly detection on bank transaction data to surface suspicious debit activity — no labelled fraud data required.

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-IsolationForest-orange?logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-F37626?logo=jupyter)

---

## 📋 Overview

Traditional fraud detection relies on labelled examples of known fraud — a luxury most real-world datasets don't have. This project takes an **unsupervised approach**: using **Isolation Forest**, a tree-based anomaly detection algorithm, to isolate transactions that behave differently from the majority.

The analysis focuses exclusively on **debit transactions**, where fraud risk is highest, and engineers features that capture behavioural patterns at the account, device, merchant, and IP level.

---

## 🔍 Problem Statement

> *Can we detect potentially fraudulent bank transactions without any prior fraud labels, using only behavioural and contextual signals?*

Key signals investigated:
- **Login attempts** — unusually high attempts before a transaction
- **Transaction duration** — suspiciously fast (< 1 min) high-frequency debit activity
- **IP address behaviour** — same IP linked to many transactions
- **Device & merchant frequency** — repeated device or merchant use per account
- **Time of day** — night/early morning transaction clustering

---

## 🧪 Methodology

### 1. Exploratory Data Analysis
- Distribution analysis of transaction amounts, durations, login attempts, account balances
- Segmentation of transactions by type, channel, location, and customer occupation
- Statistical significance testing (Welch's t-test) to validate suspicious vs. normal transaction splits

### 2. Feature Engineering
| Feature | Description |
|---|---|
| `TransactionMinute` | Transaction duration converted to minutes |
| `AccountTrans` | Count of transactions per account |
| `DeviceTrans` | Count of transactions per account–device pair |
| `IPTrans` | Count of transactions per account–IP address pair |
| `TransactionYear/Month/Day` | Temporal features from transaction timestamp |

### 3. Anomaly Detection — Isolation Forest
- Applied to debit transactions after one-hot encoding categorical features
- `contamination=0.1` (assumes ~10% of transactions are anomalous)
- Anomaly scores extracted via `decision_function` for ranking

### 4. Post-hoc Segment Analysis
- Aggregate comparison (median/mode) of anomalous vs. normal groups
- Visualisations: transaction amount distributions, location/occupation/channel breakdowns, scatter plots across key feature pairs

---

## 📁 Project Structure

```
Isolation_Forest/
├── Possible Bank Fraud.ipynb   # Full analysis: EDA → feature engineering → model → insights
└── README.md
```

---

## 🚀 Quick Start

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

### Run the Notebook
```bash
jupyter notebook "Possible Bank Fraud.ipynb"
```

> **Note:** Place your dataset (`bank_transactions_data_2_augmented_clean_2.csv`) in the same directory as the notebook before running.

---

## 📊 Key Findings

- Transactions with **≥ 3 login attempts** and completed in **< 1 minute** showed statistically significantly lower transaction amounts (p ≈ 0.000004), suggesting automated/scripted activity
- IP addresses with high login frequencies and very short transaction durations were flagged as potentially automated
- The Isolation Forest model segmented ~10% of debit transactions as anomalous, with distinct patterns in device reuse, IP frequency, and account transaction counts

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| `pandas` / `numpy` | Data manipulation & feature engineering |
| `matplotlib` / `seaborn` | Visualisation |
| `scipy.stats` | Welch's t-test for statistical validation |
| `sklearn.ensemble.IsolationForest` | Unsupervised anomaly detection |
| `sklearn.preprocessing.OneHotEncoder` | Categorical feature encoding |

---

## 👨‍💻 Author

**Jubril Ifekoya** — Data Scientist & ML Engineer