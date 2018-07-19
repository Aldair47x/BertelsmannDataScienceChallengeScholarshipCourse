<h3>Your First Subquery Questions</h3>

<li>First, we needed to group by the day and channel. Then ordering by the number of events (the third column) gave us a quick way to answer the first question.</li>

```
SELECT DATE_TRUNC('day',occurred_at) AS day,
   channel, COUNT(*) as events
FROM web_events
GROUP BY 1,2
ORDER BY 3 DESC;

```

<li>Here you can see that to get the entire table in question 1 back, we included an * in our SELECT statement. You will need to be sure to alias your table.</li>

```
SELECT *
FROM (SELECT DATE_TRUNC('day',occurred_at) AS day,
           channel, COUNT(*) as events
     FROM web_events 
     GROUP BY 1,2
     ORDER BY 3 DESC) sub;

```

<li>Finally, here we are able to get a table that shows the average number of events a day for each channel</li>

```
SELECT channel, AVG(events) AS average_events
FROM (SELECT DATE_TRUNC('day',occurred_at) AS day,
             channel, COUNT(*) as events
      FROM web_events 
      GROUP BY 1,2) sub
GROUP BY channel
ORDER BY 2 DESC;

```

<h2>Your First WITH (CTE)</h2>

<li>QUESTION: You need to find the average number of events for each channel per day.</li>

```
SELECT channel, AVG(events) AS average_events
FROM (SELECT DATE_TRUNC('day',occurred_at) AS day,
             channel, COUNT(*) as events
      FROM web_events 
      GROUP BY 1,2) sub
GROUP BY channel
ORDER BY 2 DESC;
Let's try this again using a WITH statement.

```

Notice, you can pull the inner query:

```

SELECT DATE_TRUNC('day',occurred_at) AS day, 
       channel, COUNT(*) as events
FROM web_events 
GROUP BY 1,2

This is the part we put in the WITH statement. Notice, we are aliasing the table as events below:

WITH events AS (
          SELECT DATE_TRUNC('day',occurred_at) AS day, 
                        channel, COUNT(*) as events
          FROM web_events 
          GROUP BY 1,2)
Now, we can use this newly created events table as if it is any other table in our database:

WITH events AS (
          SELECT DATE_TRUNC('day',occurred_at) AS day, 
                        channel, COUNT(*) as events
          FROM web_events 
          GROUP BY 1,2)

SELECT channel, AVG(events) AS average_events
FROM events
GROUP BY channel
ORDER BY 2 DESC;

```

For the above example, we don't need anymore than the one additional table, but imagine we needed to create a second table to pull from. We can create an additional table to pull from in the following way:

```

WITH table1 AS (
          SELECT *
          FROM web_events),

     table2 AS (
          SELECT *
          FROM accounts)


SELECT *
FROM table1
JOIN table2
ON table1.account_id = table2.id;

```