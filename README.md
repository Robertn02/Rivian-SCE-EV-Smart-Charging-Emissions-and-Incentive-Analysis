# EV Smart Charging: Rivian & SCE Emissions Optimization and Business Strategy

The project is based on a case study involving **Rivian** and **Southern California Edison (SCE)**, exploring how EV smart charging can reduce grid emissions and create new business value.

---

## Project Context

Rivian’s Smart Charging feature currently optimizes home charging for lower utility costs.  
SCE is evaluating an expanded version that delays charging by 8 hours **if** the later window produces **≥10% lower emissions**.

The goal:  
A simple, automated system that reduces carbon intensity **without requiring any behavior change from EV drivers**.

This project develops the ML model and business strategy that such a collaboration would require.

---

## Objectives

### **Technical**
- Predict whether delaying charging by 8 hours yields at least **10% lower CO₂ emissions**.
- Train the classifier using **2023 CAISO emissions data**.
- Evaluate model vs. perfect assignment vs. baseline.

### **Business**
- Convert emissions savings into customer incentives under SCE’s proposed **$1–$10 per lb CO₂ avoided**.
- Estimate monthly savings for drivers.
- Use EV sales elasticity to model potential uplift if Rivian bundles savings into lease/financing.
- Propose a **win–win–win strategy** for:
  - Rivian  
  - Southern California Edison  
  - EV customers  

---

## Methodology

1. **Data Integration**
   - Joined ~150k home charging sessions (2024) to CAISO hourly emissions data (2023–2024).
   - Computed two windows per charging session:  
     - `A = [t, t+8)`  
     - `B = [t+8, t+16)`  
   - Label = 1 if `B < 0.9 × A`.

2. **Feature Engineering**
   - Hour-of-day, day-of-week, month, weekend/holiday flags
   - Emissions rolling mean & volatility
   - Lagged emissions at t–1…t–24

3. **Modeling**
   - Logistic Regression baseline  
   - XGBoost with monotone constraints  
   - Evaluation on 2024 sessions

4. **Impact Measurement**
   - Δ Emissions per session and per vehicle/year
   - Total excess emissions due to model errors
   - Cutoff tuning + penalty recommendations

5. **Business Modeling**
   - Monetized per-vehicle CO₂ savings  
   - Computed payment-equivalent savings  
   - Estimated Rivian sales uplift via log-log elasticity model

---

## Key Findings (Template – fill with your results)

- **Perfect assignment** could reduce emissions by *X lb CO₂ per vehicle per year*.  
- **Model-based assignment** captures ~*Y%* of the potential reductions.  
- **Financial impact:** equivalent to lowering effective monthly EV payments by **$Z–$Z₂ per driver**.  
- **Elasticity results:** Rivian could see *A–B%* potential sales lift under ideal conditions.  
- **Strategic result:** high alignment — substantial benefits for SCE and customers with minimal friction for Rivian.

