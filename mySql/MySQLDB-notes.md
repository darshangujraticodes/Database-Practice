# MySQL Database Course Notes

### What is Database ?

1. It is an organized collection of structured information, typically stored electronically in computer system. It allows for data to be easily access, manage, modified, updated and deleted.

2. It serves as the backbone for all application to store all types of data

### Key Features of Database

1. Persistent Storage
2. Structured & Organized
3. Easily Retrievable
4. Concurrent Access
5. Security and Integrity

### What is DBMS ?

It is software that manage database for performing CRUD operation like, inserting, updated and deleting data. It act as interface between database and user application

Types of DBMS <br>

1. Relational DBMS : MySQL, PostgreSQL
2. Non Relational DBMS : MongoDB, Cassandra, DynamoDB
3. In Memory DBMS : Redis, Memcached

### Concept of Relational Model

1. Tables (relations)
2. Columns (Attribute)
3. Row (Records)
4. Keys (Primary and Foreign Key)
5. Relationships between them : 1:1, 1:many, many:many

### Lets Learn MySQL(Microsoft Structured Query Language)

It is of 3 Category : <br>

1.  DDL (data definition language) : CREATE, ALTER, DROP, TRUNCATE, RENAME
2.  DML (data manipulation language) : SELECT, INSERT, UPDATE, DELETE
3.  DCL (dtaa control language) : GRANT, REVOKE
4.  TCL (Transactional Control Language) : COMMIT, ROLLBACK, SAVEPOINT, SET TRANSACTION

### Select Query

> [!NOTE]
> Semicolon(;) is must to end command and note as syntax format sql keywords in CAPITAL (upper case) and other normal words in small case | example Below

1. Select Database syntax : USE database_name; `USE nextapp;`
2. Display all tables in Database : `SHOW tables;`

### Database Schema and terminilogy

Database schema : It is logical blueprint or structure that define how data is oraganized within database

1. Tables in database
2. Relationship between those tables
3. attributes within each table
4. contraints and rules that govern the data eg. not null, default value ,
5. data type of each fields

Types of schema

1. Database schema : complete structure of entire database
2. Table schema : structure of specific table including column, data types, and constraints
3. Subschema : A portion of db visible to specific user or application

Data Types in MySQL

1. Numeric -> integer, floating points ( decimal value with rounding value) and fxed points(decimal value with precise decimal digits) (decimal)

   - tiny integer
   - smal integer
   - medium integer
   - big integer
   - floating
   - double
   - decimal

2. String ->

   - char
   - varchar
   - text
   - medium text
   - long text
   - enum('male','female', 'transgender') -> select single value from multiple defined options
   - set('monday', 'tuesday', 'wednesday', 'thursday', 'friday') -> select multiple value from multiple defined options

3. Date -> Date and time

   - Date
   - datetime
   - time
   - year
   - timestamp

### Database Query

1. Database Operation :

   - `create database school_db;` -> it help to create database
   - `show databases;` -> it help to display all database created in MySQL
   - `select database();` -> it help to show current database in which we are working
   - `use school_db;` -> it helps to select database on which we have to start working
   - `drop database school_db;` -> it help to delete database

2. Table Operation :
   - `create `
