# Hotfoot Hackathon – Macro UPI Transaction Anomaly Analysis

## Problem Statement Overview

India’s digital payments ecosystem, especially **Unified Payments Interface (UPI)**, has witnessed rapid growth in transaction **volume**, **value**, and **institutional participation** (banks and apps). While this growth is generally upward trending, the system can exhibit **unusual macro-level behaviors** such as sudden spikes, drops, or shifts in market share that may indicate:

- Operational or business risks  
- Structural or systemic changes  
- Data quality or reporting artefacts  

The objective of this project is to build an **end-to-end analytical solution** that:

- Models *normal system-wide UPI behavior* using historical data  
- Detects *statistically significant deviations* from expected trends  
- Explains these anomalies using **domain-grounded reasoning**, without performing individual transaction-level fraud detection  

The analysis focuses strictly on **aggregated, macro-level trends** in UPI data.

---

## Objectives of the Solution

The solution aims to:

- Model normal UPI behavior in terms of:
  - Growth rates
  - Seasonality
  - Distribution and concentration across banks and apps
- Detect and flag anomalies such as:
  - Sudden surges or drops in total UPI volume/value
  - Abrupt or repeated jumps in a bank’s/app’s market share
  - Periods where system growth deviates from expected macro or seasonal trends
- Classify each detected anomaly as:
  - A potential **business/operational risk**, or
  - A **data-quality / reporting artefact**
- Provide **clear explanatory narratives** for each anomaly using only publicly available, aggregated data


**Problem Statement Document**  
The official hackathon problem statement can be accessed here:  
[Open Problem Statement PDF](./problem_statement.pdf)
---

## Data Source

**Important**:  
All datasets used in this repository have been collected **strictly and exclusively** from the **official government sources referenced in the problem statement PDF**.

The data originates from the **Ministry of Statistics and Programme Implementation (MOSPI)** compendium documents and related official portals, as mandated in the problem statement.

The **problem statement PDF included in this repository** clearly outlines the allowed data sources and evaluation criteria.

No external, private, scraped, or transaction-level data has been used.

The solution focuses on identifying **systemic risks, operational signals, or data-quality artefacts**, rather than fraud at the transaction level.

---

## Repository Structure and Explanation

```text
Hotfoot/
│
├── data/
│   ├── Daily_Usage.csv       # Daily-level UPI usage statistics (Short-term trends)
│   └── Month_Wise.csv        # Monthly aggregated UPI data (Growth & Seasonality)
│
├── notebooks/                # Jupyter notebooks for EDA and hypothesis testing
│   ├── 00_data_collection_and_preparation.ipynb
│   ├── 01_exploratory_and_baseline_analysis.ipynb
│   ├── 02_system_metrics_and_anomaly_detection.ipynb
│   └── 03_joint_inference_and_interpretation.ipynb
│
├── figures/                  # Generated plots, charts, and visualizations
│
├── outputs/                  # Final anomaly reports and summary tables
│
├── problem_statement.pdf     # Official project objectives and constraints
└── README.md                 # Project documentation
```
Each folder represents a distinct stage in the analytical pipeline.

---

## Data Folder (`data/`)

### `Daily_Usage.csv`
- Contains daily aggregated UPI metrics
- Used for:
  - Short-term trend analysis
  - Volatility measurement
  - Daily-level anomaly detection

### `Month_Wise.csv`
- Contains month-wise aggregated UPI data
- Used for:
  - Growth rate modeling
  - Seasonality analysis
  - Market share and concentration analysis
  - Long-term anomaly detection

---

## Notebooks (`notebooks/`)

This folder contains Jupyter notebooks that implement the **complete analytical pipeline**, executed in sequence.

### **Notebook 00 – Data Collection and Preparation**
**(Foundational Notebook)**

- Collects raw data strictly from the sources allowed in the problem statement PDF  
- Cleans, validates, and standardizes raw tables  
- Handles missing values, formatting issues, and temporal alignment  
- Constructs the final **daily-level and month-wise datasets** used across the project  
- Outputs clean datasets to the `data/` folder  

> All downstream analysis depends on the datasets created in this notebook.

---

### Notebook 01 – Exploratory and Baseline Analysis

- Loads prepared datasets from `data/`
- Performs exploratory data analysis (EDA)
- Analyzes instrument-level and system-level dominance
- Visualizes daily and monthly UPI trends
- Computes growth rates and seasonal patterns
- Establishes statistical baselines for normal system behavior

Visual outputs from this notebook are saved in the `figures/` folder.

---

### Notebook 02 – System Metrics and Anomaly Detection

- Computes system-wide growth, volatility, and stability metrics
- Analyzes market concentration (HHI, top-N share sensitivity)
- Studies bank/app participation dynamics
- Applies rolling statistics and regime detection methods
- Detects anomalies using statistical thresholds and structural deviations
- Classifies anomalies at the system and entity level

Structured outputs from this notebook are saved in the `outputs/` folder.

---

### Notebook 03 – Joint Inference and Interpretation

- Integrates signals from all previous analyses
- Produces consolidated system-level interpretations
- Classifies each anomalous period as:
  - A potential business or operational risk signal, or
  - A likely data-quality or reporting artefact
- Generates a final joint inference table for decision-making

---

## Figures (`figures/`)

This folder contains all plots and visualizations generated during the analysis, including:

- Instrument dominance and composition charts  
- Monthly and daily UPI volume trends  
- Growth rate stability and volatility plots  
- Z-score and statistical baseline visualizations  
- Time-series decomposition outputs  
- Market share evolution and sensitivity plots  

These figures provide visual justification for all detected anomalies.

---

## Outputs (`outputs/`)

This folder stores all final analytical outputs in CSV format, including:

- Monthly system-level metrics and growth indicators  
- Market concentration and dominance measures  
- Volatility regimes and predictability indices  
- Bank/app entry and exit dynamics  
- Detected anomaly tables with classification labels  
- Final joint inference dataset  

These outputs form the **decision-support layer** of the solution.

---

## How to Use This Repository

1. Read `problem_statement.pdf` to understand scope and constraints  
2. Run **Notebook 00** to construct clean datasets  
3. Execute notebooks in order:
   - Notebook 01 → Baseline & EDA  
   - Notebook 02 → Metrics & Anomaly Detection  
   - Notebook 03 → Final Inference  
4. Review generated figures in `figures/`  
5. Analyze final results in `outputs/`  

---

## Design Principles Followed

- Macro-level analysis only  
- No transaction-level or user-level inference  
- Explainable, statistically grounded methods  
- Reproducible and auditable workflow  
- Strict adherence to hackathon data constraints  

---

## Conclusion

This repository presents a complete, transparent, and policy-compliant analytical framework for detecting and explaining macro-level anomalies in India’s UPI ecosystem. The approach combines statistical rigor, economic intuition, and clear interpretability, making it suitable for systemic risk monitoring and policy-level analysis.

---
