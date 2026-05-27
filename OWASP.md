# What is OWASP?

**OWASP** stands for **Open Worldwide Application Security Project**. It is a nonprofit organization that focuses on making softwares more secure. Think of them as the "safety inspectors" of the internet. They publish a list called the **OWASP Top 10**. It is basically a ranking of the 10 most dangerous security risks that web applications face today.

The OWASP Top 10 for 2025 are:

<table>
  <tr>
    <th>Rank</th>
    <th>Risk</th>
    <th>Simple Explanation</th>
  </tr>
  <tr>
    <td>A01</td>
    <td>Broken Access Control</td>
    <td>Imagine a hotel where any guest's key card can open any room. That's broken access control - Users can access things they shouldn't.</td>
  </tr>
  <tr>
    <td>A02</td>
    <td>Security Misconfiguration</td>
    <td>Leaving doors unlocked, windows open or using default passwords. Software is setup wrong, leaving holes attackers can walk through.</td>
  </tr>
  <tr>
    <td>A03</td>
    <td>Software Supply Chain Failures</td>
    <td>You buy a phone, but the charger that came in the box was tampered with at the factory. Bad code sneaks in through third party libraries or build tools.</td>
  </tr>
  <tr>
    <td>A04</td>
    <td>Cryptographic Failures</td>
    <td>Sending a secret letter but using a code that a 5 year old could crack. Encryption is weak or missing, so sensitive data gets exposed.</td>
  </tr>
  <tr>
    <td>A05</td>
    <td>Injection</td>
    <td>You ask someone "Waht is your name?" and they reply with a command that makes your computer to do something bad. Untrusted input gets treated as a command.</td>
  </tr>
  <tr>
    <td>A06</td>
    <td>Insecure Designs</td>
    <td>The building was designed with no fire escapes. The architecture itself is flawed, not just a mistake in implementation.</td>
  </tr>
  <tr>
    <td>A07</td>
    <td>Authentication Failures</td>
    <td>The bouncer at a club lets anyone in because he doesn't check ID's properly. Login systems are weak or bypassable.</td>
  </tr>
  <tr>
    <td>A08</td>
    <td>Software Data Integrity Failures</td>
    <td>Someone swaps your download with a fake version. Code or data gets modified without you knowing.</td>
  </tr>
  <tr>
    <td>A09</td>
    <td>Security Logging & Alerting Failures</td>
    <td>A burglar breaks in, but there are no cameras and no alarms. You don't even know you were attacked.</td>
  </tr>
  <tr>
    <td>A10</td>
    <td>Mishandling of Exceptional Conditions</td>
    <td>When something goes wrong, the system panics and reveals secrets like error messages showing passwords.</td>
  </tr>
</table>

## 1. A01 - Broken Access Control.

Access control is the system that decides who can do what in an application. When it's broken, users can access data or perform actions that they shouldn't be allowed to do. Imagine a hospital scenario where every doctors key card opens every patients room, not just their assigned patients. Or worse -  a visitor's card opens the pharmacy. That is broken access control. Common examples are:
- A regular user can access an admin dashboard just by changing the URL from `/user/dashboard` to `/admin/dashboard`.
- You can view another user's order history by simply changing the order ID in the URL (`/orders/1234` ➡️ `/orders/1235`).
- An API lets you delete any account, not just your own.

It is often the easiest vulnerability to exploit. No special tools needed - just modify a URL parameter and boom, you are in someone else's account. Inorder to prevent it:
- Deny access by default - if a page/resource isn't explicitly allowed, block it.
- Validate access on the server side.
- Use proper session management and role based access control.
- Log access control failures and alert on them.

## 2. A02 - Security Misconfiguration.

The application or its infrastructure is setup incorrectly - default passwords, unnecessary features enabled, error messages revealing too much, outdated software, etc... Real life anolagies are:
- Leave the default lock code as `0000`.
- Dont lock the lock bar.
- Leave the construction crew's spare key under the mat.
- Have a sign in the front yard saying "Alarm code is 1234".

That's security misconfiguration. Common examples are:
- Default admin credentials like `admin/admin` or `root/passowrd`.
- Error pages showing full stack traces with database passwords.
- Unnessary services running (like a test database exposed to the internet).
- Missing security headers on web pages.

It's not one bug. It's a category of "slopiness" that creates many entry points. Attackers use automated scanners to find misconfigured systems constantly. Inorder to prevent it:
- Remove default accounts and change default passwords immediately.
- Disable unnecessary features, ports, and services.
- Keep software patched and updated.
- Send HTTP headers with every HTTP response.

## A03 - Software Supply Chain Failures.

Modern softwares are built like a chain - your app depends on libraries, which depend on other libraries, which depend on more libraries. If any link in that chain is compromised, your entire app is at risk. Imagine a scenario that you buy a car. The car is fine, But the tires were made in a factory that used defective rubber. The car crashes because of the tires. You trusted the tire supplier, but they let you down. Or think of it like a restaurant: you serve a salad, but the lettuce supplier had an E. coli outbreak. Your restaurant gets blamed even though you didn't grow the lettuce. Commom examples are:
- A popular JS library (like `colors` or `node-ipc`) gets hijacked and starts stealing data.
- A developer downloads a malicious package from a public repository that looks legitimate.
- A build tool or CI/CD pipeline is compromised, injecting malware into your software before it's even released.
- Using outdated libraries with known vulnerabilities.

