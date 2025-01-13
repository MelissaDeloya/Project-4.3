# Project-4.3
SQLIte Studio Practice
-- Project 4.3
--How many orders were placed in January?
SELECT COUNT(orderid)
FROM BIT_DB.JanSales
WHERE length(orderid) = 6
AND orderid <> 'Order ID';

--How many of those orders were for an iPhone?

SELECT COUNT(orderid)
FROM BIT_DB.JanSales
WHERE Product='iPhone'
AND length(orderid) = 6
AND orderid <> 'Order ID';

--Select the customer account numbers for all the orders that were placed in February.

SELECT distinct acctnum
FROM BIT_DB.customers cust
INNER JOIN BIT_DB.FebSales Feb
ON cust.order_id=FEB.orderid
WHERE length(orderid) = 6
AND orderid <> 'Order ID';

--Which product was the cheapest one sold in January, and what was the price?

SELECT distinct Product, price
FROM BIT_DB.JanSales
WHERE price in (SELECT min(price) FROM BIT_DB.JanSales);

SELECT distinct product, price
FROM BIT_DB.JanSales 
ORDER BY price ASC LIMIT 1;

--What is the total revenue for each product sold in January?
(Revenue can be calculated using the number of products sold and the price of the products).acctnum

SELECT sum(quantity)* price as revenue, product
FROM BIT_DB.JanSales
GROUP BY product;

SELECT orderid, quantity, price, product
FROM BIT_DB.JanSales;

--Which products were sold in February at 548 Lincoln St, Seattle, WA 98101, 
--how many of each were sold, and what was the total revenue?

SELECT product , sum(Quantity),sum(quantity)* price as revenue
FROM BIT_DB.FebSales
WHERE location = '548 Lincoln St, Seattle, WA 98101';

--How many customers ordered more than 2 products at a time in February, 
--and what was the average amount spent for those customers?

SELECT
count(distinct cust.acctnum),
avg(quantity*price)
FROM BIT_DB.FebSales Feb
LEFT JOIN BIT_DB.customers cust

--List all the products sold in Los Angeles in February, and include how many of each were sold.
SELECT Product, SUM(quantity)
FROM BIT_DB.FebSales

SELECT orderdate from BIT_DB.FebSales
WHERE orderdate like '02/18/19%'

SELECT distinct Product
FROM BIT_DB.FebSales
WHERE Product like '%Batteries%'

##2. 
SELECT distinct Product, Price
FROM BIT_DB.FebSales 
WHERE Price like '%.99'

--List all the products sold in Los Angeles in February, and include how many of each were sold.

SELECT Product, SUM(quantity)
FROM BIT_DB.FebSales
WHERE location like '%Los Angeles%'
GROUP BY Product;
WHERE location like '%Los Angeles%'
GROUP BY Product;
ON FEB.orderid=cust.order_id
WHERE Feb.Quantity>2
AND length(orderid) = 6
AND orderid <> 'Order ID';

--Which locations in New York received at least 3 orders in January, 
--and how many orders did they each receive? (Hint: use HAVING).

SELECT distinct location, count(orderID)
FROM BIT_DB.JanSales
WHERE location like '%New York%'
AND length(orderid) = 6 
AND orderid <> 'Order ID'
GROUP BY location
HAVING count(orderID)>2;

--How many of each type of headphone were sold in February?
SELECT SUM(quantity) as Quantity , product
FROM BIT_DB.FebSales
WHERE product like '%Headphone%'
GROUP BY product; 

--What was the average amount spent per account in February? 
--(Hints: For this question, we want the average amount spent / number of accounts, 
--not the amount spent by each account. To multiply, you can use the 
--* symbol, and to divide, you can use the / symbol.)

SELECT avg(quantity*price)
FROM BIT_DB.FebSales Feb

LEFT JOIN BIT_DB.customers cust
ON FEB.orderid=cust.order_id

WHERE length(orderid) = 6 
AND orderid <> 'Order ID'

--What was the average quantity of products purchased per account in February? 
--(Hint: just like question 3, we want the overall average, not the average for each account individually).

SELECT sum(quantity)/count(cust.acctnum)
FROM BIT_DB.FebSales Feb

LEFT JOIN BIT_DB.customers cust
ON FEB.orderid=cust.order_id

WHERE length(orderid) = 6 
AND orderid <> 'Order ID';

--Which product brought in the most revenue in January and how much revenue did it bring in total?

SELECT product,
sum(quantity*price)
FROM BIT_DB.JanSales
ORDER BY sum(quantity*price) desc
LIMIT 1

--Which locations in New York received at least 3 orders in January, 
--and how many orders did they each receive? (Hint: use HAVING).

SELECT distinct location, count(orderID)
FROM BIT_DB.JanSales
WHERE location like '%New York%'
AND length(orderid) = 6 
AND orderid <> 'Order ID'
GROUP BY location
HAVING count(orderID)>2;

--How many of each type of headphone were sold in February?
SELECT SUM(quantity) as Quantity , product
FROM BIT_DB.FebSales
WHERE product like '%Headphone%'
GROUP BY product; 

--What was the average amount spent per account in February? 
--(Hints: For this question, we want the average amount spent / number of accounts, 
--not the amount spent by each account. To multiply, you can use the 
--* symbol, and to divide, you can use the / symbol.)

SELECT avg(quantity*price)
FROM BIT_DB.FebSales Feb

LEFT JOIN BIT_DB.customers cust
ON FEB.orderid=cust.order_id

WHERE length(orderid) = 6 
AND orderid <> 'Order ID'

--What was the average quantity of products purchased per account in February? 
--(Hint: just like question 3, we want the overall average, not the average for each account individually).

SELECT sum(quantity)/count(cust.acctnum)
FROM BIT_DB.FebSales Feb

LEFT JOIN BIT_DB.customers cust
ON FEB.orderid=cust.order_id

WHERE length(orderid) = 6 
AND orderid <> 'Order ID';

--Which product brought in the most revenue in January and how much revenue did it bring in total?

SELECT product,
sum(quantity*price)
FROM BIT_DB.JanSales
ORDER BY sum(quantity*price) desc
LIMIT 1


