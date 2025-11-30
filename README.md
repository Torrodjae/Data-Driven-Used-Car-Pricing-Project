# Data-Driven-Used-Car-Pricing-Project
CTEC 426 Final Project — Data-Driven Pricing Model for Fairness in the Used Car Market

# Data-Driven Pricing: Promoting Fairness in the Used Car Market  
### CTEC 426 — Data & Predictive Analysis Project  
**By: Torrodjae Somerville**

---

## Project Overview  
The used car market is massive, fast-moving, and often inconsistent. Pricing varies wildly between sellers, locations, and vehicle conditions. The goal of this project is to use **data-driven techniques** to uncover the real factors that determine pricing, promote transparency, and help buyers and sellers make fair and informed decisions.

Using Austin Reese’s “Used Cars Dataset” from Kaggle, this project analyzes 426,880 U.S. used car listings scraped from Craigslist.  
It focuses on:  
- identifying meaningful relationships in the data  
- cleaning and refining the dataset  
- engineering new features for smarter price prediction  
- classifying vehicles by market tier  
- extracting actionable, real-world insights

---

## Research Questions  
1. **What is the relationship between a vehicle’s age, mileage, and listing price?**  
2. **How do condition, vehicle type, and manufacturer influence price and volatility?**  
3. **What features signal a “good deal” or an overpriced listing?**  
4. **Can engineered variables improve predictive value beyond the original dataset?**

---

## Dataset Information  
**Source:** Austin Reese — “Used Cars Dataset” (Kaggle)  
**Collection Method:** Craigslist web scraping  
**Original Size:** 426,880 rows × 26 columns  
**Snapshot Year:** 2022  

Each row represents an individual car listing including:  
price, condition, year, manufacturer, model, mileage, fuel type, transmission, etc.

---

## Data Cleaning & Wrangling  
Because the raw dataset was messy and inconsistent, the following steps were performed:

## Removed unrealistic entries  
- Prices < $500 or > $90,000  
- Model years ≤ 1948 (removes classic/antique cars)  
- Extreme odometer outliers  

## Dropped rows with missing critical fields  
(price, year, condition, odometer)

## Removed duplicates  
Using VIN checking where available.

## Standardized condition labels  
Consolidated the original 8+ condition categories into these:  
- *Salvage*  
- *Fair*  
- *Good*  
- *Excellent*  
- *Like New / New*

### Final Clean Dataset  
**365,671 rows × 15 columns**  
(≈14% reduction from original size)

---

## Feature Engineering

### **1. Age**  
Formula:  
`age = 2023 - year`  

Why?  
- Age reflects depreciation better than model year  
- Creates more linear relationships for analysis  
- Used by insurers and lenders

---

### **2. Miles per Year**  
Formula:  
`miles_per_year = odometer / age` (with 0 replaced by 1)

Why?  
- Total mileage alone is misleading  
- Reveals usage intensity (family use, fleet use, highway use)  
- Strong predictor of price decline  
- Helps distinguish well-maintained vs. heavily used cars

---

### **3. Price Category (Edmunds Market Tiers)**  
Using Edmunds’ used car price classifications:

- **Budget:** $0–$15,000  
- **Mid-Range:** $15,000–$30,000  
- **Luxury:** $30,000+  

Benefits:  
- Enables clearer market comparison  
- Reveals manufacturer positioning  
- Shows how vehicle types cluster across price bands

---

## Key Findings

### **1. Strongest Price Drivers**  
- **Mileage (Odometer)** → correlation ≈ *-0.66*  
- **Age** → correlation ≈ *-0.52*  
- **Miles per Year** → correlation ≈ *-0.34*  

**Interpretation:**  
Increasing mileage and usage intensity reduce value faster than age alone.

---

### **2. Market Landscape**  
Using outlier-filtered IQR plots:  
- Trucks & SUVs show higher median values than sedans and coupes  
- Outlier removal clarifies a realistic buyer’s price range  
- High-value anomalies often indicate premium trims or potential scam listings

---

### **3. Condition Affects Value at Every Age**  
- Excellent/Like New vehicles command premiums across all ages  
- Salvage/Fair vehicles show significantly reduced valuations  
- Condition acts as a vertical “shift” in the age-price curve

---

### **4. Usage Patterns Matter**  
- Mini-vans, trucks, and SUVs show **high miles/year**, used for work or family  
- Coupes, hatchbacks, and convertibles show **low miles/year**, used for leisure  
- This difference directly impacts resale value

---

### **5. Demand Creates Price Anomalies**  
High-use vehicles have a **wider upper range** of pricing due to demand, leading to:  
- justified high values  
- inflated “premium” listings  
- higher risk of scams

---

## Actionable Insights

## For Buyers  
- Look at **miles per year**, not just total miles  
- Condition differences represent real dollar value  
- Be cautious of unusually high truck/SUV prices  

## For Sellers  
- Highlight low miles/year to justify premium asking prices  
- Be transparent about condition to build trust  

## For Platforms (Craigslist, Facebook Marketplace)  
- Add an estimated fair price tool for transparency  
- Flag potential overpricing or underpricing based on usage intensity  

---

## Proposed Data Product: **FairPrice Car Valuation Tool**

A web-based app where users input:  
- make, model, year  
- condition  
- mileage  
- fuel type  
- vehicle type  

Using a trained model, the tool would:  
- Predict **fair market value**  
- Flag **Good Deals** and **Premium Listings**  
- Compare the vehicle to its market segment  

Who would benefit:  
- Everyday buyers  
- Private sellers  
- Small dealerships  

---

## Challenges & How They Were Solved
- **Messy condition labels** → standardized 5-category system  
- **Extreme outliers** → removed using realistic boundaries  
- **Missing context** → engineered `age` and `miles_per_year`  
- **Potential divide-by-zero errors** → handled through replacement  
- **Large dataset inconsistencies** → cleaned and filtered  

---

## Future Improvements  
If more time were available:

## Machine Learning  
- Random Forest or XGBoost model for automated price estimation  
- Good Deal detector  
- Price anomaly detector  

## Enhanced Feature Engineering  
- Regional price adjustments  
- Seasonal pricing trends  

## Data Product Expansion  
- Build a full FairPrice calculator website  
- Dealer dashboard for inventory valuation  

---

## Included Files  
- **CTEC 426 Project PowerPoint** (full analysis)  
- **README.md** (you’re reading it)  
- Any future notebooks / scripts (if added)

---

## Author  
**Torrodjae Somerville**  
CTEC Student — Bowie State University

---

## Contact  
Email: **somervilletj0@gmail.com**   
