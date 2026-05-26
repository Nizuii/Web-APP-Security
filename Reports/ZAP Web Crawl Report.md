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
</table>
