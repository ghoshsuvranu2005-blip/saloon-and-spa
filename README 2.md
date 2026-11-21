# 🖥️ Interactive Web Dashboard & Experimentation UI

The `frontend/` component provides an enterprise decision cockpit for visualizing A/B experiment outcomes, quasi-experimental DiD event studies, real-time power simulations, and transaction-level audit logs.

---

## 🎨 UI Design Architecture

* **Framework:** Pure Modern Vanilla JS (ES6+), HTML5, and CSS3
* **Visualization Engine:** Chart.js v4.4 (Canvas-accelerated rendering)
* **Design System:** Custom Dark-Mode Theme optimized for analytics density:
  - Deep Navy Slate Background (`#0b0f19`)
  - Elevated Card Panels (`#151c2c`, border `#222f47`)
  - Semantic Status Palette: Emerald Green (`#10b981`), Cyan Blue (`#38bdf8`), Amber (`#f59e0b`), Purple (`#a855f7`)
* **Responsive Layout:** CSS Grid and Flexbox adapting across 4K displays, laptops, and mobile screens.

---

## 🛠️ The 9 Interactive Dashboard Panels

### 1. Executive C-Suite Overview (`tab-overview`)
* **Live Decision Pill:** Pulsing status pill displaying **GO (ROLLOUT READY)**.
* **Top KPI Scorecard:** Displays Primary Metric lift (+10.09%), No-Show reduction (-36.09%), DiD causal policy lift (+8.18%), and CUPED duration savings (12.9 days).
* **Comparative Charts:** Side-by-side bar chart of RPV lift and line chart of DiD festive divergence.

### 2. A/B Experiment & SRM Diagnostics (`tab-abtest`)
* **Covariate Balance Table:** Displays Control vs Treatment means alongside Standardized Mean Differences (SMD < 0.10) for baseline spend, weekend share, walk-in ratio, master stylists, and service verticals.
* **SRM Diagnostic Card:** Displays assigned counts ($N_C=23,031$, $N_T=23,304$), $\chi^2 = 1.6085$, and $p = 0.2047$ confirming zero sample ratio mismatch.

### 3. DiD & Dynamic Event Study (`tab-did`)
* **Dynamic Event Study Chart:** Interactive Chart.js line plot displaying bi-weekly coefficients $\delta_{-6} \dots \delta_{+5}$.
* **Parallel Trends Inspection:** Visual proof that pre-treatment leads hover near zero, validating the quasi-experimental counterfactual.

### 4. Segment Winners & Losers (`tab-segments`)
* **Heterogeneous Treatment Effect Chart:** Horizontal bar chart highlighting subgroup gains across:
  - *Senior Stylists:* **+15.37%** (Top cross-selling performance)
  - *Hair Services:* **+14.55%**
  - *Skin & Facials:* **+14.23%**
  - *Residential Neighborhood Salons:* **+13.94%** (High community loyalty)
  - *Mall Outlets:* **+4.23%** ($p = 0.35$, muted due to walk-in footfall)

### 5. Interactive CUPED Simulator (`tab-cuped`)
* **Dynamic Correlation Slider:** Move the slider ($\rho \in [0.05, 0.85]$) to dynamically recalculate:
  - Variance reduction ($1 - \rho^2$)
  - Effective sample size ratio
  - Shortened experiment duration (weeks)
  - Total business days saved

### 6. Interactive Power & Sample Size Lab (`tab-power`)
* **Custom Inputs:** Adjust Baseline Mean RPV (₹), Standard Deviation, Target MDE (%), and Intra-Cluster Correlation (ICC).
* **Real-time Recalculation:** Instant asynchronous query to `/api/power/calculate` returning required sample size per arm, total visits, and cluster design effects.

### 7. Live SRM Calculator Tool (`tab-srm-tool`)
* **Custom Split Testing:** Enter arbitrary Control and Treatment observed counts with an expected split (e.g. 50/50, 60/40) to test for assignment anomalies with instant pass/fail alerts.

### 8. Transactional Appointment Explorer (`tab-explorer`)
* **Live Search & Filter:** Filter 5,000 appointment records by service category, A/B variant, or custom text query.
* **Real-time Pagination:** Fast AJAX pagination displaying raw vs cleaned status, dirty service strings, and realized spend.

### 9. Executive Decision Gate Configurator (`tab-decision-tool`)
* **Risk Policy Sliders:** Customize management criteria (Min RPV lift, Min No-Show reduction, Max allowable volume drop).
* **Automated Decision Engine:** Live query to `/api/decision/evaluate` returning a gate-by-gate pass/fail breakdown and **GO / EXTEND / NO-GO** recommendation.

---

## 🌐 How to Access the Live Dashboard
1. Ensure the backend server is running (`node server.js`).
2. Open your web browser at **`http://localhost:3000`**.
