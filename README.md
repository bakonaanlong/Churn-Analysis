# Churn Analysis Dashboard 

---

## 1. Background and Overview

This **Churn Analysis Dashboard** is a strategic business intelligence tool designed to quantify customer attrition (churn) and identify underlying behavioral, demographic, and geographic drivers. Built on a proprietary dataset of 19,873 registered users, the dashboard aggregates key performance indicators (KPIs) across age, gender, tenure, geography, and creditworthiness.

### Core Objectives
- Measure churn magnitude (20.7% exit rate).
- Segment users by engagement (47.9% active).
- Correlate salary, tenure, and credit score with retention probability.
- Enable geography-specific interventions (Spain, Germany, France focus).

### Navigation
- Interactive filters: Age Bracket, Geography, Gender
- Real-time KPI tiles for instant executive scanning


---

## 2. Data Structure Overview

The underlying dataset is relational and anonymized, comprising the following inferred schema:

| Table / Dimension | Key Fields | Data Type | Description |
|-------------------|------------|-----------|-----------|
| **users** | user_id (PK) | Integer | Unique identifier |
| | age_bracket | Categorical [MiddleAged, Old, Young] | Derived from DOB |
| | gender | Binary [Male, Female] | Self-reported |
| | geography | Categorical [Spain, Germany, France, …] | ISO country + region |
| | salary_usd | Numeric (annual) | Pre-tax compensation |
| | tenure_years | Numeric (decimal) | Platform registration duration |
| | credit_score | Integer [300-850] | FICO-equivalent |
| | is_active | Boolean | Current engagement flag |
| | exited | Boolean | Churn flag (1 = churned) |
| | registration_date | Date | Account creation |
| | last_active_date | Date | Most recent login |

### Calculated Metrics
- **Percentage of Exits** = `COUNT(exited = 1) / COUNT(user_id)` × 100
- **Percentage of Active Users** = `COUNT(is_active = 1) / COUNT(user_id)` × 100
- **Average Tenure** = `MEAN(tenure_years)` segmented by filters
- **Average Salary** = `MEAN(salary_usd)` segmented by filters

---

## 3. Executive Summary

**Headline KPIs (All Users)**
- Total Users: **19,873**
- Exit Rate: **20.7%** (4,114 churned)
- Active User Rate: **47.9%** (9,519 retained & engaged)
- Platform-wide Average Tenure: **5.16 years**
- Gender Tenure Gap: Males 5.44 years | Females 4.89 years
- Average Credit Score: **636** (mid-prime)

**Critical Observation**  
> “The age bracket with the **least number of products and tenure are: OLD**”  
This flagged segment drives disproportionate churn despite higher absolute salaries.

**Geographic Snapshot**
- Germany: highest average tenure (5.49 years) & salary (~$108,000)
- Spain: moderate tenure (5.13 years)
- France: lowest tenure (4.97 years) & salary (~$92,000)

The dashboard reveals a **retention triad**: longer tenure → higher salary → stronger credit → lower churn probability.

---

## 4. Insights Deep Dive

![yeahboy](https://github.com/bakonaanlong/Churn-Analysis/blob/main/churn%20dashboard.JPG)

### 4.1 Age Bracket Analysis
- **Salary Distribution**: MiddleAged dominate earnings ($90-110k peak); Old plateau at ~$85k; Young trail at ~$65k.
- **Tenure Pattern**: All brackets converge at ~5 years, but **Old** users display the shortest tenure despite seniority → **premature disengagement**.
- **Product Adoption Flag**: Old segment registers **fewest products** → under-utilization despite financial capacity.

### 4.2 Gender Dynamics
- Male users out-tenure females by **11.3%** (5.44 vs. 4.89 years).
- Implication: female lifecycle value compression; targeted loyalty programs warranted.

### 4.3 Geographic Variance
| Country | Avg Salary | Avg Tenure | Credit Score | Users (implied) |
|---------|------------|------------|--------------|-----------------|
| Germany | $108,000   | 5.49 years | 635          | High density    |
| Spain   | $102,000   | 5.13 years | 653          | Moderate        |
| France  | $92,000    | 4.97 years | 636          | Moderate        |

Germany’s **tenure premium** (+0.33 years above platform average) correlates with highest salary band.

### 4.4 Churn Drivers Synthesis
1. **Low Product Breadth in Old Segment** → reduced stickiness.
2. **Female Tenure Deficit** → earlier offboarding.
3. **French Market Lag** → dual salary & engagement penalty.

---

## 5. Recommendations

### Immediate (0-3 Months)
1. **“Silver Loyalty” Campaign**  
   Target: Old segment  
   Offer: bundled product trials + tenure milestone bonuses  
   KPI: +0.5 years average tenure within 90 days

2. **Gender-Specific Onboarding 2.0**  
   Extend female guided tours by 30 days; introduce peer mentorship  
   Success metric: close 50% of the 0.55-year gap

### Mid-Term (3-9 Months)
3. **France Acceleration Program**  
   - Localized credit-line incentives  
   - Salary-benchmarked cashback  
   Target: lift French tenure to 5.30 years

4. **Product Cross-Sell Engine**  
   ML-driven recommendations prioritizing Old users  
   Goal: increase average products/user from current low baseline by 25%

### Long-Term (9-18 Months)
5. **Churn Prediction Model Integration**  
   Embed real-time risk scores (tenure < 4.5 years + credit < 620 + single product)  
   Trigger proactive retention touches

6. **Geography Expansion Playbook**  
   Replicate Germany’s high-salary/high-tenure success in new EU markets

### Governance & Monitoring
- Assign KPI owners:  
  - Churn % → Retention Lead  
  - Tenure → Product Lead  
  - Geographic metrics → Regional VPs
- Monthly dashboard review cadence
- Version control: dataset v2.0 to include product_count explicit field

---


