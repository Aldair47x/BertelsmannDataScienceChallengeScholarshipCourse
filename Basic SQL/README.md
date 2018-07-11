<h1>Introduction </h1>

<p>Before we dive into writing SQL queries, let's take a look at what makes SQL and the databases that utilize SQL so popular.

I think it is an important distinction to say that SQL is a language. Hence, the last word of SQL being language. SQL is used all over the place beyond the databases we will utilize in this class. With that being said, SQL is most popular for its interaction with databases. For this class, you can think of a database as a bunch of excel spreadsheets all sitting in one place. Not all databases are a bunch of excel spreadsheets sitting in one place, but it is a reasonable idea for this class.
</p>

<p>There are some major advantages to using traditional relational databases, which we interact with using SQL. The five most apparent are:

SQL is easy to understand.
Traditional databases allow us to access data directly.
Traditional databases allow us to audit and replicate our data.
SQL is a great tool for analyzing multiple tables at once.
SQL allows you to analyze more complex questions than dashboard tools like Google Analytics.
You will experience these advantages first hand, as we learn to write SQL to interact with data.

I realize you might be getting a little nervous or anxious to start writing code. This might even be the first time you have written in any sort of programming language. I assure you, we will work through examples to help assure you feel supported the whole time to take on this new challenge!
</p>

<h2>SQL vs. NoSQL</h2>

<p>
	You may have heard of NoSQL, which stands for not only SQL. Databases using NoSQL allow for you to write code that interacts with the data a bit differently than what we will do in this course. These NoSQL environments tend to be particularly popular for web based data, but less popular for data that lives in spreadsheets the way we have been analyzing data up to this point. One of the most popular NoSQL languages is called MongoDB. Udacity has a full course on MongoDB that you can take for free here, but these will not be a focus of this program.
	NoSQL is not a focus of analyzing data in this Nanodegree program, but you might see it referenced outside this course!
</p>

<h2>SQL Queries</h2>


<h3>LIMIT</h3>

```
SELECT occurred_at, account_id, channel
FROM web_events
LIMIT 15

```
<h3>ORDER BY</h3>

<li>
Write a query to return the 10 earliest orders in the orders table. Include the id, occurred_at, and total_amt_usd.
</li>

<li>
Write a query to return the top 5 orders in terms of largest total_amt_usd. Include the id, account_id, and total_amt_usd.
</li>

<li>
Write a query to return the bottom 20 orders in terms of least total. Include the id, account_id, and total.</li>
</li>

<li>
	Write a query that returns the top 5 rows from orders ordered according to newest to oldest, but with the largest total_amt_usd for each date listed first for each date. You will notice each of these dates shows up as unique because of the time element. When you learn about truncating dates in a later lesson, you will better be able to tackle this question on a day, month, or yearly basis. 
</li>

<li>
	Write a query that returns the top 10 rows from orders ordered according to oldest to newest, but with the smallest total_amt_usd for each date listed first for each date. You will notice each of these dates shows up as unique because of the time element. When you learn about truncating dates in a later lesson, you will better be able to tackle this question on a day, month, or yearly basis. 
</li>

```
SELECT id, occurred_at, total_amt_usd
FROM orders
ORDER BY occurred_at
LIMIT 10

SELECT id, account_id, total_amt_usd
FROM orders
ORDER BY total_amt_usd DESC 
LIMIT 5

SELECT id, account_id, total
FROM orders
ORDER BY total
LIMIT 20

SELECT *
FROM orders
ORDER BY occurred_at DESC, total_amt_usd DESC 
LIMIT 5

SELECT *
FROM orders
ORDER BY occurred_at, total_amt_usd
LIMIT 10

```

<h3>WHERE</h3>

<li>
	Pull the first 5 rows and all columns from the orders table that have a dollar amount of gloss_amt_usd greater than or equal to 1000.
</li>

<li>
	Pull the first 10 rows and all columns from the orders table that have a total_amt_usd less than 500.
</li>

<li>
	Filter the accounts table to include the company name, website, and the primary point of contact (primary_poc) for Exxon Mobil in the accounts table.
</li>

```
SELECT *
FROM orders
WHERE gloss_amt_usd >= 1000
LIMIT 5;

SELECT *
FROM orders
WHERE total_amt_usd < 500
LIMIT 10;

SELECT name, website, primary_poc
FROM accounts
WHERE name = 'Exxon Mobil';

```

<h3>Arithmetic Operations</h3>

<li>Create a column that divides the standard_amt_usd by the standard_qty to find the unit price for standard paper for each order. Limit the results to the first 10 orders, and include the id and account_id fields.
</li>

<li>
Write a query that finds the percentage of revenue that comes from poster paper for each order. You will need to use only the columns that end with _usd. (Try to do this without using the total column). Include the id and account_id fields. NOTE - you will be thrown an error with the correct solution to this question. This is for a division by zero. You will learn how to get a solution without an error to this query when you learn about CASE statements in a later section. For now, you might just add some very small value to your denominator as a work around. 
</li>

```
SELECT id, account_id, standard_amt_usd/standard_qty AS unit_price
FROM orders
LIMIT 10;


SELECT id, account_id, 
       poster_amt_usd/(standard_amt_usd + gloss_amt_usd + poster_amt_usd) AS post_per
FROM orders;

```

<h2>Introduction to Logical Operators </h2>
<p>
	In the next concepts, you will be learning about Logical Operators. Logical Operators include:
