# SmartCart — Customer Segmentation System

An end-to-end **unsupervised machine learning project** that segments SmartCart's e-commerce customers into actionable groups based on demographics, spending behavior, and engagement patterns.

---

## Project Overview

SmartCart is a growing e-commerce platform serving customers across multiple countries. The company currently uses **generic marketing and engagement strategies for all customers**, which leads to:

- Inefficient marketing spend
- Missed opportunities to retain high-value customers
- Delayed identification of churn-prone users

This project builds an **intelligent customer segmentation system** using clustering algorithms to group customers into meaningful, data-driven segments — enabling personalized marketing and better retention strategies.

---

## Dataset

- **2,240 customer records**, 22 attributes
- Covers customer demographics, purchase behavior, website activity, and campaign response

| Category | Features |
|---|---|
| **Demographics** | ID, Year_Birth, Education, Marital_Status, Income, Kidhome, Teenhome, Dt_Customer |
| **Spending (Amount)** | MntWines, MntFruits, MntMeatProducts, MntFishProducts, MntSweetProducts, MntGoldProds |
| **Purchase Frequency** | NumDealsPurchases, NumWebPurchases, NumCatalogPurchases, NumStorePurchases, NumWebVisitsMonth |
| **Feedback** | Recency, Complain, Response |

---

## Project Workflow

1. **Data Preprocessing** — handled missing values (Income), removed duplicates
2. **Feature Engineering**
   - `Age` from `Year_Birth`
   - `Customer_Tenure_Days` from `Dt_Customer`
   - `Total_spending` = sum of all `Mnt*` columns
   - `Total_childrens` = `Kidhome` + `Teenhome`
   - Simplified `Education` into Graduate / Postgraduate / Undergraduate
   - Simplified `Marital_Status` into `Living_Together` (Partner / Alone)
3. **Outlier Removal** — dropped extreme income (>$600,000) and age (>90) outliers
4. **Encoding & Scaling** — One-Hot Encoding for categorical features, StandardScaler for numerical features
5. **Dimensionality Reduction** — PCA (3 components, ~44% variance explained) for visualization
6. **Finding Optimal Clusters** — Elbow Method + Silhouette Score → optimal **k = 4**
7. **Clustering** — compared KMeans, Agglomerative Clustering, and DBSCAN
   - **Agglomerative Clustering (k=4)** produced the cleanest, most interpretable segments
8. **Cluster Profiling** — analyzed income, spending, channel preference, and response rate per segment

---

## Customer Segments

| Segment | Profile | Avg. Income | Avg. Annual Spend | Campaign Response |
|---|---|---|---|---|
| 🟥 **Budget-Conscious Families** | Couples with children, price-driven | $39,681 | $222 | 7.6% |
| 🟦 **Affluent Loyalists** | High-income couples, catalog & in-store shoppers | $72,808 | $1,237 | 16.7% |
| 🟨 **Window Shoppers** | Singles, frequent browsers, low spenders | $36,960 | $166 | 14.2% |
| 🟩 **VIP Singles** | Highest income, top spenders, best campaign response | $70,723 | $1,190 | 32.0% |

### Key Insights
- **Income ↔ Total Spend**: 0.79 correlation — higher income customers spend more overall
- **Income ↔ Website Visits**: -0.65 correlation — high earners prefer catalog & in-store shopping over the website
- **Catalog Purchases ↔ Total Spend**: 0.78 correlation — catalog is the strongest driver of high lifetime spend

---

## Strategic Recommendations

- **Budget-Conscious Families** → Discount codes, coupon campaigns, family-size bundles
- **Affluent Loyalists** → Loyalty programs, catalog-first marketing, in-store events
- **Window Shoppers** → Retargeting with personalized, time-limited web offers
- **VIP Singles** → Premium/white-glove service, early access, exclusive products (highest ROI segment)

---

## Repository Contents

| File | Description |
|---|---|
| `smartcart_customer.ipynb` | Full Jupyter Notebook — data cleaning, feature engineering, EDA, clustering, and cluster profiling |
| `smartcart_customers.csv` | Raw dataset (2,240 customer records) |
| `SmartCart_Clustering_System.pdf` | Original project brief / problem statement |
| `SmartCart_Customer_Segmentation.pptx` | Business presentation summarizing the segmentation results and recommended strategy for stakeholders |

---

## Tech Stack

- **Python**: pandas, numpy
- **Visualization**: matplotlib, seaborn
- **Machine Learning**: scikit-learn (OneHotEncoder, StandardScaler, PCA, KMeans, AgglomerativeClustering, DBSCAN, silhouette_score), kneed (KneeLocator)

---

## How to Run

```bash
pip install pandas numpy seaborn matplotlib scikit-learn kneed
jupyter notebook smartcart_customer.ipynb
```

Run all cells in order — the notebook walks through preprocessing, feature engineering, clustering, and cluster analysis step by step.

---

## Presentation

A stakeholder-facing summary of this project — including the segment overview, key data insights, and recommended marketing strategy per segment — is available here:

📊 [Download Presentation](./SmartCart_Customer_Segmentation.pptx)
