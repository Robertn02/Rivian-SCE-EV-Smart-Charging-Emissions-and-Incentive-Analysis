# EV Smart Charging: Rivian & SCE Emissions Optimization and Incentive Analysis

This project builds a full end-to-end pipeline to identify cleaner and cheaper EV charging windows using real emissions data. We train a binary classifier to predict whether delaying charging by eight hours reduces grid emissions, apply the model to Rivian charging sessions, quantify emissions savings, translate them into incentive payments, and estimate business impact through price elasticity analysis.

---

## Overview

Electric vehicles are often charged during high-emission evening hours. Southern California Edison (SCE) is exploring incentives to shift charging to cleaner periods, while Rivian is interested in how this shift affects customer cost and vehicle sales.  
This project evaluates whether smart-charging automation can:

- Reduce overall grid emissions  
- Lower charging costs for drivers  
- Increase Rivian EV adoption via improved affordability  

---

## Objectives

- Build a binary classifier using **2023 CAISO emissions** to determine whether a delayed 8-hour charging window is cleaner than charging immediately  
- Apply predictions to **2024 Rivian charging sessions**  
- Compare emissions under Baseline, Perfect (oracle), and Model assignments  
- Quantify emissions savings and misclassification penalties  
- Convert avoided emissions into **SCE incentive dollars**  
- Estimate **sales uplift** using a price elasticity model  

---

## Methodology

1. **Label Generation:**  
   Compare emissions in two windows (immediate vs. delayed). Assign a delay label if the delayed window is ≥10% cleaner.

2. **Feature Engineering:**  
   Time-based features (hour, weekday), rolling averages, lagged emissions, and volatility indicators.

3. **Modeling:**  
   Logistic Regression / Random Forest with ROC-AUC evaluation and calibration checks.

4. **2024 Application:**  
   Merge predicted labels with real charging sessions to compute emissions under each assignment strategy.

5. **Incentive & Elasticity Analysis:**  
   Convert emissions savings into dollars and evaluate how lower monthly costs affect EV sales.

---

## Key Results

### Emissions Impact
- **Baseline:** 4,939,906 lbs CO₂/year  
- **Perfect Assignment:** 4,240,556 lbs  
- **Model Assignment:** 4,463,540 lbs  

Model captures **68.12%** of ideal savings and avoids **476,366 lbs** of CO₂ vs. baseline.

### Financial Impact (SCE Incentives)
- Annual savings per driver: **$233 – $1,164**  
- Monthly savings: **$19 – $97**  

### Rivian Sales Impact
- Price elasticity: **–3.1981**  
- Estimated sales uplift from incentives: **10.7% – 21.3%**

---

## Recommendation & Conclusion

Our analysis shows that shifting EV charging to cleaner time windows creates real environmental and financial benefits. The model captures **68% of the ideal emissions savings**, reducing annual CO₂ output by over **476,000 lbs** compared to immediate charging. When these savings are translated into SCE’s incentive structure, drivers receive **meaningful monthly savings** that improve the total cost of ownership for Rivian vehicles.

To maximize adoption, we recommend that Rivian implement **automated smart-charging** in the vehicle app, allowing drivers to opt in once and let the system handle scheduling based on emissions forecasts. SCE should support this with **simple, predictable incentive payments** that directly reward lower-emission charging behavior.

Overall, the combination of optimized charging windows, financial incentives, and app-based automation creates a **win–win–win**:  
- **SCE** reduces peak-hour emissions,  
- **Drivers** save money with no extra effort, and  
- **Rivian** strengthens its value proposition and can see a **10–21% uplift** in vehicle demand.

Smart charging is technically feasible, financially attractive, and strategically aligned for all stakeholders.  
The conclusion is clear: **this program is worth implementing at scale.**
