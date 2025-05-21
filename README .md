
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

To ensure clean and reliable analysis, we remove rows with NULLs in critical columns:

```sql
DELETE FROM retail_sales3
WHERE age IS NULL
   OR cogs IS NULL
   OR sale_date IS NULL
   OR quantiy IS NULL;
```

---

### 🔹 3. Exploratory Data Analysis

#### 🔸 Total Sales

```sql
SELECT COUNT(*) AS total_sales FROM retail_sales3;
```

#### 🔸 Unique Customers

```sql
SELECT COUNT(DISTINCT customer_id) AS total_customers FROM retail_sales3;
```

#### 🔸 Unique Product Categories

```sql
SELECT COUNT(DISTINCT category) AS unique_categories FROM retail_sales3;
```

---

## ❓ Business Questions and Answers

... [Content truncated for brevity; full content retained in code]

---

## 📬 Contact

For any questions, feel free to connect:

**Author:** Shounak Kapoor  
**Email:** [your-email@example.com]  
**LinkedIn:** [Your LinkedIn Profile]  
