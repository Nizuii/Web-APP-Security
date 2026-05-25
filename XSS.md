# What is XSS?

**XSS (Cross-Site Scripting)** is a type of security vulnerability found in web applications. It allows attackers to inject malicious scripts into web pages that other users view. The name Cross-Site is a bit misleading today. Originally, it referred to scripts from one site executing in the context of another. Now it broadly means injecting malicious code into a trusted website.  
Now lets take a look at how it works. Imagine a website that displays user input without checking it properly. An attacker can submit something like:
```bash
<script>alert('Hacked!')</script>
```
If the website simply displays this on the page, the browser treats it as real JavaScript and executes it. Now imagine instead of alert(), the script steals cookies or sends data to the attacker's server.
