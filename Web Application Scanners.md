# What is a Scanner?

Before diving into what scanners are first lets take a loot at what web applications and vulnerabilities are. A web application is a software we access through a web browser. Examples includes Online banking portals, social media sites, E-commerce stores, email like gmail or outlook. These applications run on server that handle sensitive data like passwords, credit card numbers, and personal information.  

A vulnerability is a weakness or flaw in the web application that an attacker can exploit to do something malicious, such as: Steal user data, take control of the server, deface the website, access authorized information etc... Common vulnerabilities includes:
- **SQL Injection**: Attackers insert malicious database commands.
- **Cross Site Scripting (XSS)**: Attackers injects malicious scripts into web pages.
- **Cross-Site Request Forgery (CSRF)**: Attackers tricking users into performing unwanted actions.
- **Security Misconfigurations**: servers left in insecure default settings.

Since manually finding vulnerability is nearly impossible and very time conmsuming, security professionals use automated scanners which are specialised tools that crawl through a web application and test it for known vulnerabilities.
