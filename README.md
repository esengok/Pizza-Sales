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
