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

<b> To normalize tables into 3NF, we need to follow the following steps:

1.Identify the functional dependencies
2.Remove the partial dependencies
3.Remove the transitive dependencies

</b>

<b>Table</b>: <code>Publisher</code>

<b>Attributes</b>: publisher id [primary key], address, email, name, phone.

This table is already in 3NF. It has a <code>primary key </code>, and there are no partial or transitive dependencies. Therefore, normalization is not required.

<a id="coding"></a>

## PL/SQL ‍💻

TODO: CODING PART
- Procedure which does group by information 
- Function which counts the number of records 
- Procedure which uses SQL%ROWCOUNT to determine the number of rows affected
- Add user-defined exception which disallows to enter title of item (e.g. book) to be less than 5 characters
- Create a trigger before insert on any entity which will show the current number of rows in the table
