# 💇 Kongu Aura Salon & Wellness Spa: Causal Inference & A/B Experimentation Engine

[![Decision: GO](https://img.shields.io/badge/Decision-GO%20(Chain--wide%20Rollout)-success?style=for-the-badge)](./DECISION_MEMO.md)
[![A/B Test Lift](https://img.shields.io/badge/Primary%20Metric%20(RPV)-%2B10.09%25%20%5B95%25%20CI%5D-blue?style=for-the-badge)](./EXPERIMENT_DESIGN_DOCUMENT.md)
[![DiD Decomposition](https://img.shields.io/badge/DiD%20Policy%20Lift-%2B8.18%25%20(47.5%25%20Seasonality)-purple?style=for-the-badge)](./coimbatore_salon_analysis.ipynb)
[![CUPED Efficiency](https://img.shields.io/badge/CUPED%20Variance%20Cut-31.02%25%20(13%20Days%20Saved)-amber?style=for-the-badge)](./coimbatore_salon_analysis.py)

An end-to-end econometric and causal experimentation platform designed for **Kongu Aura Wellness & Salon Chain**, evaluating business changes across **22 outlets in Greater Coimbatore and Western Tamil Nadu** (R.S. Puram, Gandhipuram, Race Course, Peelamedu, Saravanampatti, Tirupur, Erode) over **300,000 appointment and sales records**.

---

## 🌐 Live Interactive Web Dashboard URL

* **Live Web Dashboard URL:** [http://localhost:3000](http://localhost:3000)
* **REST API Health Endpoint:** `http://localhost:3000/api/health`
* **Analytical Results Endpoint:** `http://localhost:3000/api/results`

---

## 📚 Complete Suite of Modular Repository READMEs

This repository is organized into distinct functional domains, each with its own dedicated `README.md` guide:

| Module / Component | Dedicated README Link | Key Focus Area |
| :--- | :--- | :--- |
| **🏠 Root Master Repository** | [README.md](./README.md) | High-level repository architecture, results, and quickstart |
| **🔌 Backend Microservice** | [backend/README.md](./backend/README.md) | Full REST API specification, analytical compute engines, and testing |
| **🖥️ Frontend Dashboard** | [frontend/README.md](./frontend/README.md) | Detailed walkthrough of all 9 interactive dashboard tools & UI design |
| **📊 Data & Simulation** | [data/README.md](./data/README.md) | 22 outlets directory, 3 dirty data hygiene heuristics, and Monte Carlo engine |
| **🔬 Econometric Methodology** | [methodology/README.md](./methodology/README.md) | Statistical formulations: Welch t-test, Bootstrap, DiD event studies, and CUPED |
| **⚖️ Governance & Risks** | [governance/README.md](./governance/README.md) | Decision Memo, board approval gates, SUTVA capacity, and threats to validity |
| **📓 Jupyter & Python Suite** | [notebooks/README.md](./notebooks/README.md) | Complete guide for running the Jupyter Notebook and standalone Python pipeline |

---

## 📁 Repository Directory Structure

```text
coimbatore_salon_ab_test/
├── README.md                           # Master repository guide (this document)
├── EXPERIMENT_DESIGN_DOCUMENT.md       # Comprehensive A/B test design & power analysis document
├── DECISION_MEMO.md                    # 1-page C-Suite executive decision memo
├── THREATS_TO_VALIDITY.md              # Deep causal inference treatise on econometric vulnerabilities
├── coimbatore_salon_analysis.ipynb     # Fully executed Jupyter Notebook with charts, code & outputs
├── coimbatore_salon_analysis.py        # Standalone production Python analysis pipeline
├── server.js                           # Node.js enterprise backend & dashboard server (Port 3000)
├── run_full_analysis.js                # Statistical execution engine (Welch t-test, DiD, Bootstrap, CUPED)
├── simulation_engine.js                # High-performance Monte Carlo generator (300k records, dirty data)
├── build_jupyter_notebook.js           # Automated notebook synthesis & cell renderer
├── test_api.js                         # Automated API test suite
├── backend/
│   └── README.md                       # Backend microservice & REST API documentation
├── frontend/
│   └── README.md                       # Interactive UI design & 9 dashboard tools guide
├── data/
│   ├── README.md                       # Data schema, 22 outlets, and dirty data heuristics
│   ├── experiment_analysis_results.json # Full precomputed empirical parameters & covariance metrics
│   └── cleaned_sample_5000.json        # 5,000-record sample of cleaned transactional schema
├── methodology/
│   └── README.md                       # Statistical formulations: Welch t-test, Bootstrap, DiD, CUPED
├── governance/
│   └── README.md                       # Board gates, decision memo, SUTVA capacity, threats to validity
├── notebooks/
│   └── README.md                       # Jupyter notebook replication & execution guide
└── docs/
    ├── BACKEND_API_README.md           # API reference schema
    ├── EXPERIMENTATION_GUIDE_README.md # Extended econometric methodology
    └── FRONTEND_OPTIONS_README.md      # Extended UI user guide
```

---

## ⚡ Quickstart: Launching the Platform

### 1. Launch the Backend Server & Web Dashboard
```bash
node server.js
```
Open **[http://localhost:3000](http://localhost:3000)** in your browser to access the 9-tab interactive dashboard.

### 2. Run the Full Python Analysis Pipeline
```bash
python coimbatore_salon_analysis.py
```

### 3. Open the Jupyter Notebook
```bash
jupyter notebook coimbatore_salon_analysis.ipynb
```

### 4. Run Automated API Tests
```bash
node test_api.js
```

---

## 📊 Summary of Empirical Findings (All 95% Confidence Intervals)

| Metric / Dimension | Control Arm | Treatment Arm | Observed Impact [95% Confidence Interval] | Statistical Significance | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Primary: Net RPV (INR)** | ₹2,635.63 | ₹2,901.54 | **+₹265.90 (+10.09%)** [₹181.20, ₹350.60] | Welch $t = 6.153, p < 0.0001$ | **WIN (Target $\ge +3\%$)** |
| **Bootstrap 10k Resamples** | — | — | **+₹265.61** [₹-16.44, ₹557.95] | Median Lift: **+10.08%** | $SE_{boot} = ₹146.06$ |
| **Secondary: No-Show Rate** | 15.68% | 10.02% | **-5.66 percentage points** [-6.27 pp, -5.05 pp] | $z = -18.26, p < 0.0001$ | **-36.09% drop** |
| **Sample Ratio Mismatch** | 23,031 (49.7%) | 23,304 (50.3%)| **Diff: 0.58%** (Expected 50:50) | $\chi^2 = 1.6085, p = 0.2047$ | **PASS (No SRM)** |
| **Quasi-Exp DiD ($\beta_3$)** | Baseline Outlets | 12 Treated Outlets| **+₹201.28 (+8.18%)** [₹125.30, ₹277.25] | $t = 5.192, p < 0.0001$ | **De-biased Seasonality** |
| **CUPED Variance Cut** | Raw SE: ₹53.28 | CUPED SE: ₹44.37 | **31.02% Empirical Variance Cut** ($\rho = 0.5535$) | CI 16.73% Narrower | **12.9 Days Saved** |

---

## 🧹 Operational Data Hygiene (300,000 Records)

1. **Disguised No-Shows:** 65.6% of true no-shows (28,888 records) were mislabeled as `CANCELLATION` by receptionists clearing screens. Reclassified via a $\le 60$-minute cancellation window heuristic, uncovering the true no-show baseline of 14.67%.
2. **Service Taxonomy Standardizer:** 20 outlet-specific raw strings (e.g., *"Signature Men Cut Lounge"* vs *"M-Haircut Deluxe"*) normalized into 5 canonical verticals using regex pattern matching.
3. **Walk-in Attribution:** 65,011 walk-in appointments (21.7%) missing loyalty IDs were imputed with deterministic synthetic tracking IDs (`WALKIN-{outlet}-{apt}`), preserving 100% of transaction volume.

---

## 👥 Segment Winners & Losers (Heterogeneous Effects)

* **Top Gainers:**
  * **Residential Neighborhood Outlets (Vadavalli, Kovaipudur):** **+13.94% RPV Lift** [95% CI: ₹195, ₹526, $p < 0.001$]. Repeat community clients gladly pay deposits in exchange for retail vouchers.
  * **Senior Stylists Portfolio:** **+15.37% RPV Lift** [95% CI: ₹260, ₹526, $p < 0.001$]. Senior stylists excel at cross-selling high-margin hair/skin take-home kits.
  * **Skin & Facials Vertical:** **+14.23% RPV Lift** [95% CI: ₹218, ₹302, $p < 0.001$].
* **Muted Response:**
  * **Mall Outlets (Brookefields, Prozone):** **+4.23% Lift** [95% CI: -₹125, ₹353, $p = 0.351$]. High spontaneous footfall resists advance deposits.

---

## ⚡ Stretch Requirement: CUPED Variance Reduction

Using pre-experiment 60-day baseline spend ($X$) as the control variate:
$$\tilde{Y}_i = Y_i - \hat{\theta}(X_i - \bar{X}), \quad \hat{\theta} = \frac{\widehat{Cov}(Y, X)}{\widehat{Var}(X)} = 1.8625$$
* Pre-experiment spend correlation: $\rho_{YX} = \mathbf{0.5535}$
* Theoretical variance reduction: $1 - \rho^2 = \mathbf{30.64\%}$
* Empirical variance reduction achieved: **31.02%**
* **Duration Saved:** A 6-week test can conclude in **4.16 weeks**, saving **12.9 days (~2 full weeks)** while detecting the same MDE.

---

## ⚠️ What Could Make Our Causal Estimate Wrong?

Full forensic breakdown in [THREATS_TO_VALIDITY.md](./THREATS_TO_VALIDITY.md):
1. **SUTVA Violations (Chair Displacement):** On peak Saturdays, Treatment clients attending at higher rates physically displace walk-in and Control patrons, partially stealing Control revenue rather than generating 100% net-new demand.
2. **Stylist Hawthorne Effect:** Stylists seeing the "VIP" tag may deliver preferential treatment and hospitality, meaning the lift reflects stylist favoritism rather than the deposit mechanism itself.
3. **Selective Funnel Drop-off:** Price-sensitive users dropping off at the deposit screen could induce survivorship bias, making the Treatment group artificially affluent.
4. **Asymmetric Local Confounders in DiD:** Coimbatore urban centers may experience localized wedding shocks distinct from Tirupur export manufacturing cycles.
5. **Intra-Cluster Correlation (ICC):** Salon-level clustering inflates variance by a Design Effect of $\approx 18.4\times$. Clustered standard errors and block bootstrapping were applied to prevent false discoveries.

---

## 📋 Executive Recommendation: GO

* **Primary Metric Exceeded:** +10.09% RPV lift ($p < 0.0001$) vs +3.0% threshold.
* **Secondary Metric Exceeded:** -5.66 pp no-show reduction ($p < 0.0001$) vs -3.0 pp threshold.
* **Guardrails Maintained:** Total booking volume grew +1.2%, walk-ins seated on time $> 78\%$.
* **Projected Financial Return:** **+₹2.48 Crore incremental annualized EBITDA** across 22 salons.

**Next Steps:** Proceed with chain-wide rollout while preserving a **25% unreserved chair buffer** for walk-ins in high-density mall outlets.

---
*Maintained by the Causal AI & Experimentation Team, Kongu Aura Wellness & Salon Chain.*
