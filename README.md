# 🔌 Backend REST API Engine & Microservice Architecture

The `backend/` component powers the analytical execution engine, computational endpoints, simulation controllers, and static file streaming services for the **Kongu Aura Salon Experimentation Platform**.

---

## 🏗️ Architecture & Technical Stack

* **Runtime:** Node.js (v18.x / v20.x / v24.x)
* **Design Pattern:** Zero-dependency, asynchronous event-driven HTTP REST microservice
* **Core Compute Modules:**
  - Analytical Power Analysis & Intra-Cluster Correlation (ICC) calculator
  - Chi-Square Goodness-of-Fit Sample Ratio Mismatch (SRM) diagnostic engine
  - CUPED optimal variance-reduction scaling engine ($\hat{\theta} = \frac{Cov(Y, X)}{Var(X)}$)
  - Executive Decision Gate policy evaluator
  - High-performance filter/search engine for transaction logs

---

## 🚀 Quickstart & Server Launch

From the repository root:
```bash
node server.js
```
The server binds to `0.0.0.0:3000` and displays:
```text
Enterprise Experimentation Backend is running at: http://localhost:3000
```

---

## 📡 REST API Endpoints Specification

### 1. System Health
* **Endpoint:** `GET /api/health`
* **Description:** Health check, process uptime, and loaded outlet registry count.
* **Response (200 OK):**
```json
{
  "status": "ok",
  "uptime": 245.8,
  "outlets": 22
}
```

### 2. Analytical Results Payload
* **Endpoint:** `GET /api/results`
* **Description:** Returns the comprehensive empirical payload containing A/B test results, DiD parameters, covariate balance, CUPED variance reduction, and segmentation metrics.

### 3. Live Sample Ratio Mismatch (SRM) Test
* **Endpoint:** `POST /api/srm/calculate`
* **Request Body:**
```json
{
  "control_count": 23031,
  "treatment_count": 23304,
  "ratio": 0.5
}
```
* **Response (200 OK):**
```json
{
  "nC": 23031,
  "nT": 23304,
  "total": 46335,
  "chiSq": 1.6085,
  "pVal": 0.2047,
  "passed": true,
  "verdict": "PASS (No Sample Ratio Mismatch)",
  "controlPct": 49.71,
  "treatmentPct": 50.29
}
```

### 4. Power Analysis & Sample Size Engine
* **Endpoint:** `POST /api/power/calculate`
* **Request Body:**
```json
{
  "mean": 2635.63,
  "sd": 4673.41,
  "mde_pct": 3.5,
  "alpha": 0.05,
  "power": 0.80,
  "icc": 0.012,
  "weekly_traffic": 7720
}
```
* **Response (200 OK):**
```json
{
  "delta": 92.25,
  "def": 18.39,
  "nPerArmRaw": 40291,
  "totalRaw": 80582,
  "totalClustered": 1481729,
  "weeksRaw": 5.98,
  "weeksClustered": 191.93
}
```

### 5. CUPED Variance Reducer
* **Endpoint:** `POST /api/cuped/calculate`
* **Request Body:**
```json
{
  "rho": 0.5535,
  "weeks": 6.0
}
```
* **Response (200 OK):**
```json
{
  "rho": 0.5535,
  "varReductionPct": 30.64,
  "sampleRatio": 0.6936,
  "shortenedWeeks": 4.16,
  "daysSaved": 12.9,
  "ciNarrowPct": 16.72
}
```

### 6. Transactional Appointment Explorer
* **Endpoint:** `GET /api/appointments?page=1&limit=20&category=Hair%20Services&variant=TREATMENT&search=APT`
* **Description:** Returns paginated, searchable appointments showing raw vs cleaned categories, disguised no-show attribution, and realized bill amounts.

### 7. File Streaming & Artifact Downloads
* `GET /download/notebook` &rarr; `coimbatore_salon_analysis.ipynb`
* `GET /download/script` &rarr; `coimbatore_salon_analysis.py`
* `GET /download/memo` &rarr; `DECISION_MEMO.md`
* `GET /download/design-doc` &rarr; `EXPERIMENT_DESIGN_DOCUMENT.md`
* `GET /download/threats` &rarr; `THREATS_TO_VALIDITY.md`
* `GET /api/export/csv` &rarr; CSV stream of 1,000+ cleaned transactions

---

## 🧪 Testing & Verification

Run the automated endpoint test suite:
```bash
node test_api.js
```
Expected output:
```text
HEALTH CHECK SUCCESS: { status: 'ok', uptime: ..., outlets: 22 }
SRM CHECK SUCCESS: { chiSq: 1.6085, pVal: 0.2047, passed: true }
CUPED CHECK SUCCESS: { varReductionPct: 30.64, daysSaved: 12.9 }
```