</p>

<h3>LIKE </h3>
This allows you to perform operations similar to using WHERE and =, but for cases when you might not know exactly what you are looking for.

<h3>IN</h3>
This allows you to perform operations similar to using WHERE and =, but for more than one condition.

<h3>NOT</h3>
This is used with IN and LIKE to select all of the rows NOT LIKE or NOT IN a certain condition.

<h3>AND & BETWEEN</h3>
These allow you to combine operations where all combined conditions must be true.

<h3>OR</h3>
This allow you to combine operations where at least one of the combined conditions must be true.


<h3>LIKE operator</h3>

<li>All the companies whose names start with 'C'.</li> 

<li>All companies whose names contain the string 'one' somewhere in the name.</li>

<li>All companies whose names end with 's'.</li>

```
SELECT name
FROM accounts
WHERE name LIKE 'C%';

SELECT name
FROM accounts
WHERE name LIKE '%one%';

SELECT name
FROM accounts
WHERE name LIKE '%s';

```

<h3>IN operator</h3>
<li>
	Use the accounts table to find the account name, primary_poc, and sales_rep_id for Walmart, Target, and Nordstrom.
</li>

<li>
	Use the web_events table to find all information regarding individuals who were contacted via the channel of organic or adwords.
</li>

```

SELECT name, primary_poc, sales_rep_id
FROM accounts
WHERE name IN ('Walmart','Target','Nordstrom');

SELECT *
FROM web_events
WHERE channel IN ('organic','adwords');

```
<h3>NOT operator</h3>

<li>
	Use the accounts table to find the account name, primary poc, and sales rep id for all stores except Walmart, Target, and Nordstrom.
</li>

<li>
	
Use the web_events table to find all information regarding individuals who were contacted via any method except using organic or adwords methods.
</li>

<li>
	All the companies whose names do not start with 'C'.
</li>

<li>
	All companies whose names do not contain the string 'one' somewhere in the name.

</li>

<li>
	All companies whose names do not end with 's'.
</li>
```
SELECT name, primary_poc, sales_rep_id
FROM accounts
WHERE name NOT IN ('Walmart', 'Target', 'Nordstrom');

SELECT *
FROM web_events
WHERE channel NOT IN ('organic', 'adwords');

SELECT name
FROM accounts
WHERE name NOT LIKE 'C%';

SELECT name
FROM accounts
WHERE name NOT LIKE '%one%';

SELECT name
FROM accounts
WHERE name NOT LIKE '%s';

```
<h3>AND operator</h3>

```
WHERE column >= 6 AND column <= 10

```
<h3>BETWEEN Operator</h3>

```
WHERE column BETWEEN 6 AND 10

```

<h3>OR operator</h3>

<li>
	Find list of orders ids where either gloss_qty or poster_qty is greater than 4000. Only include the id field in the resulting table.
</li>

<li>
	Write a query that returns a list of orders where the standard_qty is zero and either the gloss_qty or poster_qty is over 1000.
</li>

```
SELECT id
FROM orders
WHERE gloss_qty > 4000 OR poster_qty > 4000;

SELECT *
FROM orders
WHERE standard_qty = 0 AND (gloss_qty > 1000 OR poster_qty > 1000);

```

<tbody>
<tr>
<td>SELECT</td>
<td>SELECT <strong>Col1</strong>, <strong>Col2</strong>, ...</td>
<td>Provide the columns you want</td>
</tr>
<tr>
<td>FROM</td>
<td>FROM <strong>Table</strong></td>
<td>Provide the table where the columns exist</td>
</tr>
<tr>
<td>LIMIT</td>
<td>LIMIT <strong>10 </strong></td>
<td>Limits based number of rows returned</td>
</tr>
<tr>
<td>ORDER BY</td>
<td>ORDER BY <strong>Col</strong></td>
<td>Orders table based on the column.  Used with <strong>DESC</strong>.</td>
</tr>
<tr>
<td>WHERE</td>
<td>WHERE <strong>Col &gt; 5</strong></td>
<td>A conditional statement to filter your results </td>
</tr>
<tr>
<td>LIKE</td>
<td>WHERE <strong>Col LIKE '%me%'</strong></td>
<td>Only pulls rows where column has 'me' within the text </td>
</tr>
<tr>
<td>IN</td>
<td>WHERE <strong>Col IN ('Y', 'N')</strong></td>
<td>A filter for only rows with column of 'Y' or 'N'</td>
</tr>
<tr>
<td>NOT</td>
<td>WHERE <strong>Col NOT IN ('Y', 'N')</strong></td>
<td><strong>NOT</strong> is frequently used with <strong>LIKE</strong> and <strong>IN</strong></td>
</tr>
<tr>
<td>AND</td>
<td>WHERE <strong>Col1 &gt; 5 AND Col2 &lt; 3 </strong></td>
<td>Filter rows where two or more conditions must be true </td>
</tr>
<tr>
<td>OR</td>
<td>WHERE <strong>Col1 &gt; 5 OR Col2 &lt; 3</strong></td>
<td>Filter rows where at least one condition must be true</td>
</tr>
<tr>
<td>BETWEEN</td>
<td>WHERE <strong>Col BETWEEN 3 AND 5</strong></td>
<td>Often easier syntax than using an <strong>AND</strong></td>
</tr>
</tbody>