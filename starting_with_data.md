Question 1: 

SQL Queries:
##SELECT channel_grouping,CAST(total_transaction_revenue AS money) AS total_revenue
FROM all_sessions
WHERE channel_grouping IS NOT NULL
AND total_transaction_revenue IS NOT NULL
ORDER BY channel_grouping DESC, total_transaction_revenue DESC 
  


Answer: Referral's generated the most total revenue



Question 2: 

SQL Queries:



Answer: 


Question 3: 

SQL Queries:









