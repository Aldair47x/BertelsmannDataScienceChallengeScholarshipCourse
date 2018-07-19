<h1>Aggregate Functions</h1>

<li>MIN: returns the smallest value in a given column</li>
<li>MAX: returns the largest value in a given column</li>
<li>SUM: returns the sum of the numeric values in a given column</li>
<li>AVG: returns the average value of a given column</li>
<li>COUNT: returns the total number of values in a given column</li>
<li>COUNT(*): returns the number of rows in a table</li>

<p>Aggregate functions are used to compute against a "returned column of numeric data" from your SELECT statement. They basically summarize the results of a particular column of selected data. We are covering these here since they are required by the next topic, "GROUP BY". Although they are required for the "GROUP BY" clause, these functions can be used without the "GROUP BY" clause.
</p>

<h3>Aggregation Questions</h3>

<p>Use the SQL environment below to find the solution for each of the following questions. If you get stuck or want to check your answers, you can find the answers at the top of the next concept.</p>

<li>Find the total amount of poster_qty paper ordered in the orders table.</li>
<li>Find the total amount of standard_qty paper ordered in the orders table.</li>
<li>Find the total dollar amount of sales using the total_amt_usd in the orders table.</li>
<li>Find the total amount spent on standard_amt_usd and gloss_amt_usd paper for each order in the orders table. This should give a dollar amount for each order in the table.</li>
<li>Find the standard_amt_usd per unit of standard_qty paper. Your solution should use both an aggregation and a mathematical operator.</li>

```
SELECT SUM(poster_qty) AS total_poster_sales
FROM orders;

SELECT SUM(standard_qty) AS total_standard_sales
FROM orders;

SELECT SUM(total_amt_usd) AS total_dollar_sales
FROM orders;

SELECT standard_amt_usd + gloss_amt_usd AS total_standard_gloss
FROM orders;

SELECT SUM(standard_amt_usd)/SUM(standard_qty) AS standard_price_per_unit
FROM orders;

```

<h3>MIN, MAX, & AVERAGE</h3>

<li>When was the earliest order ever placed?</li>
<li>Try performing the same query as in question 1 without using an aggregation function.</li>
<li>When did the most recent (latest) web_event occur?</li>
<li>Try to perform the result of the previous query without using an aggregation function.</li>
<li>Find the mean (AVERAGE) amount spent per order on each paper type, as well as the mean amount of each paper type purchased per order. Your final answer should have 6 values - one for each paper type for the average number of sales, as well as the average amount.</li>
<li>Via the video, you might be interested in how to calculate the MEDIAN. Though this is more advanced than what we have covered so far try finding - what is the MEDIAN total_usd spent on all orders? Note, this is more advanced than the topics we have covered thus far to build a general solution, but we can hard code a solution in the following way.</li>



```
SELECT MIN(occurred_at) 
FROM orders;

SELECT occurred_at 
FROM orders 
ORDER BY occurred_at
LIMIT 1;

SELECT MAX(occurred_at)
FROM web_events;

SELECT occurred_at
FROM web_events
ORDER BY occurred_at DESC
LIMIT 1;

SELECT AVG(standard_qty) mean_standard, AVG(gloss_qty) mean_gloss, 
           AVG(poster_qty) mean_poster, AVG(standard_amt_usd) mean_standard_usd, 
           AVG(gloss_amt_usd) mean_gloss_usd, AVG(poster_amt_usd) mean_poster_usd
FROM orders;


SELECT *
FROM (SELECT total_amt_usd
      FROM orders
      ORDER BY total_amt_usd
      LIMIT 3457) AS Table1
ORDER BY total_amt_usd DESC
LIMIT 2;

```

<h3>Questions: GROUP BY</h3>

<li>Which account (by name) placed the earliest order? Your solution should have the account name and the date of the order.
</li>

```
SELECT a.name, o.occurred_at
FROM accounts a
JOIN orders o
ON a.id = o.account_id
ORDER BY occurred_at
LIMIT 1;

```

<li>Find the total sales in usd for each account. You should include two columns - the total sales for each company's orders in usd and the company name.</li>

```
SELECT a.name, SUM(total_amt_usd) total_sales
FROM orders o
JOIN accounts a
ON a.id = o.account_id
GROUP BY a.name;

```

<li>Via what channel did the most recent (latest) web_event occur, which account was associated with this web_event? Your query should return only three values - the date, channel, and account name.</li>

```
SELECT w.occurred_at, w.channel, a.name
FROM web_events w
JOIN accounts a
ON w.account_id = a.id 
ORDER BY w.occurred_at DESC
LIMIT 1;

```

<li>Find the total number of times each type of channel from the web_events was used. Your final table should have two columns - the channel and the number of times the channel was used.</li>

```
SELECT w.channel, COUNT(*)
FROM web_events w
GROUP BY w.channel

```

<li>Who was the primary contact associated with the earliest web_event?</li>

```
SELECT a.primary_poc
FROM web_events w
JOIN accounts a
ON a.id = w.account_id
ORDER BY w.occurred_at
LIMIT 1;

```

<li>What was the smallest order placed by each account in terms of total usd. Provide only two columns - the account name and the total usd. Order from smallest dollar amounts to largest.</li>

```
SELECT a.name, MIN(total_amt_usd) smallest_order
FROM accounts a
JOIN orders o
ON a.id = o.account_id
GROUP BY a.name
ORDER BY smallest_order;

```
<p>Sort of strange we have a bunch of orders with no dollars. We might want to look into those. </p>

<li>Find the number of sales reps in each region. Your final table should have two columns - the region and the number of sales_reps. Order from fewest reps to most reps.</li>

```
SELECT r.name, COUNT(*) num_reps
FROM region r
JOIN sales_reps s
ON r.id = s.region_id
GROUP BY r.name
ORDER BY num_reps;

```

<li></li>

```

```



<h3></h3>

```

```

<h3></h3>

```

```

<h3></h3>

```

```

<h3></h3>

```

```

<h3></h3>

```

```