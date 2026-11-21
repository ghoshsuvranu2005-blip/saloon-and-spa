# 📓 Jupyter Notebooks & Python Analytical Suite

The `notebooks/` directory contains the executable Jupyter Notebook and Python pipelines for interactive replication of all statistical, econometric, and causal inference modeling for **Kongu Aura Wellness & Salon Chain**.

---

## 📁 Files in this Suite

| File | Type | Description |
| :--- | :--- | :--- |
| `coimbatore_salon_analysis.ipynb` | Jupyter Notebook | Complete, pre-executed notebook with interactive charts, tables, and cell narratives. |
| `coimbatore_salon_analysis.py` | Python Script | Standalone, headless Python production pipeline with zero GUI dependencies. |
| `build_jupyter_notebook.js` | Node.js Generator | Automated synthesizer that builds the `.ipynb` file from empirical simulation payloads. |

---

## 🚀 Running the Notebook

### 1. Launch with JupyterLab / Jupyter Notebook
```bash
jupyter notebook coimbatore_salon_analysis.ipynb
```
or inside VS Code, simply open `coimbatore_salon_analysis.ipynb` and select any Python 3.9+ kernel.

### 2. Run Headless via Python
```bash
python coimbatore_salon_analysis.py
```

---

## 🧪 Notebook Cell Structure & Workflow

1. **Cell 1: Environment & Setup** &mdash; Imports `numpy`, `pandas`, `scipy.stats`, and loads empirical payloads.
2. **Cell 2: Dirty Data Hygiene Audit** &mdash; Resolves disguised no-shows (65.6% mislabeled), standardizes service taxonomies, and attributes walk-ins.
3. **Cell 3: SRM Diagnostic & Covariate Balance** &mdash; Runs Pearson $\chi^2$ goodness-of-fit and computes Standardized Mean Differences (SMD < 0.10).
4. **Cell 4: A/B Test Treatment Estimation** &mdash; Welch's t-test and 10,000-resample non-parametric bootstrap on Primary RPV and No-Show rate.
5. **Cell 5: Difference-in-Differences (DiD)** &mdash; 2x2 seasonal decomposition of Q3 WhatsApp rollout vs 10 regional control salons.
6. **Cell 6: Parallel Trends Event Study** &mdash; 12-window dynamic leads and lags testing identification assumptions.
7. **Cell 7: Heterogeneous Subgroup Segmentation** &mdash; Identifies segment winners (Senior stylists, Residential outlets) and neutral responders (Malls).
8. **Cell 8: CUPED Variance Reduction** &mdash; Computes optimal $\hat{\theta}$, variance reduction ($31.02\%$), and duration savings (12.9 days).
9. **Cell 9: Executive Recommendation** &mdash; Evaluates board criteria and renders the formal **GO** decision.
