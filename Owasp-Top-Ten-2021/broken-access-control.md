# Broken Access Control

* Authorization also known as access control is a huge part of modern day web applications.
* When an application fails to validate if a user has access to a particular sensitive/privileged endpoint, which leads to the web security vulnerability `Broken Access Control` 
* A simple example for the scenario would be a normal user with no privileges can access the following privileged endpoint

```console
https://www.target.com/admin/dashboard
```

* In this particular scenario the application fails to validate the privileges of the user, i.e. failed to check if an admin is trying to access the admin dashboard.
* This vulnerability is nothing but privilege escalation and can be categorized into two.
	* Horizontal PrivEsc
		* User A can read/write User B's data (profile,transactions,etc..)
	* Vertical PrivEsc
		* User A can read/write an Admin/Manager's data (dashboard,profile etc..)

## IDOR

* IDOR known as Indirect Object Reference, is a web security vulnerability where the web application fails to implement access control checks on objects.
* An object can be a user,data,services etc.., when a reference is being made to them by the web application, i.e. the object is requested by user and the application presents it without checking if the user has the right privileges to access this object.
* When a call is being made to check status of the user like

```
/User/CheckStatus HTTP 2.0
Host: www.target.com
Content-Type: Json
Content-Length: 5
{
	id: "23"
}
```

* Now we can try and change the `id` parameter to check if we can see the status of the other users, which if  returned with the desired results, in turn confirms the vulnerability.
* IDOR is not just limited to read the object, it's advised to test for all the CRUD operations.