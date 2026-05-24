# What is a Scanner?

Before diving into what scanners are first lets take a loot at what web applications and vulnerabilities are. A web application is a software we access through a web browser. Examples includes Online banking portals, social media sites, E-commerce stores, email like gmail or outlook. These applications run on server that handle sensitive data like passwords, credit card numbers, and personal information.  

A vulnerability is a weakness or flaw in the web application that an attacker can exploit to do something malicious, such as: Steal user data, take control of the server, deface the website, access authorized information etc... Common vulnerabilities includes:
- **SQL Injection**: Attackers insert malicious database commands.
- **Cross Site Scripting (XSS)**: Attackers injects malicious scripts into web pages.
- **Cross-Site Request Forgery (CSRF)**: Attackers tricking users into performing unwanted actions.
- **Security Misconfigurations**: servers left in insecure default settings.

Since manually finding vulnerability is nearly impossible and very time conmsuming, security professionals use automated scanners which are specialised tools that crawl through a web application and test it for known vulnerabilities. Now lets go through some known scanner mainly used by testers inorder to scan web apps:

## 1. Nikto
**Nikto** is an open source web scanner that looks for dangerous files, outdated software and misconfigurations. What it does is it scans web servers for 6,700+ known vulnerabilities, checks for outdated server softwares, identifies default files and configurations that might be insecure, looks for common web server misconfigurations. For begginers its simple, free and runs from the command line. Example:

```bash
nikto -h http://targetwebsite.com
```

 <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/feedc8b9-11a3-45c1-bd40-1010699b2c21" />

## 2. OpenVas
**OpenVas** is a full-featured vulnerability scanner that checks for security issues across networks, not just web apps. What it does is: scans for thousands of known vulnerabilities (CVE's), provides detailed reports with risk ratings, can scan entire networks, not just single web servers, uses a constantly updated database of vulnerability tests. It is comprehensive and used by many security professionals worldwide.
