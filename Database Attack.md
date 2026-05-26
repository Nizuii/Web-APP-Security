# Database Server Attack.

A database server is a computer that stores, manages and serves data to other computers (clients). Think of it as a digital filing cabinet that holds information like usernames, passwords, credit card numbers, etc... Common database systems are:
- **MySQL** - Very popular, open source.
- **PostgreSQL** - Powerful, open-source.
- **Microsoft SQL Server** - Microsoft's database.
- **Oracle Database** - Enterprise grade.
- **SQLite** - lightweight, often used in apps.

## What is SQL injection?
**SQL (Structured Query Language)** is the language used to talk to databases. Examples:

```bash
SELECT * FROM users WHERE username = 'john';
```

**SQL Injection** is a hacking technique where an attacker inserts malicious SQL code into a normal query, tricking the database into executing unintended commands. Lets take a look at how it works. Imagine a login form on a website. The backend code might look like this:
```bash
query = "SELECT * FROM users WHERE username = '" + user_input + "' AND password = '" + password_input + "'"
```
If we enter:
- **Username**: `admin' OR '1'='1`
- **Password**: anything

The query becomes:
```bash
SELECT * FROM users WHERE username = 'admin' OR '1'='1' AND password = 'anything'
```

Since '1'='1' is always true, the database returns the admin user — you're logged in without a password. Now lets take a look at different types of SQL injection.

<table>
  <tr>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>In-band (Classic) SQLi</td>
    <td>Attacker uses the same channel to send the payload and get results. Includes Error-based and Union-based</td>
  </tr>
  <tr>
    <td>Bind SQLi</td>
    <td>No direct output. Attacker infers results based on behavior (true/false responses or time delays)</td>
  </tr>
  <tr>
    <td>Out-of-band SQLi</td>
    <td>Data is sent to a different server/channel (less common)</td>
  </tr>
</table>

## Introduction to SQLMap
**SQLMap** is an open source automated tool that detects and exploits SQL injection vulnerabilities. It does the heavy lifting for you so that we dont need to manually craft every payload. We use SQLMap because:
- Automatically finds SQLi vulnerabilities
- Supports many database types (MySQL, PostgreSQL, Oracle, etc.)
- Can extract database names, tables, columns, and even dump full data
- Works on Linux, Windows, and macOS
