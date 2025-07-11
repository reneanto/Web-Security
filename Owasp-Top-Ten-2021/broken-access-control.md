# Broken Access Control

* Authorization also known as access control is a huge part of modern day web applications.
* When an application fails to validate if a user has access to a particular sensitive/privileged endpoint, which leads to the web security vulnerability `Broken Access Control` 
* A simple example for the scenario would be a normal user with no privileges can access the following privileged endpoint

```console
https://www.target.com/admin/dashboard
```

* In this particular scenario the application fails to validate the privileges of the user, i.e. failed to check if an admin is trying to access the admin dashboard.