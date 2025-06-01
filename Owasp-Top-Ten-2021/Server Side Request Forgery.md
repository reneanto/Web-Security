
## Definition

SSRF aka Server Side Request Forgery is a web security vulnerability where an attacker utilizes the application to request restricted resources from the server, which often turn out to be only accessible internally.

## Impact

The Impact Varies from Critical to Medium where in instances the SSRF can be further levied to get console level access to the server via command execution, internal network scan of the infrastructure and the least being exposing internal services that are being used on the server.

## Example

* Consider an application importing swagger json endpoint for api mapping and takes the URL pointing to the swagger documentation as the input 
* This application functionality can be abused to access server side resources in many ways with the following payloads.
* `http://localhost/etc/passwd` alternatives can be used as octal,hexa,ipv6 notations to bypass the blacklist.
* `https://192.168.10.0-255` this is an example to specify the network scanning via ssrf, the https blacklist can be bypassed by switching to other protocols such as http,tcp,gopher etc.
* `http://169.254.169.254/latest/meta-data/` access aws data.

* More Payloads can be found [here](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Request%20Forgery) 