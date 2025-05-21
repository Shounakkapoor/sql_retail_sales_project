
# 🛒 Retail Sales Analysis — SQL Project

This project is a **retail sales analysis** performed using SQL. The goal is to explore, clean, and analyze a retail transaction dataset to answer real business questions such as identifying best-selling products, customer behavior, and sales trends.

---

## 📁 Project Structure

- **`SQL - Retail Sales Analysis_utf .csv`** — Raw dataset used in the project.
- **`Project 1.sql`** — SQL script for database creation, data cleaning, and analysis.
- **`README.md`** — This documentation.

---

## 🧰 Tools Used

- SQL (MySQL or any standard RDBMS)
- SQL Workbench / DBeaver (or any IDE of choice)

---

## 🛠️ Steps in the Project

### 🔹 1. Database and Table Creation

```sql
CREATE DATABASE Portfolio_Project;

CREATE TABLE retail_sales3(
	transactions_id INT,
	sale_date DATE,
	sale_time TIME,
	customer_id INT,
	gender VARCHAR(20),
	age INT,
	category VARCHAR(20),
	quantiy FLOAT,
	price_per_unit FLOAT,
	cogs FLOAT,
	total_sale FLOAT
);
```

---

### 🔹 2. Data Cleaning

```sql
DELETE FROM retail_sales3
WHERE
	age IS NULL
	OR
	cogs IS NULL
	OR
	sale_date IS NULL
	OR
	quantiy IS NULL;
```

---

### 🔹 3. Exploratory Data Analysis

#### 🔸 Total Sales

```sql
SELECT
	COUNT(*) AS total_sales
FROM retail_sales3;
```

#### 🔸 Unique Customers

```sql
SELECT
	COUNT(DISTINCT customer_id) AS total_customers
FROM retail_sales3;
```

#### 🔸 Unique Product Categories

```sql
SELECT
	COUNT(DISTINCT category) AS unique_categories
FROM retail_sales3;
```

---

## ❓ Business Questions and Answers

### Q1: Sales made on 2022-11-05

```sql
SELECT *
FROM retail_sales3
WHERE sale_date = '2022-11-05';
```
✅ Returns detailed info on each sale made on this specific date.

### Q2: 'Clothing' sales with quantity > 4 in Nov 2022

```sql
SELECT *
FROM retail_sales3
WHERE
	category = 'Clothing'
	AND
	MONTH(sale_date) = 11
	AND
	quantiy >= 4;
```
✅ Useful for seasonal inventory and promotional analysis.

### Q3: Total sales per category

```sql
SELECT
	category,
	SUM(total_sale) AS net_sales,
	COUNT(*) AS total_orders
FROM retail_sales3
GROUP BY category;
```
✅ Identifies top revenue-generating product categories.

### Q4: Average age of customers who bought 'Beauty'

```sql
SELECT ROUND(AVG(age)) AS average_age
FROM retail_sales3
	WHERE category = 'Beauty';
```
✅ Helps target marketing campaigns by age segment.

### Q5: Transactions where total_sale > 1000

```sql
SELECT *
FROM retail_sales3
	WHERE total_sale > 1000;
```
✅ Pinpoints high-value orders, possibly by VIP customers

### Q6: Total transactions by gender and category

```sql
SELECT category, gender, COUNT(transactions_id)
FROM retail_sales3
GROUP BY category, gender
ORDER BY category;
```
✅ Reveals which products appeal more to each gender.

### Q7: Average monthly sale and best-selling months

```sql
SELECT year, month, avg_sale
FROM (
	SELECT
		YEAR(sale_date) AS year,
		MONTH(sale_date) AS month,
		ROUND(AVG(total_sale)) AS avg_sale,
		RANK() OVER(ORDER BY AVG(total_sale) DESC) AS best_selling_months
	FROM retail_sales3
	GROUP BY YEAR(sale_date), MONTH(sale_date)
) T1
WHERE best_selling_months IN (1, 2);
```
✅ Highlights seasonal trends to plan inventory.

### Q8: Top 5 customers by total sales

```sql
SELECT
	customer_id,
	SUM(total_sale) AS total_sale
FROM retail_sales3
GROUP BY customer_id
ORDER BY total_sale DESC
LIMIT 5;
```
✅ Identifies most valuable customers for loyalty programs.

### Q9: Unique customers per category

```sql
SELECT
	category,
	COUNT(DISTINCT customer_id) AS unique_customers
FROM retail_sales3
GROUP BY category;
```
✅ Shows which product categories attract more diverse buyers.

### Q10: Orders by time shift

```sql
SELECT 
	CASE
		WHEN HOUR(sale_time) < 12 THEN 'Morning'
		WHEN HOUR(sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
		ELSE 'Evening'
	END AS shift,
	COUNT(transactions_id) AS total_orders
FROM retail_sales3
GROUP BY shift;
```
✅ Useful to optimize staffing and offers for different time slots.

---
## 💡 Key Insights

Clothing and Electronics are top-selling categories.

Most sales happen in the Afternoon and Evening.

November sees high-value orders, possibly due to Black Friday.

Customer age trends differ per category—valuable for targeting.

## 📌 How to Run This Project

Import the dataset into your SQL environment.

Run the Project 1.sql file in sequence.

Modify queries to answer your own business questions!

## 📬 Contact

For any questions, feel free to connect:

**Author:** Shounak Kapoor  
**Email:** ShounakKapoor1410@gmail.com  
**LinkedIn:** https://ca.linkedin.com/in/shounak-kapoor-0bb32b2a7  
