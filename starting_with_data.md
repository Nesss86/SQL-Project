Question 1: Which channel group generated the most total revenue?

SQL Queries:
##SELECT channel_grouping,CAST(total_transaction_revenue AS money) AS total_revenue
FROM all_sessions
WHERE channel_grouping IS NOT NULL
AND total_transaction_revenue IS NOT NULL
ORDER BY channel_grouping DESC, total_transaction_revenue DESC 
  


Answer: Referral's generated the most total revenue.



Question 2: Were there repeat visitors and if so, what were they viewing and was it more than once? 

SQL Queries:
##SELECT full_visitor_id, page_title, COUNT(*)
FROM all_sessions
GROUP BY full_visitor_id, page_title
HAVING COUNT(*) > 1
ORDER BY COUNT(*) DESC



Answer: There were 389 repeat visitors and in looking at the amount of views for a specific page title, it was noticed that there was one paricular visitor that viewed the same page the most. This was full_visitor_id 769560476351515188 which viewed Youtube 8 times. 


Question 3: What was the most and least popular day for site visits?

##SQL Queries:
SELECT EXTRACT(DOW FROM date) AS day_of_week, COUNT(*) AS visit_count
FROM all_sessions
GROUP BY day_of_week
ORDER BY visit_count DESC



Answer: The most popular day for visits was Wednesday with a total of 2,479 visits while the least popular day was Saturday with a total of 1572 visits.




