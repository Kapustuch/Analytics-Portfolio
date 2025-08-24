# 🛒 Olist E-Commerce Data Analysis  

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

## Exporatory Data Analysis(EDA)

The EDA involved exploring the dataset to answer key business and operational questions, such as:

- **How has the number of purchases evolved over time?**  
- **Which product categories generate the highest total revenue?**  
- **What is the average delivery time (from purchase to customer delivery)?**  
- **How common are installment payments (more than one payment per order)?**  
- **Are customers and sellers typically located in the same or different states?**

## Data Analysis




