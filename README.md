# BIG DATA MANAGEMENT WITH MYSQL

### Entity Relationship Diagrams

### MANDATORY QUERY COMMANDS SYNTAX
SELECT

FROM

### OPTIONAL QUERY COMMANDS SYNTAX
USE

WHERE

GROUP

HAVING

ORDER BY


<strong> SELECT the data I want FROM these database and tables WHERE these criteria are met GROUP (BY) this field HAVING this property ORDER (BY) this field or list; <strong>

<h3><a href="https://dev.mysql.com/doc/refman/5.7/en/keywords.html">ALL SQL QUERY COMMANDS</a></h3>


## DATABASE INTERFACE: Using Jupyter Notebooks
Jupyter allows a way to write in text an explain for every query that you try and understand the logic behind all each query.

### QUERING

First thing first:
### Library Loading
`load_ext sql`

### Connect to Database + Instruct to use specific database
`%sql mysql://username:userpwd@localhost/databasename`
`%sql USE databasename`

To get to know your data, you can use Entity Relationship Diagram or Relational Schema, or:
### Inspect Table
`%sql SHOW tables`

### Inspect Columns [+ shorthand command]
`%sql SHOW columns FROM tablename`

<strong>SHORTHAND:</strong> `%sql DESCRIBE columnname`

### Using WHERE to interact with a subset of the data set

E.G. Display the first 100 rows of dogs whose dna has been tested:

```
%%sql
SELECT dog_guid, dna_tested
FROM dogs
WHERE dna_tested=1 LIMIT 100
```

### WHERE keyword and STRINGS
Strings need to be surrounded by quotation marks in SQL. MySQL accepts both double and single quotation marks, but some database systems only accept single quotation marks. Whenever a string contains an SQL keyword, the string must be enclosed in backticks instead of quotation marks.

'the marks that surrounds this phrase are single quotation marks'
"the marks that surrounds this phrase are double quotation marks"
`the marks that surround this phrase are backticks`

Strings enclosed in quotation or backticks can be used with many of the same operators as numerical data. For example, imagine that you only wanted to look at data from dogs of the breed "Golden Retrievers." You could query (note that double quotation marks could have been used in this example is well):

SELECT dog_guid, breed
FROM dogs
WHERE breed='golden retriever';
The IN operator allows you to specify multiple values in a WHERE clause. Each of these values must be separated by a comma from the other values, and the entire list of values should be enclosed in parentheses. If you wanted to look at all the data from Golden Retrievers and Poodles, you could certainly use the OR operator, but the IN operator would be even more efficient (note that single quotation marks could have been used in this example, too):

SELECT dog_guid, breed
FROM dogs
WHERE breed IN ("golden retriever","poodle");
The LIKE operator allows you to specify a pattern that the textual data you query has to match. For example, if you wanted to look at all the data from breeds whose names started with "s", you could query:

SELECT dog_guid, breed
FROM dogs
WHERE breed LIKE ("s%");
In this syntax, the percent sign indicates a wild card. Wild cards represent unlimited numbers of missing letters. This is how the placement of the percent sign would affect the results of the query:

WHERE breed LIKE ("s%") = the breed must start with "s", but can have any number of letters after the "s"
WHERE breed LIKE ("%s") = the breed must end with "s", but can have any number of letters before the "s"
WHERE breed LIKE ("%s%") = the breed must contain an "s" somewhere in its name, but can have any number of letters before or after the "s"


