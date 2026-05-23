# What is Directory Enumeration?

When we visit a website, we see pages like `example.com/home` or `example.com/about` But websites often have hidden directories and files that aren't linked anywhere - things like admin panels, backup files, test pages, or configuration files. Directory enumeration is the process of systematically guessing and checking for these hidden paths to discover what exists on a web server. Think of it like checking every door in a building to see which ones areunlocked, even if there is no sign pointing to them. Attackers and security testers use this to find:
- Admin panels (`/admin`, `/wp-admin`, `/dashboard`).
- Backup files (`/backup`, `/site.tar.gz`).
- Configuration files (`/config.php`, `/.env`).
- API endpoints (`/api/v1/users`)
- Test/debug pages (`/test.php`, `/debug`)
Finding these can reveal vulnerabilities or sensitive information. Now lets break down the tools used one by one:

## 1. DIRB

**Dirb**
