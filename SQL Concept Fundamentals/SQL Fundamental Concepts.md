Database: Medium to store data.
Relational Database: Define relationships between tables of data inside the database.
Advantages: compared to spreadsheet, 1. Can store more data. 2. More secure 3. Many users can write queries to gather insights from data at the same time.

SQL: Structured Query Language - Programming language for creating, querying and updating relational databases.

Tables: Database is organized into tables, which hold related data about a particular subject. Rows: records, Columns: fields.
*Fields are limited to those set when the database was created, but the number of rows is unlimited.

Table parts: 
- Records: a row that holds data on an individual observation
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/Records.png)
- Fields: Holds one piece of information about all records.
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/fields.png)
- Keys: Unique Identifiers - unique value which identifies a record -- often a number.
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/Keys.png)

SQL Data Types:
- Number, text, date

Use of data types: 
1. Different types data stored differently and take up different amounts of storage space.
2. Some operations only apply to certain data types.
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/data%20types%201.png)

Strings: a sequence of characters such as letters or punctuation
  - Some string data types can only hold short strings, such as a string up to 250 characters.
  - VARCHAR: Flexible and popular string data type in SQL.

Integers: store whole numbers
  - INT: flexible and popular data type.

Floats: Fractional part ex:) 9.86, 0, 2.05
  - NUMERIC is a flexible and popular float data type

Filtering text
  - LIKE: Used to search for a pattern in a field.
    - % match zero, one, or many characters, _ match a single character
  - NOT LIKE

Schemas(Blueprints of a database): Shows a database's design, such as what tables are.
  - Reader know what data type each field can hold.

Database Storage: Stored on the hard disk of a server. 
  - Servers are centralized computers that perform services via requests made over a network.
  - They can be a computer or any centralized system.


-- Drawing insights from SQL
What is SQL useful for?
Answers questions such as 
  - Which products ahd the highest sales last week?
  - Which products get the worst review scores from customers?
  - How did website traffic change when a feature was introduced?

Keywords: reserved words for operations -- Common keywords: SELECT, FROM
Ex: -- SELECT name FROM patrons;
    -- SELECT card_num, name FROM patrons;

Aliasing: rename columns
Ex: -- SELECT name AS first_name, year_hired FROM employees;

Distinct Records:
Ex: -- SELECT DISTINCT year_hired FROM employees;

Multiples:
 : -- SELECT DISTINCT dept_id, year_hired FROM employees;

Views: Virtual table that is the result of a saved SQL SELECT statement
  - When accessed, views automatically update in response to updates in the underlying data

Ex: CREATE VIEW employee_hire_years AS SELECT id, name, year_hired FROM employees;
   Then, you can use to create, SELECT id, name FROM employee_hire_years

SQL flavors:
Two popular:
PostgreSQL
 -- Free and open source Relaiton Database 
 -- Refers to both the postgre sql databasee system
SQL server
 -- By Microsoft
 -- T-SQL is Microsoft's SQL

COUNT(): Counts the number of records with a value in a field
Ex: SELECT COUNT(birthdate) AS count_birthdates FROM people;
multiple fields:
SELECT COUNT(name) AS count_names, COUNT(birthdate) AS count_birthdates FROM people;

- COUNT(field_name) counts values in a field
- COUNT(*) counts records in a table
- * represents all fields

SELECT COUNT(*) AS total_records FROM people;
DISTINCT - removes duplicates to return only unique values
SELECT COUNT (DISTINCT birthdate) AS count_brithdates FROM people;

Order of execution
1. FROM people 2. SELECT name 3. LIMIT 10;

**Style guides --  For SQL Style guide, follow sqlstyle.guide/
Ex: 
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/Style%20Guide.png)


Non-standard Fields: Semicolumns
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/Non%20Standard%20Fields.png)

Filtering Numbers
WHERE - 
with comparison operators
Ex: 
SELECT title
FROM films
WHERE release_year > 1960; or <, <=, =, <>(not equal to)

Order of execution -- FROM, WHERE, SELECT, LIMIT

Multiple Criteria: Or, and, between
Or operator - Satisfy one condition
Ex: 
SELECT title FROM films WHERE release_year = 1994 OR release year = 2000;

Ex:
SELECT title, release_year
FROM films
WHERE (release_year BETWEEN 1994 AND 2000)
AND (language = 'English' OR language = 'Spanish')
AND gross > 2000000;

AND operator - satisfy all criteria
Ex:
SELECT title FROM films WHERE release_year = 1994 AND release year = 2000;
BETWEEN, AND

Ex:
SELECT title FROM films WHERE release_year BETWEEN 1994 AND 2000;

Filtering text
- Filter a pattern rather than specific text - LIKE, NOT LIKE, IN

LIKE
% match zero, one or many characters / _ match a single character
Ex: SELECT name FROM people WHERE name LIKE 'Ade%';


Wildcard position 
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/Wildcard%20Position.png)


NOT LIKE
SELECT name FROM people


WHERE, OR
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/WHERE%20OR.png)


WHERE, IN
![](https://github.com/Jeon-DataLab/SQL-Learning-Records/blob/main/SQL%20Concept%20Fundamentals/Source_Photos/WHERE%20IN.png)


Missing Values
COUNT(field_name) includes only non-missing values
COUNT(*) includes missing values
** Careful on using * as the data may contain many null values.

IS NULL: Checks to see if there is a null value.
SELECT name
FROM people
WHERE birthdate IS NulL;

IS NOT NULL: Checks to see no null values.
SELECT COUNT (*) AS no_birthdates
FROM people
WHERE birthdate IS NOT NULL;

This is same as 
SELECT COUNT(___) AS count_certification FROM files;

Summarizing Data --
Aggregate Functions: avg, sum, min, max, count

Select ___(budget)
FROM films;

Non numerical data
Numerical Fields only: Avg, sum
Various Data Types: Count, min, max

Important to Alias
(Non-numerical photo)

WHERE with aggregate functions
Ex:
SELECT AVG(budget) AS avg_budget
FROM films
Where release_year >= 2010;

Round(): Round(number_to_round, decimal_places)
SELECT ROUND(AVG(budget),2) AS avg_budget
FROM films
WHERE release_year >= 2010;

**You can round to whole number using 0, and also to negative -5 for instance, to get to the left value 5 position.

