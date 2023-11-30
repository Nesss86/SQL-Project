What issues will you address by cleaning the data?
##The issues I will address by cleaning the data are:
  -Ensuring proper data types for each column upon importing the database to Postgresql
  -Removing duplicates where necessary
  -Removing Nulls, 'not set' and "not available in demo dataset"
  -Determining if there are any anomalies by employing a case statement for product_variant






Queries:
Below, provide the SQL queries you used to clean your data.

##SELECT item_quantity, item_revenue, product_revenue, transaction_revenue, search_keyword,  ecommerce_action_option, transaction_id, product_refund_amount
FROM all_sessions
WHERE item_quantity IS NOT NULL
AND item_revenue IS NOT NULL
AND product_revenue IS NOT NULL
AND transaction_revenue IS NOT NULL
AND search_keyword IS NOT NULL
AND ecommerce_action_option IS NOT NULL
AND transaction_id IS NOT NULL

##SELECT DISTINCT city
  FROM all_sessions
  WHERE city != '(not set)' 
  AND city != 'not available in demo dataset'
  ORDER BY city ASC


##SELECT total_ordered
  FROM sales_report
  WHERE total_ordered IS NOT NULL


##SELECT name, ordered_quantity
  FROM products
  WHERE name IS NOT NULL 
  AND ordered_quantity IS NOT NULL



##SELECT
  CASE
  WHEN COUNT(DISTINCT product_variant) > 1 THEN
  'valid'
  ELSE 'error'
  END AS text_check
  FROM all_Sessions