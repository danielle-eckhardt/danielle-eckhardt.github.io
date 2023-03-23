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
India,
Indonesia,
Japan,
Philiphines,
South Korea,
Australia,
Newzealand,
Bangladesh

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
| percentage_chg | unique_products_2020 | unique_products_2021 |
| :---:          | :---:                | :---:                |
| 59.7793        | 363523               | 608108               |

Instead of creating two temporary tables calculating the unique product count for each year and then using a JOIn statement, I used CASE WHEN to simplify my query.

3. Provide a report with all the unique product counts for each segment and sort them in descending order of product counts.

```SQL
SELECT count(product_code) as product, segment
FROM dim_product
GROUP BY segment
ORDER BY count(product_code) DESC;
```
| product | segment |
| :---:   | :---: |
|129	| Notebook |
|116	| Accessories |
|84	| Peripherals |
|32	| Desktop |
|27	| Storage |
|9	| Networking |

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
| segment | product_count_2020 | product_count_2021 | difference |
| :---:   | :---: | :---:  | :---: |
| Networking |	11216	| 16929	| 5713 |
| Storage	| 22453	| 31977	| 9524 |
| Desktop	| 2026 | 30734 | 28708 |
| Peripherals	| 102878 | 141045 | 38167 |
| Accessories	| 112763 | 193598 | 80835 |
| Notebook	| 112187 | 193825 | 81638 |

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
| product_code | product | manufacturing_cost |
| :---:   | :---: | :---:  |
| A2118150101 | AQ Master wired x1 Ms | 0.8920 |
| A6120110206 | AQ HOME Allin1 Gen 2 | 240.5364 |

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
