# 🛒 Retail Sales Analysis — SQL Project

This project showcases a comprehensive analysis of retail sales data using SQL. It simulates a real-world business scenario where sales data is explored, cleaned, and analyzed to extract actionable insights. The dataset represents transactional data, and the analysis focuses on customer behavior, product category performance, and sales trends over time.

## 👨‍💻 Objective

To demonstrate SQL proficiency by:
- Cleaning and preparing raw retail data.
- Writing optimized queries to explore and analyze sales trends.
- Answering business questions that can guide strategic decisions.
- Presenting findings in a way that can inform real-world business actions such as customer segmentation, product focus, and campaign timing.

---

## 📁 Files Included

- **`SQL - Retail Sales Analysis_utf .csv`** — Raw dataset of transactions.
- **`Project 1.sql`** — SQL queries covering data cleaning, exploration, and analysis.
- **`README.md`** — This documentation file for project overview and walkthrough.

---

## 🧰 Tools & Technologies

- SQL (MySQL syntax used)
- MySQL Workbench / DBeaver / DB Fiddle (Any SQL environment)

---

## 🛠️ Project Workflow

### 1️⃣ Database and Table Creation

A database `Portfolio_Project` is created with a single table `retail_sales3` including fields like transaction ID, sale date and time, customer demographics, product category, quantity, COGS, and total sales.

### 2️⃣ Data Cleaning

The cleaning step removes any records with missing (`NULL`) values in important columns to ensure data quality.

```sql
DELETE FROM retail_sales3
WHERE age IS NULL OR cogs IS NULL OR sale_date IS NULL OR quantiy IS NULL;
```

### 3️⃣ Data Exploration

Simple queries are run to understand the size, diversity, and scope of the data:
- Total number of sales
- Unique customer count
- Number of distinct product categories

### 4️⃣ Business Questions Answered

#### Q1. **Sales on November 5, 2022**
```sql
SELECT * FROM retail_sales3 WHERE sale_date = '2022-11-05';
```
Used to analyze a specific promotional or holiday sales day.

#### Q2. **High-quantity clothing sales in Nov-2022**
```sql
SELECT * FROM retail_sales3 WHERE category='Clothing' AND MONTH(sale_date) = 11 AND quantiy >= 4;
```
To identify strong seasonal or promotional product segments.

#### Q3. **Net sales by category**
```sql
SELECT category, SUM(total_sale) net_sales , COUNT(*) total_orders FROM retail_sales3 GROUP BY category;
```
Used to evaluate product category performance.

#### Q4. **Average age of Beauty product customers**
```sql
SELECT ROUND(AVG(age)) FROM retail_sales3 WHERE category = 'Beauty';
```
Informs demographic targeting for cosmetics marketing.

#### Q5. **Transactions with total sales > $1000**
```sql
SELECT * FROM retail_sales3 WHERE total_sale > 1000;
```
Finds high-value transactions likely linked to premium products or loyal customers.

#### Q6. **Sales count by gender and category**
```sql
SELECT category, gender, COUNT(transactions_id) FROM retail_sales3 GROUP BY category, gender;
```
Useful for gender-based marketing insights.

#### Q7. **Best-selling months (based on average sales)**
```sql
-- Uses RANK to find top 2 average sale months
```
Helps uncover seasonal patterns to optimize inventory and campaigns.

#### Q8. **Top 5 customers by total purchase value**
```sql
SELECT customer_id, SUM(total_sale) total_sale FROM retail_sales3 GROUP BY customer_id ORDER BY total_sale DESC LIMIT 5;
```
Targets potential VIP customers.

#### Q9. **Unique customers per category**
```sql
SELECT category, COUNT(DISTINCT customer_id) FROM retail_sales3 GROUP BY category;
```
Determines category-wise reach.

#### Q10. **Sales by time shift (Morning, Afternoon, Evening)**
```sql
-- Uses HOUR() to split sales into three shifts
```
Supports resource planning and time-based promotions.

---

## 🔍 Key Findings

- **Clothing and Electronics** are leading in total sales.
- **November** is a high-value sales month, potentially linked to holiday promotions.
- **Beauty products** attract a younger customer demographic.
- Sales are concentrated in the **Afternoon** and **Evening** shifts.
- Top 5 customers contribute a significant share of total revenue.

---

## 📬 Contact

**Name:** Shounak Kapoor  
**Email:** Shounakkapoor1410@gmail.com  
**LinkedIn:** [Insert your LinkedIn profile link]

---

## 🧠 Final Note

This project is intended to demonstrate fundamental and intermediate-level SQL capabilities. You can fork or clone this project to practice queries or expand the dataset further with joins, views, or stored procedures.

Feel free to star ⭐ and share if you found this helpful!