## Music Store Sales: An analysis using SQL

### Project Description ### 
In this case study, I am tasked with analyzing and providing actionable insights to a music store on various aspects of their business operations. Specifically, my goal is to dive deep into their employee performance, customer demographics and behavior, as well as invoice and music characteristics, to help the store make data-driven decisions to optimize their business and increase profitability.

### Data Set ###
This data set came from the [SQLite Sample Database](https://www.sqlitetutorial.net/sqlite-sample-database/#:~:text=The%20name%20of%20the%20file%20is%20chinook.db%20If,download%20a%20free%20zip%20software%20such%20as%207-zip.). This data was analyzed on **SQLiteStudio (3.4.3)**.

### Data Structure ###
Schema Diagram:
![image](https://user-images.githubusercontent.com/123992539/227369420-81337f1b-b5c1-4735-8a61-9bf4e0abd4dc.png)


### Insights ###
1. Show Customers (their full names, customer ID, and country) who are not in the US.
```SQL
SELECT customerID, firstname, lastname, country
FROM chinook.customers
WHERE Country <> 'USA';
```

2. Show only the Customers from Brazil.
```SQL
SELECT customerID, firstname, lastname, country
FROM chinook.customers
WHERE Country = 'Brazil';
```

3. Find the Invoices of customers who are from Brazil.
```SQL
SELECT c.customerID, c.firstname, c.lastname, c.country, i.invoiceID, i.InvoiceDate, i.BillingCountry
FROM chinook.customers c
INNER JOIN chinook.invoices i
ON c.customerID = i.customerID
WHERE Country = 'Brazil';
```

4. Show the Employees who are Sales Agents.
```SQL
SELECT employeeID, firstname, lastname, title
FROM chinook.employees
WHERE title LIKE '%Sales%Agent%';
```

5. Find a unique/distinct list of billing countries from the Invoice table.
```SQL
SELECT DISTINCT billingcountry
FROM chinook.invoices;
```

6. Provide a query that shows the invoices associated with each sales agent. 
```SQL
SELECT i.invoiceID, (e.FirstName || ' ' || e.LastName) as SalesAgentName
FROM chinook.invoices i
JOIN chinook.customers c
ON i.CustomerID = c.CustomerId
JOIN chinook.employees e
ON e.EmployeeId = c.SupportRepId
WHERE e.title LIKE '%Sales%Agent%';
```


7. Show the Invoice Total, Customer name, Country, and Sales Agent name for all invoices and customers.
```SQL
SELECT i.total as InvoiceTotal, c.FirstName || ' ' || c.LastName as CustomerName, c.Country, e.FirstName || ' ' || e.LastName as SalesAgentName
FROM chinook.invoices i
JOIN chinook.customers c
ON i.CustomerId = c.CustomerId
JOIN chinook.employees e
ON e.EmployeeId = c.SupportRepId
WHERE e.Title LIKE '%Sales%Agent%';
```

8. How many Invoices were there in 2009?
```SQL
SELECT count(invoiceID)
FROM chinook.invoices 
WHERE invoicedate BETWEEN '2009-01-01' AND '2009-12-31';
```

9. What are the total sales for 2009?
```SQL
SELECT sum(total) as Total_sales_2009
FROM chinook.invoices 
WHERE invoicedate BETWEEN '2009-01-01' AND '2009-12-31';
```


10. Write a query that includes the purchased track name with each invoice line ID.
```SQL
SELECT t.Name as TrackName, i.InvoiceLineID
FROM chinook.tracks t
JOIN chinook.invoice_items i
ON t.TrackId = i.TrackId;
```

11. Write a query that includes the purchased track name AND artist name with each invoice line ID.
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

12. Provide a query that shows all the Tracks, and include the Album name, Media type, and Genre.
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


13. Show the total sales made by each sales agent.
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

14. Which sales agent made the most dollars in sales in 2009?
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
