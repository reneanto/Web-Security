# Injection

## Topics

* [SQL Injection](#sql-injection)
* [NoSQL Injection](#NoSQL-Injection)

## SQL-Injection

* SQL injection also known as SQLi is an injection based web security vulnerability, which occurs as a result of non moderated SQL queries made by the web application to the backend or the SQL database .

* These unrestricted SQL queries often lead to retrieval of confidential data which is not usually described in the application's routing

* SQLi can be further leveraged to compromise the backend via landing a shell in the Database and DDOS if the query takes too long to process or ends up corrupting the Database

**Detection**

* When a comment parameter ``` " ```  is passed by the application it often ends up commenting rest of what the actual query is supposed to be, this category of the SQLi is called as error based SQL Injection

* Upon discovering the above error, we can further exploit the vulnerability via passing SQL queries post the comment.


## NoSQL-Injection

* NoSQL injection occurs where the traditional SQL database is replaced by databases such as MongoDB which use custom application language like JSON,XML and in case of MongoDB it's Binary JSON aka bson.
  
* The queries here are specific to  application's programming language, for example, the query `SELECT * FROM products` corresponds to `db.collection('products').find({});` where `*` is conveyed as `{}` .

**Detection**

* There are two types of NoSQL injection, Syntax and Operator Injection.

* Syntax injection happens when the NoSQL query is exploited in a way similar to that in SQL injection to inject our desired payload, the syntax varies according to the database used.
* we can further fuzz them with syntax specific strings that trigger a database error at a point.

*  for example if an website uses a url query like `www.website.com/products?filter=new` it might relate in the sytnax such as `products.filter == 'new'` we can fuzz this with a string like 
	`' "{`
	`;$Null}`
	`$Null \aBc`  

* The most often query escaping character is `\`, if this doesn't cause an error then it is an indication that the application is vulnerable to NoSQLI.

* Once detected the vulnerability can be confirmed with conditional statements such as ` ' && 0 &&'x` or `' && 1 && 'x` 

* one way to override existing conditions as in SQLI `' or '1'=='1'` in NoSQLI is `'||'1'=='1`
* Another way to to override existing conditions is to use a Null character which goes like `new'%00`

* Operator injection is the result when we manipulate the query with the operators.

*  The operators are 

```json
--Comparision based Operators--

$eq: Values are equal
$ne: Values are not equal
$gt: Value is greater than another value
$gte: Value is greater than or equal to another value
$lt: Value is less than another value
$lte: Value is less than or equal to another value
$in: Value is matched within an 

---Logical Operators---

$and: Returns documents where both queries match
$or: Returns documents where either query matches
$nor: Returns documents where both queries fail to match
$not: Returns documents where the query does not match

---Evaluation based Operators---

$regex: Allows the use of regular expressions when evaluating field values
$text: Performs a text search
$where: Uses a JavaScript expression to match documents

```

* An example query for submitting a login query can be exploited like

```json
{"username":{"$ne":"invalid"},"password":{"$ne":"invalid"}} --> bypass authentication

{"username":{"$regex":"admin.*"},"password":{"$ne":"invalid"}} --> bypass with admin

{"username":{"$in":["admin","administrator","superadmin"]},"password":{"$ne":""}} --> login to specific account via authentication bypass
```