### Famous Real Incidents

- **SolarWinds (2020)**: Attackers compromised the build process of a widely-used IT management tool, pushing malware to 18,000+ organizations, including government agencies.
- **Log4j (2021)**: A logging library used by millions of applications had a critical vulnerability.

Inorder to prevent it:
- Use only trusted, verified libraries
- Keep dependencies updated and monitor for vulnerabilities
- Verify software integrity using checksums and digital signatures
- Use Software Composition Analysis (SCA) tools to scan your dependencies
- Isolate and secure your build environments

## A04 — Cryptographic Failures

Sensitive data is not properly protected using encryption. This includes data in transit (moving across the internet) and data at rest (stored in databases). Think of a real world analogy like you are sending a secret letter to a friend. Instead of sealing it in an envelope, you:
- Send it on a postcard (anyone can read it)
- Use a "code" that is just reversing the alphabet (a child could crack it)
- Leave copies of the letter lying around your house
That's cryptographic failure. Common examples includes:
- Storing passwords in plain text (never do this!)
- Using outdated or weak encryption algorithms like MD5 or SHA-1
- Not using HTTPS — sending data over unencrypted HTTP
- Hardcoding encryption keys in the source code
- Not encrypting database backups

It is dangerous because ff an attacker gets access to your database or intercepts network traffic, they can read everything. Passwords, credit card numbers, personal messages — all exposed. Inorder to prevent it:
- Use strong, modern encryption (AES-256, RSA-2048, ChaCha20)
- Always use HTTPS/TLS for data in transit
- Hash passwords using strong algorithms like bcrypt, Argon2, or PBKDF2
- Never hardcode keys — use secure key management systems
- Encrypt sensitive data at rest (databases, backups, logs)

## A05 — Injection

Untrusted user input is sent to an interpreter (like a database, operating system, or browser) as part of a command or query. The interpreter executes the malicious input as code. Think of a real world analogy like you go to a restaurant and order: "Burger and fries; also, give me all the money from the cash register." If the waiter blindly writes down your entire order and hands it to the kitchen without checking, the kitchen might actually try to give you the money. That's injection — the system trusted your input and treated it as an instruction. Common types are:
<table>
  <tr>
    <th>Type</th>
    <th>What it targets</th>
    <th>Example</th>
  </tr>
  <tr>
    <td>SQL Injection</td>
    <td>Databases</td>
    <td>Inputting ' OR '1'='1 into a login field to bypass authentication</td>
  </tr>
  <tr>
    <td>Command Injection</td>
    <td>Operating System</td>
    <td>Inputting ; rm -rf / into a web form that runs shell commands</td>
  </tr>
  <tr>
    <td>LDAP Injection</td>
    <td>Directory services</td>
    <td>Manipulating LDAP queries to access unauthorized data</td>
  </tr>
  <tr>
    <td>NoSQL Injection</td>
    <td>NoSQL databases</td>
    <td>Injecting malicious JSON into MongoDB queries</td>
  </tr>
  <tr>
    <td>XPath Injection</td>
    <td>XML documents</td>
    <td>Manipulating XML path queries</td>
  </tr>
</table>

Prevention methoods are:

- Never trust user input — validate and sanitize everything
- Use parameterized queries (prepared statements) — separate code from data
- Use an ORM (Object-Relational Mapping) that handles escaping automatically
- Apply the principle of least privilege to database accounts
- Use Web Application Firewalls (WAFs) as an extra layer

## A06 - Insecure Design
This is a fundamental flaw in the architecture or design of the application — not just a coding mistake. The system was designed in a way that makes security impossible or very difficult. Think of a real world analogy. We design a bank vault, but:
- We put the vault door on the outside wall facing the street
- The ventilation shaft is wide enough for a person to crawl through
- There's no alarm system, just a "Please don't steal" sign

No matter how well you build it, the design itself is insecure. Common examples include:

- A business workflow that allows users to change prices before checkout
- A password reset flow that only asks for an email (no secondary verification)
- An e-commerce site that processes payments on the client side (where users can modify the price)
- Designing a system where sensitive data flows through untrusted components

Now lets look at how to prevent it:

- Use threat modeling — think like an attacker during the design phase
- Apply secure design patterns and principles (defense in depth, least privilege)
- Segregate components by trust level
- Validate business logic, not just technical inputs
- Review designs with security experts before coding begins

## A07 — Authentication Failures 

The mechanisms that verify who a user is (login systems) are weak, broken, or bypassable. Attackers can impersonate legitimate users. Think of a real world analogy. Imagine a nightclub where:
- The bouncer doesn't check IDs properly
- Anyone can say "I'm on the list" and get in
- VIP passes are easy to photocopy
- The back door is always unlocked
- If you guess someone's birthday, you can reset their VIP membership

