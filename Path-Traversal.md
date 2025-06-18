# Path Traversal

Path traversal aka directory traversal is a web security vulnerability where the application with it's immoderation allows users to read the sensitive server resources such as `/etc/passwd` `/home/user/.ssh/public_id_rsa` via the URL path.

The impact is not just limited to the server native files, it might lead to retrieval of other sensitive data such as `/opt/application/users.json` or `/var/www/html/site/db.php` these folders and files contain even sensitive information about the application than of the server which is crucial to the business.

we can exploit this vulnerability by  parsing through directories via path

* `https://www.target.com/file?path=/etc/passwd` 
* `https://www.target.com/file?path=/images/img.svg/../../../../../etc/passwd`
* `https://www.target.com/file?path=/images/img.svg//..//..//..//..//..//..//etc//passwd
* `https://www.target.com/file?path=/opt/application/users.json%00