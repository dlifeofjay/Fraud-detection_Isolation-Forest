# Bank Fraud Detection with Isolation Forest

Unsupervised anomaly detection on bank transaction data to surface suspicious debit activity — no labelled fraud data required.

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-IsolationForest-orange?logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-F37626?logo=jupyter)

---

## Overview

Traditional fraud detection relies on labelled examples of known fraud — a luxury most real-world datasets don't have. This project takes an **unsupervised approach**: using **Isolation Forest**, a tree-based anomaly detection algorithm, to isolate transactions that behave differently from the majority.

The analysis focuses exclusively on **debit transactions**, where fraud risk is highest, and engineers features that capture behavioural patterns at the account, device, merchant, and IP level.

---

## Project Files

| File | Description |
|------|-------------|
| **`Possible Bank Fraud(Old & Model Building).ipynb`** | Original notebook (earlier version) |
| **`Possible Bank Fraud (Updated).ipynb`** | **Main / Latest version** — contains full updated analysis including data quality assessment, improved feature engineering, risk scoring, same-day multiple transaction detection, and clearer conclusions. |
| `README.md` | This file |

> **Recommended**: Use **`Possible Bank Fraud (Updated).ipynb`** for the most complete and up-to-date work.

---

## Problem Statement

> *Can we detect potentially fraudulent bank transactions without any prior fraud labels, using only behavioural and contextual signals?*

Key signals investigated:
- High `LoginAttempts` (≥3)
- Multiple transactions on the same day
- Very short `TransactionDuration` for large amounts
- Unusual device/IP reuse
- Overdraft-like transactions (`TransactionAmount > AccountBalance`)

---

## Methodology

### 1. Exploratory Data Analysis
- Distribution analysis and correlation matrices
- Outlier detection using `LoginAttempts` and `Amount/Balance` ratio
- Behavioral analysis (same-day multiple withdrawals + high login attempts)

### 2. Data Quality Assessment
- Identified issues: inconsistent account balances, unrealistic long-term device/IP reuse
- Documented limitations and adjusted focus to more robust signals

### 3. Feature Engineering & Risk Scoring
- Temporal features (date, hour)
- Velocity features (transactions per day per account)
- Risk scoring combining multiple signals

### 4. Anomaly Detection
- Statistical analysis and rule-based flagging (as a complement to Isolation Forest in earlier versions)

---

## Tech Stack

- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `scipy.stats` (Welch’s t-test)
- Jupyter Notebook

---

## Quick Start

```bash
jupyter notebook "Possible Bank Fraud (Updated).ipynb"