# ❤️ Find Love – Marketing Campaign Analytics 

This project is an **end-to-end marketing analytics pipeline** built for a dating company (anonymised as *Find Love*).  
It takes raw data from Facebook, TikTok, sign-ups, transactions, and currency exchange rates, then transforms it into a clean, ready-to-use dataset that powers a **self-serve dashboard** for the marketing team.  

---

## 🎯 Project Goal
To help the marketing team answer three simple questions:
1. Which campaigns are bringing in the most new customers?  
2. How much money are we spending to turn a sign-up into a paying customer?  
3. Which channels give the best return for every pound spent?  

---

## 📂 Data Sources
- **Facebook spend** – ad campaign costs (already in GBP).  
- **TikTok spend** – ad campaign costs (converted from USD to GBP).  
- **FX rates** – daily currency conversions.  
- **Sign-ups** – new user registrations with campaign attribution.  
- **Transactions** – customer payments in GBP and EUR.  

---

## ⚙️ Data Pipeline
![Pipeline](images/pipeline.png)  
*From raw CSVs → cleaning & validation → analytics table → Looker dashboard.*  

Steps:
1. **Load** raw datasets into BigQuery.  
2. **Clean** data: remove duplicates, fix currency issues, split campaign details.  
3. **Validate** with dbt tests: check for missing values, wrong formats, or negative spend.  
4. **Assemble** a single campaign performance table with key metrics.  
5. **Visualise** results in Looker so marketers can explore without writing SQL.  

---

## 📊 Dashboard Highlights

### 📊 Funnel View  

**Overview:** Tracks the journey from money spent → sign-ups → paying customers.  

**Conclusion:** Only ~14% of sign-ups converted into paying users; most dropped off before purchase.  

**Insight:** The biggest leak is between sign-up and first payment.  

**Action:** Add early nudges (emails, trial offers, discounts) in the first week.  

![Funnel](images/Funnel.png)  

---

### 📊 Channel Comparison  

**Return on Ad Spend (blue bars):**  
1 = break-even. Above 1 = profit.  
TikTok → 1.53 (good), Facebook → 1.29 (weak).  

**Cost to acquire a paying customer (red bars):**  
Reference line = £20.52 (average).  
TikTok → £18.15 (below average, good).  
Facebook → £22.37 (above average, risky).  

**Insight:** TikTok delivers stronger returns and cheaper customers.  

**Action:** Shift more budget to TikTok, optimise or cap Facebook until it improves.  

![TikTok vs Facebook](images/tiktok_vs_fb.png)  

---

### 📊 Spending Efficiency (by Country)  

**Which country performs better?**  
Great Britain → £1 spent returns ~£1.54.  
France → £1 spent returns ~£1.13.  

**What does it mean?**  
UK campaigns are more profitable, while French campaigns underperform.  

**How to improve France:**  
- Reallocate part of the French budget to the UK (higher returns).  
- Run A/B tests in France with new creatives and tighter targeting.  
- Track weekly until France reaches at least ~1.3× return.  

![ROAS](images/roas.png)  


### Dashboard Snapshots
![Marketing Dashboard 1](images/Marketing_dashboard_1.jpg)  
![Marketing Dashboard 2](images/Marketing_dashboard_2.jpg)  

---

## ✅ Data Quality
![Unit Testing](images/Unit-testing-Page-2.jpg)  
All cleaning and transformations are tested in **dbt**, ensuring:
- No missing or duplicate sign-ups.  
- No negative or invalid ad spend.  
- Currency conversions applied consistently.  

---

## 🔑 Key Insights
1. **TikTok outperformed Facebook** – lower cost per paying customer and higher revenue return.  
2. **Campaign D was the winner** – every pound spent returned £1.70 in revenue.  
3. **Campaign A lost money** – spend was equal to or greater than customer revenue, so it should be paused.  
4. **UK campaigns beat France** – higher returns per pound spent in Great Britain.  
5. **Organic sign-ups were high but didn’t generate revenue** – they need follow-up nudges to convert.  

---

## 🛠️ Tech Stack
- **BigQuery** – cloud data warehouse.  
- **dbt** – transformations + testing.  
- **Looker** – dashboard delivery.  
- **GitHub** – version control and code sharing.  

---

## 🚀 Future Improvements
- Automate daily runs with Airflow or dbt Cloud.  
- Add creative-level and audience-level data for deeper campaign insights.  
- Track post-sign-up “success events” (e.g. *started a relationship*) to measure true outcomes, not just purchases.  

---
