# What is Web Crawling?

Imagine internet as a giant library with billions of books (websites). Wb crawling is like sending a robot to browse through these books, read their pages, and collect information automatically. Lets think og a somple analogy:
- **We**: Person reading one book at a time.
- **Web Crawler**: Robot that can read thousands of these books per seconds and copy down important notes.
Now lets take a look at why security professionals use web crawling?

<table>
  <tr>
    <th>Purpose</th>
    <th>What it means</th>
  </tr>
  <tr>
    <td>Dicover hidden pages</td>
    <td>Find admin panels, login pages, or backup files that shouldn't be public</td>
  </tr>
  <tr>
    <td>Map the website</td>
    <td>See all pages, links, and how they're connected</td>
  </tr>
  <tr>
    <td>Find vulnerabilities</td>
    <td>Identify outdated software, exposed databases, or weak configurations</td>
  </tr>
  <tr>
    <td>Gather intelligence</td>
    <td>Collect email addresses, usernames, or technology used by a site</td>
  </tr>
</table>

Now lets take a look at the major 3 tools used for web crawling:

## 1. ZAP (OWASP Zed Attack Proxy)
It is a free security tool maintained by OWASP (a non profit security organization). It crawls websites and tests them for security vulnerabilities automatically. It is best for beginners who want to learn both crawling and basic security testing. It is completly free and has key features like automatic spider (crawler) that clicks every link it finds, finds forms, login pages, and hidden directories, shows us a "site map" of the entire website structure, and can run active security scans after crawling.

<img width="1922" height="1080" alt="image" src="https://github.com/user-attachments/assets/15aa6e6f-fe06-4c68-ab96-b09b6eecb50e" />


