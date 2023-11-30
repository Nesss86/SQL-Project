What are your risk areas? Identify and describe them.
Some of the risk areas I found in this database were the consistency of values in some of the columns. For example amongst the product_sku column were items identified by letter and items identified by number. The time column also seemed unreliable because not all of the values could be converted to time.


QA Process:
Describe your QA process and include the SQL queries used to execute it.

Some of the QA processes I employed did not results from an SQL query. In assessing the risk of ALTER TABLE as away to trim useless columns or data, I decided against it as I did not want to compromise the original data. To find a way around this I made a CTE which will be shown amongst the other queries I tried to convert the data type of the time column


##CREATE TEMPORARY TABLE Question_2 AS 
SELECT all_sessions.country, all_sessions.product_sku AS sku_1, sales_report.name, AVG(sales_report.total_ordered), sales_report.product_sku AS sku_2
FROM all_sessions
RIGHT JOIN sales_report
ON all_sessions.product_sku = sales_report.product_sku
WHERE country IS NOT NULL
AND country != '(not set)'
GROUP BY all_sessions.country, all_sessions.product_sku, sales_report.name,sales_report.product_sku 
ORDER BY country ASC


##SELECT full_visitor_id, channel_grouping,
  CAST(time AS TIME)
  AS new_time_column
  FROM all_sessions


##SELECT *
  FROM all_sessions
  WHERE CASE WHEN trim(both '' from time) ~'^\d{2}:\d{2}:d{2}$'
  THEN NULL
  ELSE CAST(time AS TIME)
  END IS NULL

SELECT *
FROM all_sessions
WHERE NOT(trim(both '' from time) ~ '^\d{2}:\d{2}:\d{2}$')