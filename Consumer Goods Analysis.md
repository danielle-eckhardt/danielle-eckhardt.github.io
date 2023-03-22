## Consumer Goods: An analysis using SQL

### Project Description ### 
In this case study, I am hired at Atliq Hardwares (imaginary company), one of the leading computer hardware producers in India and well expanded in other countries too. 
The management noticed that they do not get enough insights to make quick and smart data-informed decisions. 
Here, I showcase my skills completing 10 ad hoc requests to help the business have some insights on the data.

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
