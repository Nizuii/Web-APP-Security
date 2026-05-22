# What is OSINT?
**OSINT** or **Open Source Intelligence** is gathering information from publicly available sources to learn about a target (person, organization, system or event). **Open Source** means the information is already public. We are not breaking into systems or bypassing passwords. We are just really good at finding and connecting publicly visible dots. Think of it like a detective who:
- Reads, newspaper. social media and public records.
- Looks at satellite images anyone can access.
- Checks public business registrations.
- Analyzes photos for hidden clures (metadata, landmarks).

All of this is legal and ethical when done properly.

## Why do people use OSINT?

<table>
  <tr>
    <th>Role</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td>Cybersecurity Defenders</td>
    <td>Find out what attackers can discover about their own company</td>
  </tr>
  <tr>
    <td>Penetration Testers</td>
    <td>Map the "attack surface" before testing</td>
  </tr>
  <tr>
    <td>Journalists</td>
    <td>Investigate people, companies, or events</td>
  </tr>
  <tr>
    <td>Law Enforcement</td>
    <td>Gather intelligence on suspects (legally)</td>
  </tr>
  <tr>
    <td>Threat Intelligence Analysts</td>
    <td>Track hacker groups, malware campaigns, or emerging threats</td>
  </tr>
</table>

```bash
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  1. DEFINE      │────▶│  2. GATHER      │────▶│  3. ANALYZE     │
│  What/Who are   │     │  Collect raw    │     │  Connect dots,  │
│  you looking    │     │  data from      │     │  verify, and    │
│  for?           │     │  sources        │     │  find patterns  │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                                                        │
┌─────────────────┐     ┌─────────────────┐             │
│  5. REPORT      │◄────│  4. PIVOT       │◄─────────── ┘
│  Present your   │     │  Use new info   │
│  findings       │     │  to find more   │
└─────────────────┘     └─────────────────┘
```
## Specific Tools We Need to Know

### 1. Google Dorking.
Google Dorks are advanced search operators that let you find very specific things that regular searches miss. It's not "hacking google" - it's using google's own advanced features to find information that happens to be publicly accessible. Example: Instead of typing: `company confidential documents` we search: `site:github.com filetype:pdf "confidential"`. This tells Google: "Only search within company.com, only returns PDF files, and inly if they contain the word 'confidential'."  

Common Operators are:

<table>
  <tr>
    <th>Operator</th>
    <th>What it does</th>
    <th>Example</th>
  </tr>
  <tr>
    <td>site:</td>
    <td>Search only within a specific website.</td>
    <td>site:github.com "password"</td>
  </tr>
  <tr>
    <td>filetype:</td>
    <td>Search for only specific file types.</td>
    <td>filetype:pdf "internal use only"</td>
  </tr>
  <tr>
    <td>intitle:</td>
    <td>Search in the page title only</td>
    <td>intitle:"index of" "passwords"</td>
  </tr>
</table>

<img width="1865" height="968" alt="image" src="https://github.com/user-attachments/assets/90980644-bd90-4865-85f3-48131dc83c4a" />

### 2. Shodan
Shodan is a search engine. but instead of searching for websites, it searches for internet connected devices.
