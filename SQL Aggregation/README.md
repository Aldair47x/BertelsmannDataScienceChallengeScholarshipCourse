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

<h3></h3>

```

```

<h3></h3>

```

```