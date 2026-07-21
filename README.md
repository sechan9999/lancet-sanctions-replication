# Lancet Global Health (2025) Sanctions Mortality Replication & Dashboard

This repository contains an independent replication study and interactive visualization dashboard for the research paper:

> **Rodríguez, F., Rendón, R., & Weisbrot, M. (2025).**  
> *"Effects of international sanctions on age-specific mortality: a cross-national panel data analysis."*  
> **Lancet Global Health**, 13(9), e1358–e1366. DOI: [10.1016/S2214-109X(25)00189-5](https://doi.org/10.1016/S2214-109X(25)00189-5)

---

## 📌 Overview & Objectives

1. **Replication of Panel Regressions & Monte Carlo Simulations**:
   Re-estimate two-way fixed effects (Country and Year FE) panel regression models across 6 age groups (`0-1`, `1-5`, `5-10`, `10-15`, `15-60`, `60-80`) and perform $N=1000$ Monte Carlo simulations to calculate annual excess mortality and 95% confidence intervals.

2. **Empirical Evaluation of Public Claims**:
   Evaluate public assertions (e.g., statements citing ~38 million deaths over 50 years due to economic sanctions) against the statistical confidence intervals derived from empirical panel data.

3. **Interactive Visualization Dashboard**:
   Provide a standalone, client-side interactive web dashboard (`sanctions_dashboard.html`) to explore excess mortality estimates, age-specific breakdowns, and cumulative projection scenarios.

---

## 📁 Repository Structure

```
.
├── monte_carlo_sanctions.py   # Self-contained Python script for PanelOLS & Monte Carlo simulation
├── sanctions_dashboard.html   # Interactive web dashboard (HTML5 / Vanilla JS / CSS)
├── requirements.txt           # Python dependency specifications
├── README.md                  # Project documentation and replication guide
└── .gitignore                 # Git ignore rules for data binaries and temporary files
```

---

## 📊 Dataset Requirements

The primary datasets must be downloaded from the official Harvard Dataverse repository:
- **Dataverse DOI**: [doi:10.7910/DVN/ZJSHU4](https://doi.org/10.7910/DVN/ZJSHU4)

Place the following files in the project root directory:
1. `mortality1_r-1.dta`: Country-year panel dataset (1971–2021) containing sanction indicators, log age-specific mortality rates, and socio-economic controls.
2. `un_single_age_life_t.dta`: UN World Population Prospects single-age life tables containing population numbers and total deaths.

*Note: Large `.dta` files are excluded from Git tracking via `.gitignore`.*

---

## 🚀 Quick Start & Reproduction

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Run Monte Carlo Simulation
```bash
python monte_carlo_sanctions.py
```

### 3. Launch Interactive Dashboard
Open `sanctions_dashboard.html` directly in any web browser, or serve locally:
```bash
python -m http.server 8000
```
Then navigate to `http://localhost:8000/sanctions_dashboard.html`.

---

## 🔍 Key Empirical Findings

| Metric | Published Lancet Study | Replicated Panel OLS + Monte Carlo |
| :--- | :---: | :---: |
| **Annual Excess Deaths (Mean)** | ~564,258 | ~801,800 (Unweighted) / ~619,391 (Controlled) |
| **95% Confidence Interval** | [367,838 – 760,677] | [564,529 – 1,029,666] |
| **50-Year Extrapolation (Mean)** | ~28.2 Million | ~31.0 – 40.1 Million |
| **50-Year Extrapolation (CI Upper Bound)** | **~38.0 Million** | **~42.7 – 51.5 Million** |

### Critical Takeaway
- Extrapolating the **upper bound** (95% CI upper limit) over 50 years yields ~38 million deaths, matching widely cited public commentary.
- Citing the upper statistical limit as a definitive point estimate presents a conservative upper-bound scenario rather than the central statistical expectation.

---

## 📄 License
This repository is released under the MIT License.
