## Music Store Sales: An analysis using SQL

### Project Description ### 
In this case study, I am tasked with analyzing and providing actionable insights to a music store on various aspects of their business operations. Specifically, my goal is to dive deep into their employee performance, customer demographics and behavior, as well as invoice and music characteristics, to help the store make data-driven decisions to optimize their business and increase profitability.

### Data Set ###
This data set came from the [SQLite Sample Database](https://www.sqlitetutorial.net/sqlite-sample-database/#:~:text=The%20name%20of%20the%20file%20is%20chinook.db%20If,download%20a%20free%20zip%20software%20such%20as%207-zip.). This data was analyzed on **SQLiteStudio (3.4.3)**.

### Data Structure ###
[Schema Diagram](https://www.sqlitetutorial.net/wp-content/uploads/2018/03/sqlite-sample-database-diagram.pdf):
![image](https://user-images.githubusercontent.com/123992539/227369420-81337f1b-b5c1-4735-8a61-9bf4e0abd4dc.png)


### Insights ###
1. Show Customers (their full names, customer ID, and country) who are not in the US.
```SQL
SELECT customerID, firstname, lastname, country
FROM chinook.customers
WHERE Country <> 'USA';
```
![image](https://user-images.githubusercontent.com/123992539/227374835-c242f79c-7d49-4217-abe8-3169b418bd9a.png)


2. Find the Invoices of customers who are from Brazil.
```SQL
SELECT c.customerID, c.firstname, c.lastname, c.country, i.invoiceID, i.InvoiceDate, i.BillingCountry
FROM chinook.customers c
INNER JOIN chinook.invoices i
ON c.customerID = i.customerID
WHERE Country = 'Brazil';
```
![image](https://user-images.githubusercontent.com/123992539/227375019-efd79a64-252a-4960-b47f-ffa7c6f2cae4.png)

3. Show the Employees who are Sales Agents.
```SQL
SELECT employeeID, firstname, lastname, title
FROM chinook.employees
WHERE title LIKE '%Sales%Agent%';
```
![image](https://user-images.githubusercontent.com/123992539/227375079-50117ca1-a22a-47db-94ba-e062ac4ea4dd.png)

4. Find a unique list of billing countries from the Invoice table.
```SQL
SELECT DISTINCT billingcountry
FROM chinook.invoices;
```
![image](https://user-images.githubusercontent.com/123992539/227375164-e234f40e-dcc4-47f3-adbe-cf06e66a8ac7.png)


5. Show the Invoice Total, Customer name, Country, and Sales Agent name for all invoices and customers.
```SQL
SELECT i.total as InvoiceTotal, c.FirstName || ' ' || c.LastName as CustomerName, c.Country, e.FirstName || ' ' || e.LastName as SalesAgentName
FROM chinook.invoices i
JOIN chinook.customers c
ON i.CustomerId = c.CustomerId
JOIN chinook.employees e
ON e.EmployeeId = c.SupportRepId
WHERE e.Title LIKE '%Sales%Agent%';
```
![image](https://user-images.githubusercontent.com/123992539/227375410-68bd03ff-b6ff-4278-9359-8ce2908af1a4.png)

6. How many Invoices and what are the total sales in 2009?
```SQL
SELECT count(invoiceID) as Total_Invoices_2009, sum(total) as Total_sales_2009
FROM chinook.invoices 
WHERE invoicedate BETWEEN '2009-01-01' AND '2009-12-31';
```
![image](https://user-images.githubusercontent.com/123992539/227375669-fbcc939b-8a2c-4a8f-9e3c-733e77a6eacb.png)

7. Write a query that includes the purchased track name AND artist name with each invoice line ID.
```SQL
SELECT i.InvoiceLineID, t.Name as TrackName, a.Name as ArtistName
FROM chinook.tracks t
JOIN chinook.invoice_items i
ON t.TrackId = i.TrackId
JOIN chinook.albums alb
ON alb.AlbumId = t.AlbumId
JOIN chinook.artists a
ON a.ArtistId = alb.ArtistId
ORDER BY i.InvoiceLineID;
```
![image](https://user-images.githubusercontent.com/123992539/227375816-3904cba2-a919-4c1a-85d8-d309e75ab710.png)

8. Provide a query that shows all the Tracks, and include the Album name, Media type, and Genre.
```SQL
SELECT t.Name as TrackName, a.Title as AlbumTitle, m.Name as MediaType, g.Name as Genre
FROM chinook.tracks t
JOIN chinook.albums a
ON t.AlbumId = a.AlbumId
JOIN chinook.media_types m
ON m.MediaTypeId = t.MediaTypeId
JOIN chinook.genres g
ON t.GenreId = g.GenreId;
```
![image](https://user-images.githubusercontent.com/123992539/227375928-eeefc19d-e430-485c-ba9d-169d58c361c6.png)

9. Show the total sales made by each sales agent.
```SQL
SELECT e.LastName, e.FirstName, sum(i.total) as TotalSales
FROM chinook.employees e
JOIN chinook.customers c
ON e.employeeID = c.supportrepid
JOIN chinook.invoices i
ON i.customerID = c.customerID
WHERE e. Title LIKE '%Sales%Agent%'
GROUP BY e.LastName, e.FirstName;
```
![image](https://user-images.githubusercontent.com/123992539/227375982-3eecd1ed-8332-4036-978c-c32186398eee.png)

10. Which sales agent made the most dollars in sales in 2009?
```SQL
SELECT e.LastName, e.FirstName, 
SUM(CASE WHEN i.invoicedate BETWEEN '2009-01-01' AND '2009-12-31' THEN i.total END) as '2009_Sales'
FROM chinook.employees e
JOIN chinook.customers c
ON e.employeeID = c.supportrepid
JOIN chinook.invoices i
ON i.customerID = c.customerID
WHERE e. Title LIKE '%Sales%Agent%'
GROUP BY e.LastName, e.FirstName
ORDER BY 2009_sales
LIMIT 1;
```
![image](https://user-images.githubusercontent.com/123992539/227376103-df542061-3364-469e-91d5-da82a12f65c0.png)
