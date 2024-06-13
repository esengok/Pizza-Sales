# Pizza-Sales

SELECT
SUM (total_price) AS Total_Revenue
FROM `pizzasales.pizzasales`




SELECT SUM(total_price) / COUNT (DISTINCT order_id) AS Avg_Order_Value

FROM `pizzasales.pizzasales`




SELECT SUM(quantity) AS Total_Pizza_Sold

FROM `pizzasales.pizzasales`






SELECT COUNT(DISTINCT order_id) AS Total_Orders

FROM `pizzasales.pizzasales`







SELECT
  FORMAT_DATE('%A', CAST(order_date AS DATE)) AS order_day, COUNT(DISTINCT order_id) AS Total_Orders
FROM `pizzasales.pizzasales`
GROUP BY order_day



SELECT ROUND(SUM(quantity) / COUNT(DISTINCT order_id), 2) AS Avg_Pizza

FROM `pizzasales.pizzasales`



SELECT
  FORMAT_DATE('%B', CAST(order_date AS DATE)) AS order_day, COUNT(DISTINCT order_id) AS Total_Orders
FROM `pizzasales.pizzasales`
GROUP BY order_day





SELECT 
    pizza_category,
   
    SUM(total_price) / (SELECT SUM(total_price) FROM `pizzasales.pizzasales`) * 100 AS Total_Sales
FROM 
    `pizzasales.pizzasales`

GROUP BY 
    pizza_category;







--choosing specific month (january)

    SELECT 
    EXTRACT(MONTH FROM TIMESTAMP(order_date)) AS sale_month,
    pizza_category,
    SUM(total_price) AS total_sales,
    SUM(total_price) / (SELECT SUM(total_price) FROM `pizzasales.pizzasales` WHERE EXTRACT(MONTH FROM TIMESTAMP(order_date)) = 01) * 100 AS sales_percentage
FROM 
    `pizzasales.pizzasales`
WHERE 
    EXTRACT(MONTH FROM TIMESTAMP(order_date)) = 01
GROUP BY 
    sale_month, pizza_category;






SELECT 
    pizza_size,
    
    SUM(total_price) / (SELECT SUM(total_price) FROM `pizzasales.pizzasales`) * 100 AS Total_Sales
    
FROM 
    `pizzasales.pizzasales`

GROUP BY 
    pizza_size;
