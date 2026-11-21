# ⚖️ Governance, Decision Framework, & Threats to Validity

The `governance/` directory houses the formal decision memos, executive governance criteria, SUTVA capacity constraints, and econometric risk analyses for **Kongu Aura Wellness & Salon Chain**.

---

## 📋 Executive Decision Matrix

| Gate Criterion | Policy Threshold | Observed Empirical Value | Gate Verdict |
| :--- | :--- | :--- | :--- |
| **Primary Metric (RPV)** | Lift $\ge +3.0\%, p < 0.05$ | **+10.09%** [CI: +6.88%, +13.30%], $p < 0.0001$ | **PASS** |
| **Secondary (No-Show)** | Drop $\ge -3.0\text{ pp}, p < 0.05$ | **-5.66 pp** (-36.09%), $p < 0.0001$ | **PASS** |
| **Internal Validity (SRM)** | Pearson $\chi^2$ $p > 0.01$ | $\chi^2 = 1.6085, p = 0.2047$ | **PASS** |
| **Volume Retention** | Drop $\le -3.0\%$ | **+1.2% net booking volume growth** | **PASS** |
| **Annualized EBITDA** | $> ₹1.5\text{ Crore}$ | **+₹2.48 Crore EBITDA Addition** | **PASS** |

### **Final Board Verdict: GO (PROCEED WITH CHAIN-WIDE ROLLOUT)**

---

## ⚠️ Threats to Causal Validity: What Could Make Our Estimates Wrong?

As outlined in [THREATS_TO_VALIDITY.md](../THREATS_TO_VALIDITY.md), five critical threats could bias causal conclusions:

### 1. SUTVA Violation via Physical Chair Displacement
* **Mechanism:** In a salon with 8 chairs, Treatment clients showing up reliably occupy prime chairs during peak hours. On crowded Saturdays, this crowds out walk-in and Control patrons.
* **Bias Direction:** **Positive Bias (Overestimates lift).** The observed lift partially reflects *stolen chair capacity* from Control rather than pure net-new market creation.
* **Mitigation:** We segmented outcomes by Day Type (Weekday vs Weekend). Weekend capacity saturation was accounted for, and a 25% unreserved chair buffer is mandated for rollout.

### 2. Stylist Hawthorne Effect & Preferential Effort
* **Mechanism:** Stylists aware that a client has the "VIP" tag on the POS terminal may deliver superior service, scalp massages, or more aggressive retail upselling.
* **Bias Direction:** Positive bias toward VIPs; or underestimation if newly learned upsell behavior spills over into Control appointments.
* **Mitigation:** Voucher redemption is handled at POS checkout rather than during chair consultation.

### 3. Selective Funnel Drop-off (Hidden SRM at Booking Screen)
* **Mechanism:** If price-sensitive customers abandon the booking flow at the deposit prompt *before* a transaction ID is generated, the Treatment group suffers from **survivorship bias**.
* **Bias Direction:** Positive bias (Treatment appears wealthier than Control).
* **Mitigation:** Full-funnel instrumentation logs assignment at the moment service is selected, prior to deposit prompt presentation.

### 4. Asymmetric Local Confounders in DiD
* **Mechanism:** If Coimbatore urban centers experienced an idiosyncratic surge (e.g. concentrated wedding banquet hall bookings or regional ad blitzes) not shared by Tirupur/Erode, the DiD estimator attributes this divergence to the WhatsApp protocol.
* **Mitigation:** 12-window dynamic event study verified that pre-treatment leads were parallel.

### 5. Intra-Cluster Correlation (ICC)
* **Mechanism:** Salon appointments within the same outlet share local staff, manager efficiency, and footfall demographics ($ICC \approx 0.012, Def \approx 18.39$).
* **Mitigation:** Clustered standard errors and non-parametric block bootstrapping prevent false discoveries.

---

## 📁 Governance Documents Inventory

* `DECISION_MEMO.md`: 1-page executive decision memo tailored for the CEO, CFO, and Board.
* `EXPERIMENT_DESIGN_DOCUMENT.md`: Full formal A/B experiment design and power analysis specification.
* `THREATS_TO_VALIDITY.md`: Deep econometric treatise detailing identification risks.
