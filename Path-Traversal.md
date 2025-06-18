# Path Traversal

Path traversal is a web security vulnerability where the application with it's immoderation allows users to access the sensitive server resources such as `/etc/passwd` `/home/user/.ssh/public_id_rsa` via the URL path.

The impact is not just limited to the server native files, it might lead to retrieval of other sensitive data such as `/opt/application/users.json` or `/var/www/html/site/db.php` these folders and files contain even sensitive information about the application than of the server which is crucial to the business.

This can often be chained with file upload and other vulnerabilities to trigger RCE

one such example can be 

arbitrarily send single line php command injection payload to the ftp server in password or username while logging into the ftp server or the apache based web server

then access `/var/ftp/logs/error.log?cmd=ls` or `/var/apache/logs/login-errors.log?cmd=pwd`
