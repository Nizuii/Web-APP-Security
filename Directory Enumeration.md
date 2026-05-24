# What is Directory Enumeration?

When we visit a website, we see pages like `example.com/home` or `example.com/about` But websites often have hidden directories and files that aren't linked anywhere - things like admin panels, backup files, test pages, or configuration files. Directory enumeration is the process of systematically guessing and checking for these hidden paths to discover what exists on a web server. Think of it like checking every door in a building to see which ones areunlocked, even if there is no sign pointing to them. Attackers and security testers use this to find:
- Admin panels (`/admin`, `/wp-admin`, `/dashboard`).
- Backup files (`/backup`, `/site.tar.gz`).
- Configuration files (`/config.php`, `/.env`).
- API endpoints (`/api/v1/users`)
- Test/debug pages (`/test.php`, `/debug`)
Finding these can reveal vulnerabilities or sensitive information. Now lets break down the tools used one by one:

## 1. DIRB

**Dirb** is a classic command-line tool that brute-forces directories using a wordlist. It works when we give a URL and a list of common directory names. It tries each one and tells you which ones exist. Example it tries: `example.com/admin`, `example.com/login`, `example.com/backup` etc... and reports back which returned a valid page.

<img width="1925" height="1080" alt="image" src="https://github.com/user-attachments/assets/018abd29-6b04-4dba-87cc-0707b2d2c17c" />

## 2. DirBuster

**DirBuster** is similar to DIRB but with a graphical user interface (GUI). It is easier for beginners to use. It also uses wordlist but lets us see results visually. It can be slower but it is more user-friendly.
