# BookStore 📚

## Overview 📙

The "Bookstore 📚" repository is a project developed for a database management system course ⚙️. The purpose of the project is to design and implement a database management system for an online book shop 🛍️

<br>

## Table of Contents 📄
1. [Introduction](#intro)
2. [ER-Diagram](#erd)
3. [Normalization](#normalize)
4. [PL/SQL](#coding)

<br>
<a id="intro"></a>

## Introduction 📝

The main goal of this project is to develop a software for the effective management of an online bookstore's database 🪧. The software is designed to be used by online shoppers 🛍️. Customers can order books using the online store 📦, and employees can easily update the website with new books and features✨

#### Features:

1. The software includes a grouping procedure to organize information efficiently 👾

2. It has a function that counts the total number of records 🤖

3. A procedure is available to determine the number of rows affected 🔖

4. Our software has user-defined exceptions, which prevent the entry of book names that are less than 5 characters 👻
   
5. The software also features a trigger that shows the current number of rows in the table before inserting new data 📍

<br>
<a id="erd"></a>

## ER-Diagram 🖼

Let's move on to the ER-Diagram section. The ERD consists of 9 entity sets, 27 attributes, and 8 relations 🖇. Below, you can view the ERD👇

<img width="874" alt="Er-diagram" src="https://user-images.githubusercontent.com/96326525/233801973-7373b260-301e-4c01-8c69-a212cad46bd9.png">


<br>

<a id="normalize"></a>

## Normalization ⚙️

TODO: Explanation of why the structure follows normal forms

<b> To normalize tables into 3NF, we need to follow the following steps: </b>

1. Identify the functional dependencies<br>
2. Remove the partial dependencies<br>
3. Remove the transitive dependencies<br>

<b>Table</b>: <code>Publishers</code>

<b>Attributes</b>: publisher_id [primary key], address, email, publisher_name, phone.
* there are no repeating groups, 1Nf
* publisher_id is the only candidate key, there are no partial dependencies, 2NF
* no transitive dependencies, 3NF

<b>Table</b>: <code>Books</code>

<b>Attributes</b>: book_id, author_id, publisher_id, name, price.
This satisfies the requirements of 3NF because there are no transitive dependencies and non-key atributes depend on primary key.




<b>Table</b>: <code>Reviews</code>

<b>Attributes</b>: text, rating, customer_id [foreign key].
The table is already in 1NF since all attributes contain atomic values. Since there is only one non-prime attribute ("text" and "rating" are both dependent on the entire primary key), the table is already in 2NF. There are no transitive dependencies in the table, so it is already in 3NF.




<b>Table</b>: <code>Cart</code>

<b>Attributes</b>: total_price, cart_id [primary key], customer_id [foreign key].
* The table is already in first normal form (1NF) because all attributes have atomic values.
* Second Normal Form (2NF): The table is already in 2NF since "total_price" is functionally reliant on the full primary key (i.e., "cart_id, customer_id").
* Third Normal Form (3NF): Because the table has no transitive relationships, it is already in 3NF.


<b>Table</b>: <code>Genre</code>

<b>Attributes</b>: genre_id (primary key), genre, age_group
* Since there are no repeating groups in the table, it is already in 1NF.
* Since the table only has one candidate key, which is the primary key, there are no partial dependencies to eliminate.
* There are no transitive dependencies and the table is already in 3NF.


<b>Table</b>: <code>Website</code>

<b>Attributes</b>: name, URL [primary key]
* 1NF -- > The table is already in first normal form (1NF) because all attributes have atomic values.
* 2NF -- > Second Normal Form (2NF): The table is already in 2NF since there is only one non-prime attribute ("name") present.
* 3NF -- > Third Normal Form (3NF): Because the table contains no transitive dependencies, it is already in 3NF.


<b>Table</b>: <code>Orders</code>

<b>Attributes</b>: order_id (primary key), customer_id(foreign key), order_date
* there are no repeating groups in the table so it is already in 1NF.
* the table only has one candidate key, it's primary key, there are no partial dependencies, so it's in 2NF.
* there are no transitive dependencies because there is one atribute that depends on primary key so it's in 3NF.


<b>Table</b>: <code>Authors</code>

<b>Attributes</b>: author_id(primary key), gender, num_books, address, name
* there are no repeating groups, so it's in 1nf
* author_id is the only candidate key, there are no partial dependencies in this table.
* there is no transitive dependency in this table so it is in 3NF.



<b>Table</b>: <code>Customers</code>

<b>Attributes</b>: c_name, age, address, customer_id [primary key].
* Table contains a single value [unique]
* It is a single-column primary key that is 1NF and independent of any subset of candidate key relations in terms of functionality.
* It is a 2NF and it has no transitive functional dependencies


<b>Table</b>: <code>Employees</code>

<b>Attributes</b>: employee_id (primary key), employee_name, title, salary



   
<a id="coding"></a>

## PL/SQL ‍💻

TODO: CODING PART
- Procedure which does group by information 

```sql
CREATE OR REPLACE PROCEDURE group_by_info
IS
  v_address authors.address%TYPE;
  v_count NUMBER;
BEGIN
  SELECT address, COUNT(*) INTO v_address, v_count
  FROM authors
  GROUP BY address;
END;
```


- Function which counts the number of records

```sql
CREATE OR REPLACE FUNCTION count_records
RETURN NUMBER
IS
   record_count NUMBER;
BEGIN
   SELECT COUNT(*) INTO record_count FROM authors;
   RETURN record_count;
END;
```

```sql
DECLARE
  v_count NUMBER;
BEGIN
  v_count := count_records();
  DBMS_OUTPUT.PUT_LINE('The number of records is: ' || v_count);
END;
```


- Procedure which uses SQL%ROWCOUNT to determine the number of rows affected
```sql
CREATE OR REPLACE PROCEDURE rows_affected
IS
   rows_processed NUMBER;
BEGIN
   UPDATE employees SET employee_name = 'Anuar Ospanov' WHERE employee_id = '1';
   rows_processed := SQL%ROWCOUNT;
   DBMS_OUTPUT.PUT_LINE('Number of rows affected: ' || rows_processed);
END;
```

- Add user-defined exception which disallows to enter title of item (e.g. book) to be less than 5 characters
- Create a trigger before insert on any entity which will show the current number of rows in the table
```sql
CREATE OR REPLACE TRIGGER count_rows_trigger
BEFORE INSERT ON books
DECLARE
   current_rows NUMBER;
BEGIN
   SELECT COUNT(*) INTO current_rows FROM books;
   DBMS_OUTPUT.PUT_LINE('Current number of rows in the table: ' || current_rows);
END;
```

