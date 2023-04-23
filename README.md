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

<b>Table</b>: <code>Publisher</code>

<b>Attributes</b>: publisher id [primary key], address, email, name, phone.

This table is already in 3NF. It has a <code>primary key </code>, and there are no partial or transitive dependencies. Therefore, normalization is not required.




<b>Table</b>: <code>Books</code>

<b>Attributes</b>: book_id, author_id, publisher_id, name, price.
This satisfies the requirements of 3NF because there are no transitive dependencies and all non-key attributes are dependent on the primary key of each table.




<b>Table</b>: <code>Reviews</code>

<b>Attributes</b>: text, rating, customer_id [foreign key].
The table is already in 1NF since all attributes contain atomic values. Since there is only one non-prime attribute ("text" and "rating" are both dependent on the entire primary key), the table is already in 2NF. There are no transitive dependencies in the table, so it is already in 3NF.




<b>Table</b>: <code>Cart</code>

<b>Attributes</b>: total_price, cart_id [primary key], customer_id[foreign key].
* The table is already in first normal form (1NF) because all attributes have atomic values.
* Second Normal Form (2NF): The table is already in 2NF since "total_price" is functionally reliant on the full primary key (i.e., "cart_id, customer_id").
* Third Normal Form (3NF): Because the table has no transitive relationships, it is already in 3NF.


<b>Table</b>: <code></code>

<b>Attributes</b>: 
write________________


<b>Table</b>: <code></code>

<b>Attributes</b>: 
write________________


<b>Table</b>: <code></code>

<b>Attributes</b>: 
write________________


<b>Table</b>: <code></code>

<b>Attributes</b>: 
write________________


<b>Table</b>: <code></code>

<b>Attributes</b>: 
write________________


<b>Table</b>: <code></code>

<b>Attributes</b>: 
write________________



   
<a id="coding"></a>

## PL/SQL ‍💻

TODO: CODING PART
- Procedure which does group by information 
- Function which counts the number of records 
- Procedure which uses SQL%ROWCOUNT to determine the number of rows affected
- Add user-defined exception which disallows to enter title of item (e.g. book) to be less than 5 characters
- Create a trigger before insert on any entity which will show the current number of rows in the table