That's authentication failure — the system meant to verify identity is broken. Common examples are:

- **Weak password policies:** Allowing passwords like "123456" or "password"
- **Credential stuffing:** Attackers use leaked username/password combos from other breaches because people reuse passwords
- **Brute force attacks:** No rate limiting — an attacker can try millions of passwords
- **Session hijacking:** Session tokens (cookies) don't expire or are predictable
- **Missing MFA:** No multi-factor authentication — if someone guesses your password, they're in
- **Insecure password reset:** Reset links sent over HTTP, or links that don't expire

How to prevent it:

- Enforce strong password policies (length > complexity)
- Implement Multi-Factor Authentication (MFA) wherever possible
- Rate-limit login attempts to stop brute force
- Use secure session management — random tokens, proper expiration, HTTPS-only
- Check passwords against known breach databases (like HaveIBeenPwned)
- Don't implement your own authentication — use battle-tested frameworks (OAuth, OpenID Connect)

## A08 - Software or Data Integrity Failures

Code or data is modified without authorization, and the system doesn't detect it. This includes insecure deserialization, untrusted dependencies, and lack of integrity verification. Imagine a real world scenario:  
You order a package from Amazon. Someone intercepts it, opens the box, replaces your laptop with a brick, reseals it, and delivers it. You open it and have no idea it was tampered with because the box looked fine. That's a data integrity failure — the content changed, but there was no way to detect it. Common examples are:
- **Insecure Deserialization:** An application receives a serialized object (like a saved user session) and blindly trusts it. An attacker modifies the object to include malicious code, and the app executes it.
- **No integrity checks on updates:** Your app auto-updates but doesn't verify the update file's signature. An attacker replaces it with malware.
- **CI/CD pipeline tampering:** Code is modified during the build process before deployment
- **Unsigned software:** Users download your app, but there's no way to verify it came from you

Now lets take a loot at how to prevent it:
- Never deserialize untrusted data
- Use integrity checks (digital signatures, checksums) for all data and updates
- Verify software signatures before installation
- Use serialization formats that only contain data, not code (like JSON instead of pickle in Python)
- Implement a software bill of materials (SBOM) to track what goes into your software

## A09 — Security Logging & Alerting Failures
When something bad happens, nobody knows about it. There's no logging, no monitoring, no alerting. Attackers can break in, steal data, and leave — and you won't even realize it happened until months later (if ever). Now lets take a real world analogy. You own a jewelry store:
- There are no security cameras
- The alarm system is turned off
- The motion sensors are broken
- The security guard sleeps on the job

A burglar breaks in, cleans out the vault, and leaves. You come in the next morning and everything looks normal until you open the vault. You have no idea when it happened, who did it, or how they got in. That's logging and alerting failure. Common examples are:
- No logs for login attempts (successful or failed)
- No logs for sensitive actions (password changes, money transfers, admin actions)
- Logs exist but aren't monitored — they just sit in a file nobody reads
- No alerts for suspicious patterns (e.g., 1000 failed logins in 1 minute)
- Logs are stored locally and get deleted when the server is compromised
- Logs contain sensitive data (passwords, credit cards) — which is a privacy risk

 Now lets look at the prevention methods:

- Log all authentication attempts, access control failures, and input validation errors
- Generate logs with enough detail to identify attackers (but not so much that you log passwords)
- Store logs in a centralized, tamper-resistant system (not just on the server)
- Set up real-time alerting for suspicious activity
- Regularly review and test your logging and alerting systems

## A10 — Mishandling of Exceptional Conditions 
When something unexpected happens (an error, exception, or edge case), the application doesn't handle it gracefully. Instead, it might crash, expose sensitive information, or behave unpredictably — giving attackers clues or opening new vulnerabilities. Think of a real world analogy: You're at a bank and ask the teller for something they can't do (like withdraw money from a closed account). Instead of saying "I can't do that," the teller:
- Panics and shows you the bank's internal ledger
- Starts crying and reveals the vault combination
- Freezes up, leaving the drawer open

That's mishandling an exceptional condition — the error itself becomes a vulnerability. Common examples are:

- **Verbose error messages:** A database error reveals the table structure: `Table 'users' doesn't exist` — now the attacker knows your database schema
- **Stack traces in production:** Error pages show file paths, function names, and sometimes even credentials
- **Race conditions:** Two users try to buy the last item simultaneously. The app doesn't handle it, so both succeed and you oversell.
- **Resource exhaustion:** An attacker sends a specially crafted request that causes the app to use all memory/CPU, crashing it (Denial of Service)
- **Integer overflow:** A calculation produces a number too large, wrapping around to a negative number — possibly bypassing security checks

Now lets take a look at the prevention methods:

- Catch and handle all exceptions gracefully
- Show generic error messages to users; log detailed errors server-side
- Never expose stack traces, file paths, or database details in production
- Test for edge cases and unexpected inputs
- Implement rate limiting and resource controls to prevent DoS
- Use fuzz testing (sending random/garbage input) to find unexpected behavior
