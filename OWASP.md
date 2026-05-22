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

That's security misconfiguration.
