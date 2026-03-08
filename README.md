# Retail-Sales-Analysis-SQL-Project


# 📊 Retail Sales Data Analysis using SQL

## 📝 Project Overview

This project analyzes a retail sales dataset using SQL to simulate
real-world data analyst tasks. The project includes database creation,
data cleaning, exploratory data analysis (EDA), and generating business
insights from retail transaction data.

The objective of this project is to understand customer purchasing
behavior, sales trends, and category performance using SQL queries.

------------------------------------------------------------------------

## 📂 Dataset Description

The dataset contains transactional retail sales data. Each record
represents a customer purchase.

### Key Columns

-   transactions_id -- Unique identifier for each transaction\
-   sale_date -- Date of the sale\
-   sale_time -- Time of the sale\
-   customer_id -- Unique identifier for each customer\
-   gender -- Customer gender\
-   age -- Age of the customer\
-   category -- Product category\
-   quantity -- Number of units purchased\
-   price_per_unit -- Price per item\
-   cogs -- Cost of goods sold\
-   total_sale -- Total transaction value

------------------------------------------------------------------------

## 🛠 Tools & Technologies

-   SQL
-   PostgreSQL
-   pgAdmin
-   Retail Sales Dataset

------------------------------------------------------------------------

## 🗄 Database Setup

### Create Database

``` sql
CREATE DATABASE retail_sales_db;
```

### Create Table

``` sql
CREATE TABLE retail_sales (
    transactions_id INT PRIMARY KEY,
    sale_date DATE,
    sale_time TIME,
    customer_id INT,
    gender VARCHAR(10),
    age INT,
    category VARCHAR(35),
    quantity INT,
    price_per_unit FLOAT,
    cogs FLOAT,
    total_sale FLOAT
);
```

------------------------------------------------------------------------

## 🔍 Data Exploration

``` sql
SELECT COUNT(*) FROM retail_sales;
```

``` sql
SELECT COUNT(DISTINCT customer_id) FROM retail_sales;
```

``` sql
SELECT DISTINCT category FROM retail_sales;
```

------------------------------------------------------------------------

## 🧹 Data Cleaning

``` sql
DELETE FROM retail_sales
WHERE
sale_date IS NULL
OR sale_time IS NULL
OR customer_id IS NULL
OR gender IS NULL
OR age IS NULL
OR category IS NULL
OR quantity IS NULL
OR price_per_unit IS NULL
OR cogs IS NULL;
```

------------------------------------------------------------------------

## 📊 Business Analysis

### Sales on a Specific Date

``` sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

### Clothing Sales in November 2022

``` sql
SELECT *
FROM retail_sales
WHERE category = 'Clothing'
AND quantity >= 4
AND TO_CHAR(sale_date,'YYYY-MM')='2022-11';
```

### Total Sales by Category

``` sql
SELECT category,
SUM(total_sale) AS total_sales
FROM retail_sales
GROUP BY category;
```

### High Value Transactions

``` sql
SELECT *
FROM retail_sales
WHERE total_sale > 1000;
```

### Top 5 Customers by Total Spending

``` sql
SELECT customer_id,
SUM(total_sale) AS total_spent
FROM retail_sales
GROUP BY customer_id
ORDER BY total_spent DESC
LIMIT 5;
```

------------------------------------------------------------------------

## 📈 Key Insights

-   Sales performance varies across product categories.
-   Certain customers generate significantly higher revenue.
-   Monthly sales trends help identify peak sales periods.
-   Customer purchase behavior helps businesses identify valuable
    customers.

------------------------------------------------------------------------

## 📌 Conclusion

This project demonstrates practical SQL skills including database setup,
data cleaning, exploratory analysis, and business insight generation
using retail sales data.

⭐ If you found this project useful, feel free to star the repository.
