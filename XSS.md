# What is XSS?

**XSS (Cross-Site Scripting)** is a type of security vulnerability found in web applications. It allows attackers to inject malicious scripts into web pages that other users view. The name Cross-Site is a bit misleading today. Originally, it referred to scripts from one site executing in the context of another. Now it broadly means injecting malicious code into a trusted website.  
Now lets take a look at how it works. Imagine a website that displays user input without checking it properly. An attacker can submit something like:
```bash
<script>alert('Hacked!')</script>
```
If the website simply displays this on the page, the browser treats it as real JavaScript and executes it. Now imagine instead of alert(), the script steals cookies or sends data to the attacker's server. Now lets take a look at three types of XSS:

## 1. Reflected XSS

The malicious script is in the URL itself. The server "reflects" it back in the response. The victim has to click a crafted link.  
**Real scenario**: A search page shows "You searched for: [your input]". If the attacker crafts a URL like `search?q=<script>stealCookies()</script>` and tricks you into clicking it, the server echoes that script into the page, your browser runs it.
- The script is NOT stored anywhere permanently
- Only the person who clicks the evil link is affected
- It travels via a malicious link (email, chat, etc.)

## 2. Stored XSS (also called Persistent XSS)
The malicious script is saved into the website's database. Every user who loads that page gets attacked — automatically, no link-clicking needed.
**Real scenario**: A comment section on a blog. Attacker posts a comment containing <script>stealCookies()</script>. The site saves it to the database. Now every person who reads that blog post runs the attacker's code in their browser.
- The script IS stored permanently on the server
- Every visitor is affected, not just one
- Most dangerous type


**Real scenario**: A page has JavaScript that does `document.getElementById('msg').innerHTML = location.hash`. An attacker sends a link like `page.html#<img src=x onerror=stealCookies()>`. The server never sees the attack — your own browser's JavaScript does the damage.
- Server never sees the payload
- Purely a JavaScript-side vulnerability
- Hardest to detect for traditional scanners

