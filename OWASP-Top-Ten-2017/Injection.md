# Injection

## Topics

* [SQL Injection](#sql-injection)

## SQL Injection

* SQL injection also known as SQLi is an injection based web security vulnerability, which occurs as a result of non moderated SQL queries made by the web application to the backend or the SQL database .

* These unrestricted SQL queries often lead to retrieval of confidential data which is not usually described in the application's routing

* SQLi can be further leveraged to compromise the backend via landing a shell in the Database and DDOS if the query takes too long to process or ends up corrupting the Database

### Detection

* When a comment parameter ``` " ```  is passed by the application it often ends up commenting rest of what the actual query is supposed to be, this category of the SQLi is called as error based SQL Injection