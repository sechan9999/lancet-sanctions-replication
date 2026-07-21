# Lancet Global Health (2025) Sanctions Mortality Replication & Streamlit Dashboard

This repository contains an independent replication study and interactive Streamlit web dashboard for the research paper:

> **Rodríguez, F., Rendón, R., & Weisbrot, M. (2025).** 
> *"Effects of international sanctions on age-specific mortality: a cross-national panel data analysis."*  
> **Lancet Global Health**, 13(9), e1358–e1366. DOI: [10.1016/S2214-109X(25)00189-5](https://doi.org/10.1016/S2214-109X(25)00189-5)
> 
> https://sechan9999.github.io/lancet-sanctions-replication/

---

## 📌 Features & Objectives

1. **Interactive Streamlit Web Dashboard (`app.py`)**: https://lancet.streamlit.app/
   - Live Monte Carlo simulation engine ($N=100 - 5000$) with custom confidence bounds.
   - Interactive Plotly visualizations for age-specific mortality effects and Panel OLS parameters.
   - Multi-decadal scenario projection calculator (evaluating claims like ~38 million deaths over 50 years).
   - Country panel data explorer.

2. **Standalone Command-Line Replication (`monte_carlo_sanctions.py`)**:
   - Automated two-way fixed effects (Country & Year FE) panel regression and $N=1000$ uncertainty simulation.

---

## 📁 Repository Structure

```
.
├── app.py                     # Streamlit web dashboard application
├── monte_carlo_sanctions.py   # Standalone Python replication script
├── sanctions_dashboard.html   # HTML5 static dashboard template
├── requirements.txt           # Python dependencies (Streamlit, Plotly, Pandas, NumPy)
├── README.md                  # Project documentation and replication guide
└── .gitignore                 # Git ignore rules for data binaries and temporary files
```

---

## 📊 Dataset Requirements

The primary datasets can be downloaded from the official Harvard Dataverse repository:
- **Dataverse DOI**: [doi:10.7910/DVN/ZJSHU4](https://doi.org/10.7910/DVN/ZJSHU4)

Place the following files in the project root directory:
1. `mortality1_r-1.dta`: Country-year panel dataset (1971–2021) containing sanction indicators and mortality rates.
2. `un_single_age_life_t.dta`: UN World Population Prospects single-age life tables.

*(Note: The Streamlit app includes pre-calculated fallback parameters if `.dta` files are not placed locally).*

---

## 🚀 Quick Start & Local Run

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Launch Streamlit Web Dashboard
```bash
streamlit run app.py
```
Access the dashboard at `http://localhost:8501`.

### 3. Run Command-Line Replication Script
```bash
python monte_carlo_sanctions.py
```

---

## ☁️ Deployment

### Streamlit Community Cloud
1. Fork / push this repository to GitHub (`sechan9999/lancet-sanctions-replication`).
2. Log into [share.streamlit.io](https://share.streamlit.io/).
3. Select this repository and set Main file path to `app.py`.

---

## 📄 License
This repository is released under the MIT License.
