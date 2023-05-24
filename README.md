# BookStore 📚

## Overview 📙

The "Bookstore 📚" repository is a project developed for a database management system course ⚙️. The purpose of the project is to design and implement a database management system for an online book shop 🛍️

<br>

## Table of Links 📄
#### 1. <a href="https://docs.google.com/presentation/d/10Zp-Qr_TWKR9FG4UQcXwb0Lfp0XqOSTvhHAa7u5Cyjg/edit#slide=id.p">Presentation Link</a>
#### 2. <a href="https://youtu.be/T44gVQuIYC8">YouTube Link</a>
#### 3. <a href="https://github.com/Shyngys001/BookStore-Management-System">GitHub Link</a>

<br>

## Introduction 📝

The main goal of this project is to develop a software for the effective management of an online bookstore's database 🪧. The software is designed to be used by online shoppers 🛍️. Customers can order books using the online store 📦, and employees can easily update the website with new books and features✨

#### Features:
1. The software includes a grouping procedure to organize information efficiently 👾
2. It has a function that counts the total number of records 🤖
3. A procedure is available to determine the number of rows affected 🔖
4. Our software has user-defined exceptions, which prevent the entry of book names that are less than 5 characters 👻
5. The software also features a trigger that shows the current number of rows in the table before inserting new data 📍
<br>

## IDs of Teammembers:
* 210103370
* 210107180
* 210103362
* 210103418
* 210103205

# <p align="center">Final 📑</p>

### What's new?
We have made some updates to our project. Firstly, we have transitioned all our data to a NoSQL format, specifically MongoDB. Additionally, we have implemented several queries tailored for MongoDB🍃 to efficiently retrieve and manipulate data within the repository. These queries ⚙️ have been specifically designed to optimize performance and enhance overall functionality. Below, you will find a list of queries.👇

## Queries:
### 1. Show all customers who have written reviews 📇
```js
db.customers.aggregate([
  {
    $lookup: {
      from: 'reviews',
      localField: '_id',
      foreignField: 'customer_id',
      as: 'reviews'
    }
  },
  {
    $match: {
      reviews: { $exists: true, $ne: [] }
    }
  },
  {
    $project: {
      _id: 1,
      name: 1
    }
  }
])

```

### 2. Print the minimum and maximum prices of books 📚
```js
db.books.aggregate([
  {
    $group: {
      _id: null,
      minPrice: { $min: '$price' },
      maxPrice: { $max: '$price' }
    }
  },
  {
    $project: {
      _id: 0,
      minPrice: 1,
      maxPrice: 1
    }
  }
])
```

### 3. Print name and salary of Frontend employees 💻
```js
db.employees.find(
  {title: "Frontend Developer"}, 
  {_id: 0}
)
```

### 4. Find the average salary of employees of a specific position who work in the bookStore. If it's decimal, convert it to int and show the result 💡
```js
const employeePosition = "Backend Developer"
db.employees.aggregate([
  {
    $match: {title: employeePosition}
  },
  {
    $group: {
      _id: null,
      averageSalary: { $avg: "$salary" }
    }
  },
  { 
    $addFields: { 
      convertedSalarytoInt: { $concat: [ { $toString: { $toInt: "$averageSalary" }}, " $"] }
    } 
  }
])
```

### 5. Retrieve the total number of books in your bookStore 📒
```js
db.books.countDocuments()
```

### 6. List all authors who have published more than five books 📋
```js
db.authors.find({numBooks: {$gt : 5}}, {name : true, numBooks: true, _id: false})
```

### 7. List: name and price of all books published by a specific publisher 📃
(id : 2172280151)
```js
db.books.find({publisher_id: "2172280151"}, {bookName: true, price: true, publisher_id:
true, _id: false});
```

### 8. Find all books ordered by a specific customer 📜 
```js
db.orders.aggregate([
{
  $match: {
    customer_id: ObjectId("6469eb14da0b8e34ca487d81")
  }
},
{
  $lookup: {
    from: "customers",
    localField: "customer_id",
    foreignField: "_id",
    as: "books"
  }
}
])
```


### 9. List the books with the most reviews. 📜 
```js
db.books.aggregate([
{
$lookup: {
from: "reviews",
localField: "_id",
foreignField: "book_id",
as: "reviews"
}
},
{
$project: {
_id: 1,
bookName: 1,
reviewCount: { $size: "$reviews" }
}
},
{$match: {
reviewCount: {$ne : 0}
}
}
])
```

### 10. List books with drama genres.📜 
```js
db.genre.aggregate([
{
$lookup: {
from: 'books',
localField: 'book_id',
foreignField: '_id',
as: 'genres'
}
},
{
$match: {
genre: "Drama"
}
}
])
```

### 13.1. Display the details of the employee with the lowest salary.
```js
db.employees.find().sort({ salary: 1 }).limit(1)
```


### 13.2. Retrieve books within a particular price range
```js
db.books.find({ price: { $gte: 10, $lte: 50 } })
```



### 14. Retrieve the total revenue generated from all orders in your cart.
```js
db.cart.aggregate([
{
  $group: {
    _id: null,
    totalRevenue: { $sum: "$totalPrice" }
  } 
}
])
```

### 15.1 Find the book with the highest price.
```js
db.books.find().sort({ price: -1 }).limit(1)
```


### 15.2 Calculate the average price of books in a specific genre or category.
```js
db.books.aggregate([
  { 
    $match: { 
      genre: "Comedy" 
    } 
  },
  { 
    $group: { 
      _id: null, 
      averagePrice: { $avg: "$price" } 
    } 
  }
])
```



### 16. Find all customers who have placed orders.
```js
db.customers.aggregate([ 
{
  $lookup: {
    from: "orders",
    localField: "_id", 
    foreignField: "customer_id", 
    as: "orders"
  } 
},
{
  $match: {
    "orders": { $ne: [] } 
  }
} 
])
```



Feel free to explore these queries and utilize them to interact with our MongoDB database effectively.<br>
If you have any questions or need assistance, please don't hesitate to reach out.<br>
Happy coding! 🤗
