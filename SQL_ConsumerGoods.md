## Consumer Goods: An analysis using SQL

**Project description:** In this case study, I am hired as a marketing analyst to interpret the research about a company’s consumers and their buying habits. 

### Data Set
  This data set was analyzed in SQLiteStudio 3.4.3 and came from the [BreakIntoTech Data Analytics Course](https://howtobreakintotech.com/data-analytics-certificate-program/). 

[Link to Database File](https://www.dropbox.com/s/cvsasmtr8syq2c2/BIT_DB?dl=0)

**Database Structure** <br>
Database name: BIT_DB <br>
<br>
Tables:
<br>
JanSales (orderID INTEGER PRIMARY KEY, Product TEXT, Quantity INTEGER, price  DECIMAL, orderdate TEXT(mm-dd-yy hh:mm), location TEXT) <br>
FebSales (orderID INTEGER PRIMARY KEY, Product TEXT, Quantity INTEGER, price  DECIMAL, orderdate TEXT(mm-dd-yy hh:mm), location TEXT) <br>
MarSales (orderID INTEGER PRIMARY KEY, Product TEXT, Quantity INTEGER, price  DECIMAL, orderdate TEXT(mm-dd-yy hh:mm), location TEXT) <br>
AprSales (orderID INTEGER PRIMARY KEY, Product TEXT, Quantity INTEGER, price  DECIMAL, orderdate TEXT(mm-dd-yy hh:mm), location TEXT) <br>
MaySales (orderID INTEGER PRIMARY KEY, Product TEXT, Quantity INTEGER, price  DECIMAL, orderdate TEXT(mm-dd-yy hh:mm), location TEXT) <br>
customers (order_id INTEGER PRIMARY KEY, acctnum INTEGER)

### Analysis

- How many orders were placed in January?

```SQL
SELECT count(*)
FROM bit_db.jansales
WHERE length(orderID) = 6 
AND orderID <> 'Order ID'; 
```
Here, you can see in my code there was a bit of data cleaning that needed to be included to avoid mis-calculated results. There are several entries were the 'orderID' is not a proper 6 digit code and they needed to be filtered out in the calculation.

There are **9681** orders placed in January.

- How many of those orders were for an iPhone?

```SQL
SELECT count(*)
FROM bit_db.jansales
WHERE length(orderid) = 6 
AND orderid <> 'Order ID'
AND product = 'iPhone';
```
Using the same SQL code from the previous question, _but_ adding another extention to the WHERE statement with another AND clause I was able to filter out only the products that were iPhones. Of the 9681 orders, only **379** of them were iPhones.

### Key Takeaways

<img src="images/dummy_thumbnail.jpg?raw=true"/>
SQL is so versatile and can help us easily find the answers to some of the most important questions in a buisness. 
