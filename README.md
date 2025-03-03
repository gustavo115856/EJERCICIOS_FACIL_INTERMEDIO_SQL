Ejercicios de DataLemur en SQL

1.seccion 1-SOL TUTORIAL INTRO

SQL WHERE Practice Exercise 

Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause. Only display the user_id and stars columns. SELECT user_id, stars FROM reviews WHERE stars = 3;


SQL Select Practice Exercise

Your given a products table, which contains data about different Microsoft Azure cloud products.Output all the data, in all the columns. SELECT * FROM products


SQL WHERE Practice Exercise

Given the reviews table, write a query to retrieve all 3-star reviews using the SQL WHERE clause. Only display the user_id and stars columns.
SELECT user_id, stars FROM reviews WHERE stars = 3;


SQL WHERE AND Practice Exercise

SELECT * FROM reviews WHERE stars >= 4 AND  review_id < 6000AND  review_id > 2000AND user_id <> 142;


SQL BETWEEN Practice Exercise

SELECT manufacturer, drug, units_sold FROM pharmacy_sales WHERE (manufacturer = 'Biogen' OR manufacturer = 'AbbVie' OR manufacturer = 'Eli Lilly') AND units_sold BETWEEN 100000 AND 105000;


SQL IN Practice Exercise

SELECT  manufacturer, drug, units_sold FROM pharmacy_sales WHERE manufacturer IN ('Roche', 'Bayer', 'AstraZeneca') AND units_sold NOT BETWEEN 55000 AND 550000;


SQL LIKE % Practice Exercise

SELECT * FROM customers WHERE customer_name LIKE 'F%ck';


SQL LIKE _ Practice Exercise

SELECT * FROM customers WHERE customer_name LIKE '_ee%';


SQL Filtering Practice Exercise #1

SELECT  customer_id,  customer_name,  gender, age, zip_code, city,  state FROM customers
WHERE age BETWEEN 18 AND 22 AND state IN ('Victoria', 'Tasmania', 'Queensland') AND gender != 'n/a' AND (customer_name LIKE 'A%' OR customer_name LIKE 'B%');


2.seccion 2-NTERMEDIATE INTRO


SQL COUNT Practice Exercise:


SELECT COUNT(*) FROM pharmacy_sales;

SELECT COUNT(*), SUM(total_sales) FROM pharmacy_sales WHERE manufacturer = 'Pfizer'

SELECT AVG(open) FROM stock_prices WHERE ticker='GOOG';

SELECT MIN(open) FROM stock_prices WHERE ticker='MSFT';

SELECT MAX(open) FROM stock_prices WHERE ticker='NFLX';


Easy SQL GROUP BY Practice Exercise

SELECT ticker, MIN(open) FROM stock_prices GROUP BY ticker ORDER BY min DESC;


SQL GROUP BY Practice Exercise: Candidate Skills

SELECT skill, COUNT(candidate_id) FROM candidates GROUP BY skill ORDER BY count DESC;


SQL HAVING MIN Practice Exercise

SELECT ticker, MIN(open) FROM stock_prices GROUP BY ticker HAVING MIN(open) > 100


SQL HAVING Practice Exercise

SELECT candidate_id FROM candidates GROUP BY candidate_id HAVING COUNT(candidate_id) > 2;

SQL COUNT DISTINCT Practice Exercise

SELECT category, COUNT(DISTINCT product) FROM product_spend GROUP BY category;


Pharmacy Analytics (Part 1)

SELECT  drug, (total_sales - cogs) AS total_profit FROM  pharmacy_sales ORDER BY total_profit DESC LIMIT 3;
Cards Issued Difference
SELECT card_name, MAX(issued_amount) - MIN(issued_amount) AS difference FROM monthly_cards_issued
GROUP BY card_name ORDER BY difference DESC;


SQL Math Practice Exercise: Big-Mover Months

SELECT ticker, COUNT(ticker) FROM stock_prices WHERE (close - open)/open > 0.10 OR (close - open)/open < -0.10GROUP BY ticker ORDER BY count DESC;


SQL CEIL Practice Exercise

SELECT drug, CEIL(total_sales / units_sold) AS unit_cost FROM pharmacy_sales WHERE manufacturer = 'Merck' ORDER BY unit_cost;


Unfinished Parts

SELECT part, assembly_step FROM parts_assembly WHERE finish_date IS NULL;


SQL Tutorial Lesson: Superheroes' Likes

SELECT actor, character, platform, avg_likes,CASE WHEN avg_likes >= 15000 THEN 'Super Likes'WHEN avg_likes BETWEEN 5000 AND 14999 THEN 'Good Likes'
ELSE 'Low Likes'END AS likes_category FROM marvel_avengers ORDER BY avg_likes DESC;


Laptop vs. Mobile Viewership

SELECT COUNT(*) FILTER (WHERE device_type = 'laptop') AS laptop_views,COUNT(*) FILTER (WHERE device_type IN ('tablet', 'phone'))  AS mobile_views 
FROM viewership


Easy SQL JOIN Practice Exercise

SELECT *FROM trades INNER JOIN user ON trades.user_id = users.user_id;


Page With No Likes

SELECT  p.page_id FROM pages p LEFT JOIN page_likes pl ON p.page_id = pl.page_id WHERE pl.page_id IS NULL ORDER BY p.page_id ASC;


Average Post Hiatus (Part 1)

SELECT user_id, MAX(post_date::DATE) - MIN(post_date::DATE) AS days_between FROM posts
WHERE DATE_PART('year', post_date::DATE) = 2021 GROUP BY user_id
HAVING COUNT(post_id)>1;
