
# Local File Inclusion

* LFI is a web security vulerability where the application fails to negate the arbitrary loading/inclusion of server side resources onto the web application.
* In general, this occurs when a functionality of the application is to include files from the servers is abused
* per say to load an pdf version of the transaction on before printing it and it's being fetched as

```console
https://www.target.com/transaction/preview?file=pid.pdf
```

* Now to identify the vulnerability we try to load the `index.html` or any page that is local to the `web directory/root` itself 