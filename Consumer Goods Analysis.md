## Consumer Goods: An analysis using SQL

### Project Description ### 
In this case study, I am hired at Atliq Hardwares (imaginary company), one of the leading computer hardware producers in India and well expanded in other countries too. The management noticed that they do not get enough insights to make quick and smart data-informed decisions.  Here, I showcase my skills completing 10 ad hoc requests to help the business have some insights on the data.

### Data Set ###
This database and data sets came from a [Code Basics](https://codebasics.io/challenge/codebasics-resume-project-challenge) challenge. The data was analyzed on **MySQL Workbench 8.0 CE**.

### Data Structure ###
Tables:
1. dim_customer: contains customer-related data <br>
```Columns: customer_code, customer, platform, channel, market, region, sub_zone```
2. dim_product: contains product-related data <br>
```Columns: product_code, division, segment, category, product, variant```
3. fact_gross_price: contains gross price information for each product <br>
```Columns: product_code, fiscal_year, gross_price```
4. fact_manufacturing_cost: contains the cost incurred in the production of each product <br>
```Columns: product_code, cost_year, manufacturing_cost```
5. fact_pre_invoice_deductions: contains pre-invoice deductions information for each product <br>
```Columns: customer_code, fiscal_year, pre_invoice_discount_pct```
6. fact_sales_monthly: contains monthly sales data for each product <br>
```Columns: date, product_code, customer_code, sold_quantity, fiscal_year```

### Ad Hoc Requests ###

1. Provide the list of markets in which customer "Atliq Exclusive" operates its
business in the APAC region.

```SQL
SELECT DISTINCT market
FROM dim_customer
WHERE customer = "Atliq Exclusive" AND region = "APAC";
```
![image](https://user-images.githubusercontent.com/123992539/227342232-876fd70e-eeba-4ac4-98a1-b658e82ac469.png) <br>
Since the market 'India' appears twice in the dataset, I used the 'DISTINCT' command to return all markets whose customer is "Atliq Exclusive" and operates its business in the APAC region.

2. What is the percentage of unique product increase in 2021 vs. 2020?

```SQL
SELECT 
    (COUNT(CASE WHEN fiscal_year = 2020 THEN product_code END) / COUNT(CASE WHEN fiscal_year = 2021 THEN product_code END)) * 100 AS percentage_chg,
    COUNT(CASE WHEN fiscal_year = 2020 THEN product_code END) AS unique_products_2020,
    COUNT(CASE WHEN fiscal_year = 2021 THEN product_code END) AS unique_products_2021
FROM 
    fact_sales_monthly
WHERE 
    fiscal_year IN (2020, 2021);
```
![image](https://user-images.githubusercontent.com/123992539/227342694-136fd2c6-e58c-498e-8608-da2852c05070.png) <br>
Instead of creating two temporary tables calculating the unique product count for each year and then using a JOIN statement, I used CASE WHEN to simplify my query.


3. Provide a report with all the unique product counts for each segment and sort them in descending order of product counts.

```SQL
SELECT count(product_code) as product, segment
FROM dim_product
GROUP BY segment
ORDER BY count(product_code) DESC;
```
![image](https://user-images.githubusercontent.com/123992539/227343142-04eb53cb-3913-47d4-9eb8-81e9ae2cfd6d.png) <br>


4. Follow-up: Which segment had the most increase in unique products in 2021 vs 2020?

```SQL
SELECT 
  p.segment, 
  COUNT(CASE WHEN fiscal_year = 2020 THEN s.product_code END) AS product_count_2020,
  COUNT(CASE WHEN fiscal_year = 2021 THEN s.product_code END) AS product_count_2021,
  COUNT(CASE WHEN fiscal_year = 2021 THEN s.product_code END) - COUNT(CASE WHEN fiscal_year = 2020 THEN s.product_code END) AS difference
FROM 
  fact_sales_monthly s
  LEFT JOIN dim_product p ON s.product_code = p.product_code
WHERE 
  fiscal_year IN (2020, 2021)
GROUP BY 
  p.segment
ORDER BY 
  difference;
```
![image](https://user-images.githubusercontent.com/123992539/227343247-dae13bf1-d32b-44ee-9d74-f7d08825e336.png) <br>


5. Get the products that have the highest and lowest manufacturing costs.

```SQL
SELECT 
  d.product_code, 
  d.product, 
  f.manufacturing_cost
FROM 
  fact_manufacturing_cost f 
  JOIN dim_product d ON f.product_code = d.product_code 
WHERE 
  f.manufacturing_cost = (
    SELECT 
      MAX(manufacturing_cost) 
    FROM 
      fact_manufacturing_cost
  ) 
  OR 
  f.manufacturing_cost = (
    SELECT 
      MIN(manufacturing_cost) 
    FROM 
      fact_manufacturing_cost
  )
ORDER BY 
  f.manufacturing_cost;
```
![image](https://user-images.githubusercontent.com/123992539/227343383-c86a618b-1d5a-469d-985e-cdb43cf1153d.png)<br>


6. Generate a report which contains the top 5 customers who received an average high pre_invoice_discount_pct for the fiscal year 2021 and in the Indian market.

```SQL
SELECT f.customer_code, d.customer, avg(f.pre_invoice_discount_pct) as average_discount_percentage
FROM fact_pre_invoice_deductions f
JOIN dim_customer d
ON f.customer_code = d.customer_code
WHERE f.fiscal_year = 2021 AND d.sub_zone = 'India'
GROUP BY f.customer_code, d.customer
ORDER BY average_discount_percentage DESC
LIMIT 5;
```
![image](https://user-images.githubusercontent.com/123992539/227343503-368368bc-9fce-4877-96eb-87eee0642219.png) <br>

7. Get the complete report of the Gross sales amount for the customer “Atliq Exclusive” for each month. This analysis helps to get an idea of low and high-performing months and take strategic decisions.

```SQL
SELECT extract(year from date) as year, extract(month from date) as month, sum(fgp.gross_price * fsm.sold_quantity) as GrossSalesAmount
FROM fact_gross_price fgp
JOIN fact_sales_monthly fsm
ON fgp.product_code = fsm.product_code
JOIN dim_customer dm
ON dm.customer_code = fsm.customer_code
WHERE dm.customer = 'Atliq Exclusive'
GROUP BY year, month
ORDER BY year, month;
```
![image](https://user-images.githubusercontent.com/123992539/227344870-a8ce45ce-c59b-41e2-ae6a-5e758f9bb7fd.png)<br>

8. In which quarter of 2020, got the maximum total_sold_quantity?

```SQL
SELECT DISTINCT
  quarter(date) AS Quarter,
  SUM(sold_quantity) OVER (PARTITION BY quarter(date)) AS total_sold_quantity
FROM fact_sales_monthly
WHERE fiscal_year = 2020
ORDER BY total_sold_quantity DESC
LIMIT 1;
```
![image](https://user-images.githubusercontent.com/123992539/227345994-931a4baf-e4e7-4979-8e46-dc8da3f67192.png)<br>

9. Which channel helped to bring more gross sales in the fiscal year 2021 and the percentage of contribution?

```SQL
SELECT 
  d.channel, 
  SUM(fgp.gross_price * fsm.sold_quantity) AS gross_sales_mln, 
 (SUM(fgp.gross_price * fsm.sold_quantity) / SUM(SUM(fgp.gross_price * fsm.sold_quantity)) OVER ()) * 100 AS percentage
FROM 
  dim_customer d
  JOIN fact_sales_monthly fsm ON d.customer_code = fsm.customer_code
  JOIN fact_gross_price fgp ON fgp.product_code = fsm.product_code
WHERE 
  fsm.fiscal_year = 2021
GROUP BY 
  d.channel;
```
![image](https://user-images.githubusercontent.com/123992539/227347040-3e7d4e9d-f3e5-4395-8c2f-ba06286f7345.png)<br>

10. Get the Top 3 products in each division that have a high total_sold_quantity in the fiscal_year 2021?

```SQL
SELECT 
  division, 
  product_code, 
  product, 
  total_sold_quantity, 
  rank_no
FROM (
  SELECT 
    d.division, 
    d.product_code, 
    d.product, 
    SUM(fsm.sold_quantity) AS total_sold_quantity, 
    RANK() OVER (PARTITION BY d.division ORDER BY SUM(fsm.sold_quantity) DESC) AS rank_no
  FROM 
    fact_sales_monthly fsm 
    JOIN dim_product d ON fsm.product_code = d.product_code 
  WHERE 
    fsm.fiscal_year = 2021
  GROUP BY 
    d.division, 
    d.product_code, 
    d.product
) AS t
WHERE 
  rank_no <= 3
ORDER BY 
  division, 
  rank_no;
```
![image](https://user-images.githubusercontent.com/123992539/227348170-e2aed1fe-ad06-407d-a940-3f00981d5da7.png) <br>
