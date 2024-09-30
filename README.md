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


