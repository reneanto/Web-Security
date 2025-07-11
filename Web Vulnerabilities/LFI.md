
# Local File Inclusion

* LFI is a web security vulnerability where the application fails to negate the arbitrary loading/inclusion of server side resources onto the web application.
* In general, this occurs when a functionality of the application is to include files from the servers is abused
* per say to load an pdf version of the transaction on before printing it and it's being fetched as

```console
https://www.target.com/transaction/preview?file=pid.pdf
```

* Now to identify the vulnerability we try to load the `index.html` or any page that is local to the `web directory/root` itself 

``` console
https://www.target.com/transaction/preview?file=index.html
```

* We can observe that the index.html page was being rendered onto the browser
* This can be further leveraged to load sensitive files such as `/etc/passwd`

```console
https://www.target.com/transaction/preview?file=../../../../../../etc/passwd
```

## LFI vs Directory Traversal

* The main difference between LFI and Directory traversal is
	* In Directory Traversal you can only read/retrieve data, i.e. data won't be rendered onto the front end.
	* Where as in LFI the data will be included, i.e. rendered by the application onto the client side, which leads to potential issues such as RCE.

