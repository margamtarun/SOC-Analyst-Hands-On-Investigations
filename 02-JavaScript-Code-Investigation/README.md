# Case #2 – JavaScript Code Investigation

## Alert Information

| Field | Details |
|---|---|
| Alert | SOC166 – Javascript Code Detected in Requested URL |
| Event ID | 116 |
| Severity | Medium |
| Alert Type | Web Attack |
| Result | True Positive |
| Attack Type | Reflected XSS |
| Source IP | 112.85.42.13 |
| Destination IP | 172.16.17.17 |
| Hostname | WebServer1002 |
| HTTP Method | GET |
| MITRE ATT&CK | T1190 – Exploit Public-Facing Application |

---

## Investigation Summary

Investigated a JavaScript/XSS attack attempt against the web server
`172.16.17.17`.

The investigation identified multiple XSS payloads originating from
`112.85.42.13`. The payloads were delivered through the `q` parameter
of HTTP GET requests, indicating a reflected XSS attack.

The requests received HTTP 302 redirects, and the investigation determined
that the attack was unsuccessful.

---

## Investigation Findings

### 1. Initial Alert

The alert identified JavaScript code in a requested URL targeting the
web server `172.16.17.17`.

### 2. Malicious XSS Payload

The requested URL contained JavaScript/XSS code within the `q` parameter.

Example payloads observed during the investigation included:

- `prompt(8)`
- `<img src=q onerror=prompt(8)>`
- `<svg><script>...`
- Other JavaScript payload variations

### 3. Source IP Investigation

Filtering the logs by source IP `112.85.42.13` revealed multiple requests
containing different XSS payloads targeting the same web server.

This confirmed that the activity was not an isolated request.

### 4. Attack Result

The HTTP requests received a `302` response.

Based on the available log evidence and the completed LetsDefend investigation,
the XSS attack attempt was determined to be unsuccessful.

---

## Evidence

### Alert Overview

![Alert Overview](evidence/01-alert-overview.png)

### XSS Payload

![XSS Payload](evidence/02-xss-request.png)

### Multiple XSS Attempts

![Multiple XSS Payloads](evidence/03-multiple-xss-payloads.png)

### HTTP 302 Response

![HTTP 302 Response](evidence/04-http-302-response.png)

---

## Investigation Outcome

**Verdict: True Positive – Unsuccessful Reflected XSS Attack Attempt**

The investigation identified multiple malicious XSS payloads originating
from `112.85.42.13` and targeting `172.16.17.17`.

The activity was confirmed as a reflected XSS attack attempt. The requests
were redirected with HTTP 302 responses, and the attack was determined to
be unsuccessful.

**LetsDefend Playbook Score: 100%**

---

## Skills Demonstrated

- SOC Alert Investigation
- Web Attack Analysis
- XSS Detection
- Reflected XSS Identification
- Log Analysis
- Source IP Investigation
- HTTP Request Analysis
- HTTP Response Analysis
- MITRE ATT&CK Mapping
- Security Alert Triage
