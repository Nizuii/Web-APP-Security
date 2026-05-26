# Passive Scan & Spider — DVWA on localhost

**Tool**: OWASP ZAP  
**Scan Policy**: Dev Standard  
**Ajax Spider**: Firefox  
**Target**: http://localhost/  
**Spider**: Traditional + Ajax  
**Browser**: Firefox  
**Total Alerts**: 14  
**Tester**: nizuii@zoyx  
**Date**: 2026-04-26  

---

<img width="1929" height="1080" alt="2026-05-26-152059_hyprshot" src="https://github.com/user-attachments/assets/1b7f5405-8df8-4221-a647-255ff863a2ff" />

## Summary

- **Total Alerts**: 14
- **High Alerts**: 2
- **Medium Alerts**: 5
- **Low Alerts**: 4
- **Info Alerts**: 3

### Critical Findings at a Glance:

<table>
  <tr>
    <th>Alert</th>
    <th>Risk</th>
    <th>Count</th>
    <th>What it means</th>
  </tr>
  <tr>
    <td>Path Traversal</td>
    <td>High</td>
    <td>-</td>
    <td>Attacker may read files outside web root (e.g. /etc/passwd)</td>
  </tr>
  <tr>
    <td>SQL Injection</td>
    <td>High</td>
    <td>3</td>
    <td>Database queries can be manipulated — data theft, auth bypass</td>
  </tr>
  <tr>
    <td>CSP Header Not Set</td>
    <td>Medium</td>
    <td>Systemic</td>
    <td>No Content Security Policy — XSS attacks have no browser-level defense</td>
  </tr>
  <tr>
    <td>Missing Anti-Clickjacking</td>
    <td>Medium</td>
    <td>Systemic</td>
    <td>Site can be embedded in iframes — clickjacking attacks possible</td>
  </tr>
  <tr>
    <td>XSLT Injection</td>
    <td>Medium</td>
    <td>2</td>
    <td>XML/XSLT input not sanitized — potential code execution</td>
  </tr>
  <tr>
    <td>Cookie No HttpOnly Flag</td>
    <td>Medium</td>
    <td>Systemic</td>
    <td>Session cookies readable by JavaScript — XSS can steal sessions</td>
  </tr>
  <tr>
    <td>Cookie No SameSite</td>
    <td>Medium</td>
    <td>Systemic</td>
    <td>CSRF attacks possible — cookies sent cross-site</td>
  </tr>
  <tr>
    <td>In Page Banner Info Leak</td>
    <td>Low</td>
    <td>2</td>
    <td>App/server version visible in page content</td>
  </tr>
  <tr>
    <td>Debug Error Messages</td>
    <td>LOW</td>
    <td>2</td>
    <td>Stack traces or PHP errors exposed to users</td>
  </tr>
  <tr>
    <td>Server Version via Header</td>
    <td>LOW</td>
    <td>-</td>
    <td>Apache/PHP version in HTTP response headers</td>
  </tr>
  <tr>
    <td>X-Content-Type Missing</td>
    <td>LOW</td>
    <td>Systemic</td>
    <td>MIME-type sniffing possible — browser may misinterpret files</td>
  </tr>
  <tr>
    <td>Auth Request Identified</td>
    <td>INFO</td>
    <td>-</td>
    <td>ZAP found the login form — can be used for auth testing</td>
  </tr>
  <tr>
    <td>Suspicious Comments</td>
    <td>Info</td>
    <td>-</td>
    <td>Developer comments in HTML/JS may leak info</td>
  </tr>
  <tr>
    <td>Session Mgmt Identified</td>
    <td>Info</td>
    <td>6</td>
    <td>ZAP identified session handling points — useful for session attacks</td>
  </tr>
</table>
