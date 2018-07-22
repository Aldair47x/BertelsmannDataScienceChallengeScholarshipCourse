<h1>Data Cleaning</h1>

<li>LEFT</li>
<li>RIGHT</li>
<li>LENGTH</li>

<h2>LEFT</h2>
pulls a specified number of characters for each row in a specified column starting at the beginning (or from the left). As you saw here, you can pull the first three digits of a phone number using LEFT(phone_number, 3).

<h2>RIGHT</h2>
pulls a specified number of characters for each row in a specified column starting at the end (or from the right). As you saw here, you can pull the last eight digits of a phone number using RIGHT(phone_number, 8).

<h2>LENGTH </h2>
provides the number of characters for each row of a specified column. Here, you saw that we could use this to get the length of each phone number as LENGTH(phone_number).



<h3>LEFT & RIGHT Quizzes</h3>

<li>In the accounts table, there is a column holding the website for each company. The last three digits specify what type of web address they are using. A list of extensions (and pricing) is provided here. Pull these extensions and provide how many of each website type exist in the accounts table.
</li>

```
SELECT RIGHT(website, 3) AS domain, COUNT(*) num_companies
FROM accounts
GROUP BY 1
ORDER BY 2 DESC;

```

<li>There is much debate about how much the name (or even the first letter of a company name) matters. Use the accounts table to pull the first letter of each company name to see the distribution of company names that begin with each letter (or number). </li>

```
SELECT LEFT(UPPER(name), 1) AS first_letter, COUNT(*) num_companies
FROM accounts
GROUP BY 1
ORDER BY 2 DESC;

```

<li>POSITION</li>
<li>STRPOS</li>
<li>LOWER</li>
<li>UPPER</li>

<h2>POSITION </h2>
takes a character and a column, and provides the index where that character is for each row. The index of the first position is 1 in SQL. If you come from another programming language, many begin indexing at 0. Here, you saw that you can pull the index of a comma as POSITION(',' IN city_state).

<h2>STRPOS</h2>
provides the same result as POSITION, but the syntax for achieving those results is a bit different as shown here: STRPOS(city_state, ',').

Note, both POSITION and STRPOS are case sensitive, so looking for A is different than looking for a. 


<h2>LOWER or UPPER </h2>

Therefore, if you want to pull an index regardless of the case of a letter, you might want to use LOWER or UPPER to make all of the characters lower or uppercase.


<li>CONCAT</li>
<li>Piping ||</li>

Each of these will allow you to combine columns together across rows. In this video, you saw how first and last names stored in separate columns could be combined together to create a full name: CONCAT(first_name, ' ', last_name) or with piping as first_name || ' ' || last_name.

<li>TO_DATE</li>
<li>CAST</li>
<li>Casting with ::</li>

DATE_PART('month', TO_DATE(month, 'month')) here changed a month name into the number associated with that particular month.


Then you can change a string to a date using CAST. CAST is actually useful to change lots of column types. Commonly you might be doing as you saw here, where you change a string to a date using CAST(date_column AS DATE). However, you might want to make other changes to your columns in terms of their data types. You can see other examples here.

In this example, you also saw that instead of CAST(date_column AS DATE), you can use date_column::DATE.

<h2>Expert Tip</h2>
Most of the functions presented in this lesson are specific to strings. They won’t work with dates, integers or floating-point numbers. However, using any of these functions will automatically change the data to the appropriate type.

LEFT, RIGHT, and TRIM are all used to select only certain elements of strings, but using them to select elements of a number or date will treat them as strings for the purpose of the function. Though we didn't cover TRIM in this lesson explicitly, it can be used to remove characters from the beginning and end of a string. This can remove unwanted spaces at the beginning or end of a row that often happen with data being moved from Excel or other storage systems.

There are a number of variations of these functions, as well as several other string functions not covered here. Different databases use subtle variations on these functions, so be sure to look up the appropriate database’s syntax if you’re connected to a private database.The Postgres literature contains a lot of the related functions.