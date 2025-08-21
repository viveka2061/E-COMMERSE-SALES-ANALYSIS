CREATE DATABASE ecommerce;
USE ecommerce;


# Create the table:

CREATE TABLE sales_data (
InvoiceNo VARCHAR(20),
StockCode VARCHAR(20),
Description TEXT,
Quantity INT,
InvoiceDate DATETIME,
UnitPrice FLOAT,
CustomerID VARCHAR(20),
Country VARCHAR(100)
);

# 1. Analyze Monthly Order Trends 
SELECT MONTH(InvoiceDate) AS Month,
COUNT(DISTINCT InvoiceNo) AS TotalOrders
FROM sales_data
GROUP BY
MONTH(InvoiceDate)
ORDER BY
Month;

# 2. Calculate Monthly Revenue Growth
SELECT MONTH(InvoiceDate) AS Month,
ROUND(SUM(UnitPrice * Quantity), 2) AS Revenue
FROM sales_data
GROUP BY
MONTH(InvoiceDate)
ORDER BY
Month;

# 3. Top 5 Best-Selling Products (by Quantity)
SELECT Description,
SUM(Quantity) AS TotalQuantity
FROM sales_data
GROUP BY
Description
ORDER BY
TotalQuantity DESC
LIMIT 5;

# 4. Find Top 5 Products by Total Revenue
SELECT Description,
ROUND(SUM(Quantity * UnitPrice), 2) AS Revenue
FROM sales_data
GROUP BY
Description
ORDER BY
Revenue DESC
LIMIT 5;

# 5. Top Countries by Sales
SELECT [archive.zip](https://github.com/user-attachments/files/21912826/archive.zip)
Country,
ROUND(SUM(Quantity * UnitPrice), 2) AS Revenue
FROM sales_data
GROUP BY
Country ORDER BY
Revenue DESC
LIMIT 5;
