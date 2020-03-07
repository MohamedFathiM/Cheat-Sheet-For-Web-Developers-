# ***DML*** – Data Manipulation Language :refers to the INSERT, UPDATE and DELETE statements , DML allows to add / modify / delete data itself.


# Data Types :

## String :

> CHAR(size) , VARCHAR(size) , TINYTEXT(size) , TEXT(size) , MEDIUMTEXT(size) , LONGTEXT(size)

## Number :

> TINYINT , SMALLINT , MEDIUMINT , INT , BIGINT  , FLOAT(M,D) , DOUBLE(M,D) , DECIMAL(m,d)

## Date :

> DATE , DATETIME , TIME , YEAR[(2|4)]

---------------------------------------------------------------------------------------------------

# Database Constraints

 ▰ Not Null. ▰ Primary Key. ▰ Unique Key. ▰ Referential Integrity ( FK ). ▰ AUTO_INCREMENT

 ---------------------------------------------------------------------------------------------------


# General Query :

`SHOW DATABASES ;` // To display All databases

`USE databasename;` // to select database to work on it

`SHOW TABLES;` // Show tables of selected database

`Describe tablename ; ` // show table column information

`Show create table tablename ; ` // show table creation Query

---------------------------------------------------------------------------------------------------

# Create and drop database :

`CREATE DATABASE mydatabasename ;`

`CREATE DATABASE IF NOT EXISTS mydatabasename ;`

`DROP DATABASE mydatabasename ;` // For Delete Database

---------------------------------------------------------------------------------------------------

# Create new user :

` CREATE USER ‘username'@‘server' IDENTIFIED BY ‘password'; `

---------------------------------------------------------------------------------------------------

# Grant Permission to user :

` GRANT PRIVILEGES ON database.table TO 'username'@'localhost' IDENTIFIED BY 'password'; `

> ▰ PRIVILEGES => create ,drop ,select ,… or ALL PRIVILEGES.

**EX:**

`GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password';`

---------------------------------------------------------------------------------------------------

# Revoking Privileges From Users :

`REVOKE privileges ON object FROM user;`

> ▰ PRIVILEGES => create ,drop ,select ,…or ALL , Grant .

---------------------------------------------------------------------------------------------------

# Create Command :

`Create table "table_name” (“column name” data type, “column name” data type, ...) `

**EX:**
```
CREATE TABLE customer (ID int (3) Not Null, First_Name char(50), Last_Name char(50), City char(25), Birth_Date date, Primary key (ID) FOREIGN KEY (PersonID) REFERENCES Persons(PersonID));
```
---------------------------------------------------------------------------------------------------

# Drop Command :

` Drop table “table name”; ` // to delete table

---------------------------------------------------------------------------------------------------

# Alter Command :

`ALTER TABLE table_name ADD column_name datatype ` // to add column

`ALTER TABLE table_name DROP COLUMN column_name ` // to delete column

---------------------------------------------------------------------------------------------------

# Insert Command :

` INSERT INTO "table_name” ("column1","column2", ...) VALUES ("value1", "value2", ...)`

**EX :**

`INSERT INTO Person VALUES (‘Saleh’, ‘Ahmed', ‘Moharam bak', ‘Alex.')`

---------------------------------------------------------------------------------------------------

# Update Command :

`UPDATE "table_name" SET "column_1" = {new value} [WHERE {condition}] `

**EX :**

`UPDATE Person SET City= ‘Assiut’` // All records will be updated

`UPDATE Person SET City= ‘Assiut’ Where FirstName = ‘Ahmed’` // Only records with first name 'Ahmed' will be updated

---------------------------------------------------------------------------------------------------

# Delete Command :

` DELETE FROM "table_name" [WHERE {condition} ] `

---------------------------------------------------------------------------------------------------

# References :

Intake 39 - DB Mohamed Elshafei
