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

<h3></h3>

```

```

<h3></h3>

```

```

<h3></h3>

```

```