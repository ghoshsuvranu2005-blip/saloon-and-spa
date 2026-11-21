# EXECUTIVE DECISION MEMO: A/B TEST RESULTS & CAUSAL IMPACT ANALYSIS
**TO:** Chief Executive Officer, Chief Financial Officer & Board of Directors  
**FROM:** Lead Econometrician & Experimentation Platform Lead  
**DATE:** November 21, 2026  
**SUBJECT:** Business Impact Assessment: Retrospective Q3 Rollout & Q4 "SmartSlot VIP" A/B Test  
**DECISION STATUS:** **GO — PROCEED WITH CHAIN-WIDE ROLLOUT**  

---

### 1. Executive Summary & Core Recommendation
Following an exhaustive causal econometric evaluation of **300,000 appointment records across all 22 outlets**, the Experimentation & Data Science team recommends an immediate, chain-wide **GO** for the **"SmartSlot VIP" Dynamic Deposit & Concierge Protocol**. 

1. **New Initiative A/B Test (Q4):** Delivered a statistically verified **+10.09% lift in Net Revenue Per Visit (RPV)** [95% CI: +6.88%, +13.30%, $p < 0.0001$] and slashed the True No-Show Rate by **-36.1%** (-5.66 percentage points), while improving overall booking volume by **+1.2%**.
2. **Retrospective De-biasing (Q3 Change):** Management's claimed **+15.7% revenue jump** from the Q3 WhatsApp upsell protocol was heavily confounded by macro-seasonality. Econometric Difference-in-Differences (DiD) proves that **nearly half of that jump (+7.44%) was general Kongu wedding & festive demand**, with the true policy effect being **+8.18%** [95% CI: +5.09%, +11.27%].
3. **Financial Bottom Line:** Full deployment of SmartSlot VIP will generate an estimated **₹2.48 Crore in incremental annualized EBITDA** across our 22-salon network with zero brand equity dilution.

---

### 2. Comprehensive Metric Scorecard & Empirical Findings

| Evaluation Dimension | Metric / Test | Control Arm | Treatment Arm | Estimated Impact [95% Confidence Interval] | Statistical Significance | Business Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **A/B Test Primary** | **Net Revenue / Visit (RPV)** | ₹2,635.63 | ₹2,901.54 | **+₹265.90 (+10.09%)** [₹181.20, ₹350.60] | Welch $t = 6.15, p < 0.0001$ | **WIN (Target $\ge +3\%$)** |
| **A/B Test Secondary**| **True No-Show Rate (%)** | 15.68% | 10.02% | **-5.66 pp (-36.09%)** [-6.27 pp, -5.05 pp] | $z = -18.26, p < 0.0001$ | **WIN (Target $\le -3\text{ pp}$)** |
| **Integrity Diagnostic**| **Sample Ratio Mismatch** | 23,031 (49.7%) | 23,304 (50.3%)| **Diff: 0.58%** (Expected 50:50) | $\chi^2 = 1.61, p = 0.2047$ | **PASS (No SRM)** |
| **Quasi-Exp (Q3 Past)**| **True Causal DiD ($\beta_3$)** | Baseline Outlets | 12 Treated Outlets| **+₹201.28 (+8.18%)** [₹125.30, ₹277.25] | $t = 5.19, p < 0.0001$ | **47.5% was Seasonality** |
| **Variance Reduction**| **CUPED Acceleration** | Raw SE: ₹53.28 | CUPED SE: ₹44.37 | **Variance Reduced by 31.02%** ($\rho = 0.5535$) | CI 16.7% Narrower | **Saved 13 Days of Test** |

---

### 3. De-biasing Q3: Seasonality vs True Business Value
In Q3, leadership observed a gross revenue increase of +15.7% across 12 Coimbatore outlets. Our Difference-in-Differences model against 10 comparable regional outlets (Greater Kovai, Tirupur, Erode) disentangles this claim:
* **The Kongu Festive Surge (+7.44%):** Driven by late Aadi discount clearance, auspicious *Aavani Muhurtham* weddings, and pre-Diwali demand across all western TN salons regardless of intervention.
* **The True Policy Lift (+8.18%):** While positive, it was **barely half of what was claimed**. Uncontrolled business changes create dangerous illusions of competence; future rollouts must use causal evaluation to prevent misallocated capital.

---

### 4. Segment Winners & Losers (Heterogeneous Effects)

```
[Residential Outlets (Vadavalli, Kovaipudur)]   ████████████████████ +13.94% (High loyalty, low deposit friction)
[Senior Stylists Portfolio]                    ██████████████████   +15.37% (Excellent voucher cross-selling)
[Skin & Facials Vertical]                      █████████████████    +14.23% (High voucher uptake for home care)
[Hair Services Vertical]                       ████████████████     +14.55% (Consistent basket expansion)
[Walk-in / First-time Clients]                 ████████████         +10.35% (Better seating predictability)
[High Street Hubs (R.S. Puram, Race Course)]   ███████████          +9.45%  (Steady adoption)
[Mall Outlets (Brookefields, Prozone)]         █████                +4.23%  (Muted: higher spontaneous footfall)
[Bridal & Makeover High-Ticket]                ████                 +3.76%  (Insignificant lift: high ticket variance)
```
* **Key Takeaway:** Neighborhood residential outlets and senior stylists drive the largest incremental gains. Mall outlets have higher walk-in spontaneity and require nuanced deposit policies.

---

### 5. Implementation Roadmap & Guardrail Safeguards
To safeguard brand equity while rolling out across all 22 outlets:
1. **Preserve Walk-in Buffer:** Mandate that **25% of styling chairs** remain unreserved for spontaneous walk-in traffic in mall and high-street locations.
2. **Graceful Deposit Policy:** Full automatic deposit refund if cancelled with $\ge 2$ hours notice, or 100% credit applied if rescheduled within 7 days.
3. **Permanent CUPED Deployment:** Institutionalize the CUPED engine within the enterprise BI stack, permanently cutting future A/B testing cycles from 6 weeks to 4 weeks.

**Final Board Verdict:** **GO.** Authorize regional operations to implement SmartSlot VIP effective Q1.
