# 🛒 Olist E-Commerce Data Analysis  

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Final Results & Business Recommendations](#final-results--business-recommendations)
- [Limitations](#limitations)

## Project Overview  
This project explores the **Olist Brazilian E-Commerce dataset**, which contains information on customer orders, payments, products, sellers, and logistics. The goal of the analysis is to uncover insights into customer behavior, product performance, payment preferences, and delivery challenges in Brazil’s e-commerce market.  

Through data cleaning, exploratory data analysis (EDA), and visualization, the project answers key business questions such as:  
- What are the most popular product categories and which generate the highest revenue?  
- How do payment methods and installment plans impact order value?  
- How does delivery performance vary across regions, and how does it affect customer satisfaction?  
- Where are most customers and sellers located, and what does this mean for logistics?  

The findings highlight both opportunities and challenges for Brazilian e-commerce companies, especially regarding logistics in Northern states, payment flexibility, and balancing sales volume with profitability.  

This project demonstrates how data analysis can translate into **actionable business recommendations** for improving operations, customer experience, and market growth strategies.  

## Data Sources

This project analyzes the **Brazilian E-Commerce Public Dataset** by Olist, publicly available on **Kaggle**. It contains approximately **100,000 orders** placed on the Olist Store between **2016 and 2018**, offering a rich, multi-dimensional view of Brazil’s e-commerce landscape.

### Dataset Highlights:
- **Orders & Payments**: Includes detailed order status, purchase timestamps, payment types (credit card, boleto, voucher), installment counts, and payment amounts.
- **Customer & Seller Information**: Provides anonymized customer IDs with city/state location data, alongside seller IDs and their geographic details.
- **Product Details**: Contains product category identifiers, descriptive metadata, and price information. A separate translation table allows mapping product categories from Portuguese to English.
- **Reviews**: Encompasses customer feedback through review scores and text comments on completed orders.
- **Geolocation**: Links Brazilian zip code prefixes to geographic coordinates, enabling spatial and logistics-oriented analyses.

You can access the dataset and its files here:
[Brazilian E-Commerce Public Dataset by Olist on Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

## Tools 
- **Python** – core programming language for data analysis  
- **pandas** – data manipulation and cleaning  
- **numpy** – numerical computations and array operations  
- **matplotlib** – data visualization and plotting  
- **seaborn** – advanced statistical visualizations

## Data Cleaning/Preparation  

To prepare the dataset for analysis, the following steps were applied:  

- **Loaded multiple CSV files** (orders, order items, customers, products, payments, reviews, sellers, geolocation, and category translations).  
- **Converted date columns** (e.g., purchase, approval, delivery, and estimated delivery dates) into proper datetime format for time-series analysis.  
- **Checked for missing values** and identified nulls in delivery-related fields (mainly for canceled or undelivered orders).  
- **Handled duplicates**.   
- **Inspected numeric columns** for anomalies and outliers.  

These cleaning steps ensured consistent formats, reduced errors, and prepared the dataset for meaningful exploratory data analysis (EDA).  

## Exploratory Data Analysis

The EDA involved exploring the dataset to answer key business and operational questions, such as:

- **How has the number of purchases evolved over time?**  
- **Which product categories generate the highest total revenue?**  
- **What is the average delivery time (from purchase to customer delivery)?**  
- **How common are installment payments (more than one payment per order)?**  
- **Are customers and sellers typically located in the same or different states?**

## Data Analysis

### Example: Delivery Time vs Customer Review Scores  

One key analysis was to explore how delivery performance impacts customer satisfaction.  
The code below visualizes delivery times against review scores, both with and without extreme outliers (>75 days):  

```python
relationship_delivery_review = orders_customer_delivery.merge(
    reviews, on='order_id', how='left'
)[['order_id', 'delivery_days', 'review_score']]

fig, axs = plt.subplots(2, figsize=(12, 12))

sns.boxplot(relationship_delivery_review, x='review_score', y='delivery_days', color='skyblue', ax=axs[0])
sns.boxplot(relationship_delivery_review[relationship_delivery_review['delivery_days'] < 75], 
            x='review_score', y='delivery_days', color='skyblue', ax=axs[1])

for ax in axs:
    ax.grid(axis='y', linestyle='--', alpha=0.5)

axs[0].set_title("Delivery Time by Review Score (Full)", fontsize=14, weight='bold')
axs[0].set_xlabel("Review Score", fontsize=12)
axs[0].set_ylabel("Delivery Days", fontsize=12)

axs[1].set_title("Delivery Time by Review Score (<75)", fontsize=14, weight='bold')
axs[1].set_xlabel("Review Score", fontsize=12)
axs[1].set_ylabel("Delivery Days", fontsize=12)

plt.tight_layout()
```
<img width="1189" height="1189" alt="image" src="https://github.com/user-attachments/assets/740b33b8-3b28-4c1f-91be-f382275d5c85" />

### Result

This analysis showed that longer delivery times are generally associated with lower review scores, confirming the impact of logistics on customer satisfaction.

## Final Results & Business Recommendations  

The analysis of the Olist dataset highlights key patterns in customer behavior, product performance, logistics, and payment preferences that can inform strategic business decisions.  

### 1. Customer Behavior & Sales Trends  
- Online shopping in Brazil is growing steadily, with Mondays being the most popular day for purchases.  
- Seasonal peaks indicate opportunities to align promotions with high-demand months.  
**Recommendation:** Plan marketing campaigns around seasonal peaks and optimize promotions for the start of the week when engagement is highest.  

### 2. Product Strategy  
- `bed_bath_table` and `health_beauty` dominate in sales volume and revenue but show relatively low average order values.  
- Niche categories like `computers` generate fewer sales but achieve higher value per purchase.  
**Recommendation:** Maintain strong presence in high-volume categories while exploring strategies to boost order value (bundling, premium products). Invest in high-value niches with tailored marketing.  

### 3. Logistics & Delivery Performance  
- Typical delivery time is 6–15 days, but customers in Northern Brazil wait up to 2–3x longer than those in Southeastern regions.  
- Longer delivery times are strongly linked to lower customer review scores.  
**Recommendation:** Strengthen logistics in Northern regions through partnerships with local carriers, better route planning, and alternative transport methods. Communicate realistic delivery expectations to maintain trust.  

### 4. Payments & Customer Experience  
- Credit cards account for 77% of payments, with nearly half of customers opting for installments (avg. 2.85).  
- Higher installment options are associated with higher order values.  
**Recommendation:** Continue supporting diverse installment options to encourage higher spending. Offer incentives for customers to use installments responsibly.  

### 5. Marketplace Dynamics & Regional Focus  
- São Paulo dominates the market (42% of customers, 60% of sellers), but buyers are more geographically dispersed.  
**Recommendation:** While SP remains the core market, expanding seller presence in other states can reduce delivery delays and improve customer satisfaction.  

---

**Overall Business Insight:**  
Brazilian e-commerce is growing rapidly but remains geographically uneven. Companies that combine efficient logistics, flexible payment options, and region-specific marketing can capture both the dense urban hubs (SP, RJ, MG) and unlock new opportunities in the logistically challenging Northern regions. To achieve sustainable growth, sellers and marketplaces should prioritize logistics optimization, financial accessibility, and product diversification—strengthening their presence in established markets while expanding into underserved areas.

## Limitations  

Some records have missing or inconsistent values. For example:  
  - Several orders have no `order_delivered_customer_date`, which usually corresponds to canceled or undelivered orders.  
  - A small portion of records show **0 delivery days** (likely data entry errors or same-day deliveries).  
  - Other records report **very high delivery times (40+ days)**, which are extreme outliers compared to the majority (6–15 days).  
These anomalies required cleaning and filtering, but they still introduce uncertainty and may slightly distort averages or trends.  


