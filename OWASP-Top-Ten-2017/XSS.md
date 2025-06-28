# Cross Site Scripting

In this web security vulnerability of the type injection, the web application allows javascript to be directly injected onto the application through an untrusted source, which can be abused by an attacker to further escalate it to a session hijacking or Command execution etc.

The different kinds of XSS are

* Reflected XSS
* Stored XSS
* DOM XSS

## Reflected XSS

**Definition**

* Reflected XSS occurs when the attacker injects the malicious javascript code via a web/HTTP request and the resulting execution of the same is triggered in the respective response of the very same request.

* This is actively exploited by delivering it to the victim by a precrafted link via mail aka using phishing/Social Engineering .

## Stored XSS

**Definiton**

* Stored XSS is the result of the script being executed on the browser/client side whenever the resource is being visited, which is the script/malicious code being loaded from the backend/server which was stored onto it in a previous request.

* This is exploited via resources which are stored on the backend/server and are being fetched whenever they are visited/requested such as Posts,Comments,Images etc etc...