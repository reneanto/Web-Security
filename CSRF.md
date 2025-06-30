
Definition:

Cross Site Request Forgery is a web security vulnerability where an attacker impersonates/makes a user performed action that the user doesn't intend perform in their current active session.

This includes manipulating the user to perform an action with their active session where the cookies are not protected , i.e. makes use of the user's cookies to perform a malicious *state changing* action in the victim's current session.

This attack can be further chained with an underlying XSS/htmli vulnerability, i.e. to perform a sensitive action with the cookies captured by the xss exploit


```html
<img src='https://test.com/products/id=1&?buy=credit'>
```

Prevention:

* Using Anti-Csrf Tokens in the request such as `xsrf-token:` header or `double submit cookie` methods.
* SameSite setting  being set to either `None` or `lax` according to the application's functionality.
* Validation based on the `Refere:` header.

Bypasses:

* changing the method type, i.e change the method `POST` to `GET` or `PUT` .
* Stagnant CSRF token or the application is not checking for CSRF token value even if the token is present.
* CSRF token not tied to a specific user's session
* CSRF token and session handling are not integrated together
* using an arbitrary value in double submit cookie where the application doesn't validate the same.
* Application's not actually checking  for a referer header.
* If the application expects a regex in the referer then we can use a controlled domain that starts with the regex.