# 🔬 Econometric Methodology & Causal Inference Guide

The `methodology/` component documents the mathematical and statistical foundations underpinning our A/B test evaluation, Difference-in-Differences quasi-experiment, and CUPED variance reduction.

---

## 1. Primary Metric Formulation & Identification

### Primary Metric: Net Revenue Per Visit (RPV, INR)
$$\mathbb{E}[RPV] = (1 - P_{noshow}) \cdot \mathbb{E}[Spend \mid Attended]$$

* **Why RPV Over Retention:** 60-day retention takes 2–3 months to observe, delaying decisions.
* **Why RPV Over No-Show Rate:** Optimizing for no-show reduction alone could look "improved" even if deposit friction causes a drastic collapse in total bookings.
* **The Advantage:** RPV combines attendance realization and retail voucher upsell into a single financial metric. A missed appointment records ₹0 spend, naturally penalizing no-shows in the expectation.

---

## 2. Statistical Testing Suite

### 2.1 Sample Ratio Mismatch (SRM) Test
$$\chi^2 = \sum_{j \in \{C, T\}} \frac{(O_j - E_j)^2}{E_j} \sim \chi^2(1)$$
* $N_C = 23,031$ (49.71%), $N_T = 23,304$ (50.29%)
* $\chi^2 = 1.6085 \implies \mathbf{p = 0.2047 > 0.01}$ (**PASS &mdash; No SRM**)

### 2.2 Covariate Balance (Standardized Mean Difference)
$$SMD = \frac{|\bar{X}_T - \bar{X}_C|}{\sqrt{\frac{s_T^2 + s_C^2}{2}}}$$
All baseline features exhibit $SMD < 0.035 \ll 0.10$, confirming pristine balance across treatment and control arms.

### 2.3 Welch's Two-Sample t-Test (Unequal Variances)
$$t = \frac{\bar{Y}_T - \bar{Y}_C}{\sqrt{\frac{s_T^2}{N_T} + \frac{s_C^2}{N_C}}} = 6.153 \implies \mathbf{p < 0.0001}$$
* Control Mean: ₹2,635.63 ($s = ₹4,673.41$)
* Treatment Mean: ₹2,901.54 ($s = ₹4,628.01$)
* Absolute Lift: **+₹265.90** [95% CI: ₹181.20, ₹350.60]
* Relative Lift: **+10.09%** [95% CI: +6.88%, +13.30%]

### 2.4 Non-Parametric Bootstrap (10,000 Resamples)
* 10,000 empirical resamples: Median lift = **+₹265.61**, $SE_{boot} = ₹146.06$.

---

## 3. Difference-in-Differences (DiD) Quasi-Experiment

### 3.1 Econometric Specification
$$Y_{ist} = \beta_0 + \beta_1 Treat_s + \beta_2 Post_t + \beta_3 (Treat_s \times Post_t) + \mathbf{X}_{ist}'\gamma + \varepsilon_{ist}$$
Where:
* $Treat_s$: 12 treated Coimbatore urban salons vs 10 comparison salons (Greater Kovai, Tirupur, Erode).
* $Post_t$: Q3 (Weeks 27–39) vs Pre-period Q1–Q2 (Weeks 1–26).
* $\beta_3$: True Average Treatment Effect on the Treated (ATT).

### 3.2 Seasonal Decomposition
$$\text{Raw Observed Jump in Treated Salons: } \Delta Y_T = +₹385.14 \text{ (+15.66\%) [Management Claim]}$$
$$\text{Regional Seasonal Surge in Control Salons: } \Delta Y_C = +₹183.86 \text{ (+7.44\%) [Aadi/Aavani Festive Tailwind]}$$
$$\text{True Causal DiD Effect: } \hat{\beta}_3 = (+₹385.14) - (+₹183.86) = \mathbf{+₹201.28 \text{ [95\% CI: +₹125.30, +₹277.25]}}$$
$$\text{True Policy Lift} = \mathbf{+8.18\% \text{ [95\% CI: +5.09\%, +11.27\%]}} \quad (t = 5.192, p < 0.0001)$$
**Crucial Finding:** Nearly half (47.5%) of the raw revenue surge was general festive seasonality.

### 3.3 Dynamic 12-Window Event Study
$$Y_{ist} = \sum_{k = -6, k \ne -1}^{+5} \delta_k (Treat_s \times \mathbb{I}(t = k)) + \theta_s + \lambda_t + \varepsilon_{ist}$$
Pre-treatment leads $\delta_{-6} \dots \delta_{-2}$ hover around zero ($p > 0.05$), validating that treated and control salons shared common baseline trajectories.

---

## 4. CUPED Variance Reduction

$$\tilde{Y}_i = Y_i - \hat{\theta}(X_i - \bar{X}), \quad \hat{\theta} = \frac{\widehat{Cov}(Y, X)}{\widehat{Var}(X)} = 1.8625$$
* Pre-experiment spend correlation: $\rho_{YX} = \mathbf{0.5535}$
* Theoretical variance reduction: $1 - \rho_{YX}^2 = \mathbf{30.64\%}$
* Empirical variance reduction achieved: **31.02%**
* Standard error reduction: $SE_{raw} = ₹53.28 \rightarrow SE_{cuped} = ₹44.37$ (16.73% narrower CI width).
* **Business Duration Saved:** Required sample size drops to 69.36% of original, shortening the test from **6.0 weeks to 4.16 weeks (saving 12.9 business days)**.
