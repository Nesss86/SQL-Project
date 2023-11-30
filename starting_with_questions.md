Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
##SELECT country,CAST(total_transaction_revenue AS money) AS total_revenue
  FROM all_sessions
  WHERE country IS NOT NULL
  AND total_transaction_revenue IS NOT NULL
  ORDER BY country DESC, total_transaction_revenue DESC


Answer: USA




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
##CREATE TEMPORARY TABLE Question_2 AS 
SELECT all_sessions.country, all_sessions.product_sku AS sku_1, sales_report.name,  AVG(sales_report.total_ordered), sales_report.product_sku AS sku_2
FROM all_sessions
RIGHT JOIN sales_report
ON all_sessions.product_sku = sales_report.product_sku
WHERE country IS NOT NULL
AND country != '(not set)'
GROUP BY all_sessions.country, all_sessions.product_sku, sales_report.name,sales_report.product_sku 
ORDER BY country ASC
LIMIT 50




Answer:The query generated all of the countries and products purchased on average





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
##SELECT country, v2_product_category, COUNT(*) AS category_count
  FROM all_sessions
  WHERE v2_product_category != '(not set)'
  GROUP BY v2_product_category, country
  ORDER BY category_count DESC
  LIMIT 50



Answer:The query generated the top 50 products and ordered it by the category to show that United States had the highest amount of purchases in the top 50 product categories which makes sense considering they generated the most revenue





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
##SELECT all_sessions.country, all_sessions.product_sku AS sku_1, sales_report.name, sales_report.total_ordered, sales_report.product_sku AS sku_2
FROM all_sessions
RIGHT JOIN sales_report
ON all_sessions.product_sku = sales_report.product_sku
WHERE country IS NOT NULL
AND country != '(not set)'
GROUP BY all_sessions.country, all_sessions.product_sku, sales_report.name,sales_report.product_sku, sales_report.total_ordered
ORDER BY total_ordered DESC



Answer:The top selling product from each country appeared to be the ballpoint LED Light Pen





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:I tripped up on the wording and was unsure how to answer this correctly








