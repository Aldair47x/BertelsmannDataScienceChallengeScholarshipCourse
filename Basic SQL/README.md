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
