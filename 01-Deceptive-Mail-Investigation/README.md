
# SOC282 – Deceptive Mail Investigation

## Alert Overview

**Alert:** SOC282 - Phishing Alert - Deceptive Mail Detected

**Event ID:** 257

**Severity:** Medium

**Category:** Exchange / Phishing

**Result:** True Positive

**Event Time:** 2024-05-13 09:22:00 +03:00

**Role:** Security Analyst

---

## Investigation Objective

Investigate a suspected phishing email, determine whether the email
contained malicious content, identify whether the recipient interacted
with the malicious content, and determine the appropriate containment
actions.

---

## Initial Alert Analysis

The alert identified an email with the subject:

**"Free Coffee Voucher"**

The email was sent from:

**free@coffeeshoop.com**

and was delivered to:

**Felix@letsdefend.io**

The email was allowed and delivered to the recipient's mailbox.

---

## Email Analysis

The email contained a suspicious URL embedded within the message.

The URL referenced a ZIP file:

`Free_coffee.zip`

The URL was:

`https://files-ld3.s3.us-east-2.amazonaws.com/free-coffee.zip`

The presence of a downloadable ZIP file within a deceptive promotional
email was treated as a suspicious indicator and required further analysis.

---

## URL / File Analysis

The URL and associated file were analyzed using security analysis
platforms.

The analysis determined that the referenced file was malicious.

This confirmed that the email was not simply suspicious or unsolicited;
it contained malicious content.

---

## User Interaction Analysis

Log and process activity showed that the recipient's host accessed the
malicious URL, downloaded the malware, and executed it.

This established that the phishing attempt resulted in user interaction
with the malicious content.

---

## Investigation Timeline

| Stage | Observation |
|---|---|
| 1 | Phishing email was received |
| 2 | Email was delivered to the recipient |
| 3 | Email contained a suspicious URL |
| 4 | URL pointed to a ZIP file |
| 5 | URL/file analysis identified malicious content |
| 6 | Recipient's host accessed the malicious URL |
| 7 | Malware was downloaded and executed |
| 8 | Device was contained |
| 9 | Malicious email was deleted |

---

## Indicators of Interest

| Indicator | Value |
|---|---|
| Sender | free@coffeeshoop.com |
| Recipient | Felix@letsdefend.io |
| Subject | Free Coffee Voucher |
| SMTP Address | 103.80.134.63 |
| Malicious File | Free_coffee.zip |
| Destination | files-ld3.s3.us-east-2.amazonaws.com |

---

## MITRE ATT&CK

The alert was associated with the following MITRE ATT&CK techniques:

- **T1566** – Phishing
- **T1566.002** – Phishing: Spearphishing Link
- **T1059** – Command and Scripting Interpreter
- **T1204** – User Execution

---

## Response and Containment

The investigation confirmed the alert as a true positive.

The following response actions were identified:

1. Confirmed the malicious email.
2. Confirmed the malicious URL/file.
3. Confirmed user interaction with the malicious content.
4. Confirmed malware download and execution.
5. Contained the affected device.
6. Deleted the malicious email from the recipient's mailbox.

---

## Conclusion

The investigation confirmed a phishing email containing a malicious URL
and file.

The email was successfully delivered to the recipient, and subsequent
log and process activity showed that the malicious content was accessed,
downloaded, and executed.

The incident was therefore classified as a **True Positive**, and
containment and email removal actions were performed.

---

## Skills Demonstrated

- Phishing Email Analysis
- Security Alert Triage
- Email Security Investigation
- URL Analysis
- Malware Analysis
- IOC Identification
- Log Analysis
- Process Activity Analysis
- Incident Response
- MITRE ATT&CK Mapping
- Endpoint Containment
