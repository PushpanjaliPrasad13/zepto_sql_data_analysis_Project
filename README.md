# zepto_sql_data_analysis_Project

This is a complete, real-world data analyst portfolio project based on an e-commerce inventory dataset scraped from [Zepto](https://www.zeptonow.com/) — one of India’s fastest-growing quick-commerce startups. This project simulates real analyst workflows, from raw data exploration to business-focused data analysis.

This project is perfect for:

📊 Data Analyst aspirants to build a strong Portfolio Project for interviews and LinkedIn
📚 Anyone learning SQL hands-on
💼 Preparing for interviews in retail, e-commerce, or product analytics

# Project Overview

The goal is to simulate how actual data analysts in the e-commerce or retail industries work behind the scenes to use SQL to:

✅ Set up a messy, real-world e-commerce inventory database

✅ Perform Exploratory Data Analysis (EDA) to explore product categories, availability, and pricing inconsistencies

✅ Implement Data Cleaning to handle null values, remove invalid entries, and convert pricing from paise to rupees

✅ Write business-driven SQL queries to derive insights around pricing, inventory, stock availability, revenue and more

# Dataset Overview

The dataset, originally sourced from [Kaggle](https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/data?select=zepto_v2.csv), was scraped from Zepto’s official product listings. It closely resembles a real-world e-commerce inventory system, providing realistic data patterns and structure.

Each row represents a unique SKU (Stock Keeping Unit) corresponding to a specific product listing.
Duplicate product names appear because the same item may be listed multiple times with variations in package size, weight, discount, or category — a common practice in e-commerce platforms to enhance product visibility.

| Column                     | Description                                                                         |
| :------------------------- | :---------------------------------------------------------------------------------- |
| **sku_id**                 | Unique identifier for each product entry (serves as a synthetic primary key).       |
| **name**                   | Product name as displayed on the Zepto app.                                         |
| **category**               | Product category (e.g., *Fruits*, *Snacks*, *Beverages*, etc.).                     |
| **mrp**                    | Maximum Retail Price in ₹ (originally in paise, later converted).                   |
| **discountPercent**        | Percentage discount applied to the MRP.                                             |
| **discountedSellingPrice** | Final selling price after applying the discount (in ₹).                             |
| **availableQuantity**      | Number of units available in stock.                                                 |
| **weightInGms**            | Product weight in grams.                                                            |
| **outOfStock**             | Boolean flag indicating whether the product is currently out of stock.              |
| **quantity**               | Number of units per package (for some products, this may represent weight instead). |

# Project Workflow

# 1. Database & Table Creation
We start by creating a SQL table with appropriate data types:

CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);

# 2. Data Import
Loaded CSV using pgAdmin's import feature.

# 3. 🔍 Data Exploration

Counted the total number of records in the dataset

Viewed a sample of the dataset to understand structure and content

Checked for null values across all columns

Identified distinct product categories available in the dataset

Compared in-stock vs out-of-stock product counts

Detected products present multiple times, representing different SKUs

# 4. 🧹 Data Cleaning
Identified and removed rows where MRP or discounted selling price was zero

Converted mrp and discountedSellingPrice from paise to rupees for consistency and readability

# 5. 📊 Business Insights

Found top 10 best-value products based on discount percentage

Identified high-MRP products that are currently out of stock

Estimated potential revenue for each product category

Filtered expensive products (MRP > ₹500) with minimal discount

Ranked top 5 categories offering highest average discounts

Calculated price per gram to identify value-for-money products

Grouped products based on weight into Low, Medium, and Bulk categories

Measured total inventory weight per product category
