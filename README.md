![Retail_store_sales_dashboard](https://github.com/user-attachments/assets/3a51dbc8-3c69-4aba-a6fd-5705673d67f9)

## Retail Store Sales Analysis
In this project, I combined the strengths of SQL for data extraction, Excel for cleaning and preliminary analysis, and Power BI for creating an interactive dashboard to uncover key business insights, such as:

✅ Total revenue generated

✅ Monthly revenue trends

✅ Top 5 best-selling product categories

✅ Customer demographics and purchase behavior

✅ Gender-wise purchasing patterns

✅ Order status distribution and sales channels

✅ Top-performing shipping states

✅ B2B vs B2C order and revenue comparison

##  Key Tools & Techniques Used:

SQL: Efficient data extraction and transformation

Excel: Data cleaning, validation

Power BI: Building dynamic, visual dashboards for storytelling and decision-making

Through this project, I strengthened my skills in:

Writing optimized SQL queries

Advanced Excel functions and data modeling

Designing visually compelling Power BI dashboards

Business trend analysis and strategic reporting

📈 I’m passionate about turning raw data into meaningful insights to drive smart business decisions.

## Here is SQL Query(PostgreSQL)
CREATE TABLE retail_store (

    index SERIAL PRIMARY KEY,
    order_id VARCHAR(50),
    cust_id VARCHAR(50),
    gender VARCHAR(10),
    age INTEGER,
    age_group VARCHAR(20),
    date DATE,
    month VARCHAR(20),
    status VARCHAR(20),
    channel VARCHAR(50),
    sku VARCHAR(50),
    category VARCHAR(50),
    size VARCHAR(20),
    qty INTEGER,
    currency VARCHAR(10),
    amount NUMERIC(12, 2),
    ship_city VARCHAR(100),
    ship_state VARCHAR(100),
    ship_postal_code VARCHAR(20),
    ship_country VARCHAR(50),
    b2b BOOLEAN
);


### Data Cleaning
SELECT * FROM retail_store

WHERE

    index IS NULL
	OR
	order_id IS NULL
	OR
	cust_id IS NULL
	OR
	gender IS NULL
	OR
	age IS NULL
	OR
	age_group IS NULL
	OR
	date IS NULL
	OR
	month IS NULL
	OR
	status IS NULL
	OR
	channel IS NULL
	OR
	sku IS NULL
	OR
	category IS NULL
	OR
	size IS NULL
	OR
	qty IS NULL
	OR
	currency IS NULL
	OR
	amount IS NULL
	OR
	ship_city IS NULL
	OR
	ship_postal_code IS NULL
	OR
	ship_country IS NULL
	OR
	b2b IS NULL;
------------------------------------------------------------------------------------------------------

### Data Exploration

### How many orders we have?

SELECT COUNT(order_id) 

FROM retail_store;

### How many unique customers we have?

SELECT COUNT(DISTINCT cust_id) 

FROM retail_store;

### How many unique category we have?
SELECT COUNT(DISTINCT category) 

FROM retail_store;

### How many unique category we have?

SELECT COUNT(DISTINCT channel)

FROM retail_store;

------------------------------------------------------------------------------------------------------
### Data Analysis & Business Key Problems & Answers

### Sales & Revenue

### Q1.Total revenue generated by the store

SELECT SUM(amount) AS total_revenue

FROM retail_store;

------------------------------------------------------------------------------------------------------
### Q2.Monthly trend revenue
SELECT 

    month,
    SUM(amount) AS monthly_revenue
FROM retail_store

GROUP BY month

ORDER BY CASE month

    WHEN 'January' THEN 1
    WHEN 'February' THEN 2
    WHEN 'March' THEN 3
    WHEN 'April' THEN 4
    WHEN 'May' THEN 5
    WHEN 'June' THEN 6
    WHEN 'July' THEN 7
    WHEN 'August' THEN 8
    WHEN 'September' THEN 9
    WHEN 'October' THEN 10
    WHEN 'November' THEN 11
    WHEN 'December' THEN 12
    ELSE 13 -- optional, in case month value is wrong
END;

-----------------------------------------------------------------------------------------------------

### Q3.Top 5 best-selling categories by quantity

SELECT 

     category,
	   SUM(qty) AS total_quantity
FROM retail_store

GROUP BY 1

ORDER BY 2 DESC

LIMIT 5;

----------------------------------------------------------------------------------------------------
### Customer & Demographics
### Q4.Number of unique customers

SELECT COUNT(DISTINCT cust_id) AS unique_cust

FROM retail_store;

---------------------------------------------------------------------------------------------------

### Q5.Sales distribution by age group

SELECT

     age_group,
	   SUM(amount) AS revenue
FROM retail_store

GROUP BY 1

ORDER BY 2 DESC;

---------------------------------------------------------------------------------------------------

### Q6.Gender-wise purchase summary
SELECT

     gender,
	   COUNT(*) AS orders,
	   SUM(amount) AS revenue
FROM retail_store

GROUP BY 1;

---------------------------------------------------------------------------------------------------
### Order Insights
### Q7.Order status distribution

SELECT

     status,
	   COUNT(*) AS order_count
FROM retail_store

GROUP BY 1;

---------------------------------------------------------------------------------------------------

### Q8.Most popular sales channel

SELECT 

     channel,
	   COUNT(*) AS orders
FROM retail_store

GROUP BY 1

ORDER BY 2 DESC;

----------------------------------------------------------------------------------------------------
### Geography-Based
### Q9.Top 5 shipping states by order volume

SELECT 

     ship_state,
	   COUNT(*) AS orders
FROM retail_store

GROUP BY 1

ORDER BY 2 DESC

LIMIT 5;

-------------------------------------------------------------------------------------------------

### Q10.B2B vs B2C order count and revenue
SELECT

     B2B,
	   COUNT(*) AS orders,
	   SUM(amount) AS revenue
FROM retail_store

GROUP BY 1;

-------------------------------------------------------------------------------------------------


💬 Always happy to connect with fellow data enthusiasts and professionals!

