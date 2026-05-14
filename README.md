# phishing_kit_analysis

## Overview

This repository documents my analysis of a cryptocurrency phishing kit from a cybersecurity lab. The kit was designed to impersonate a crypto wallet connection page and collect wallet recovery seed phrases from victims.

The investigation focused on reviewing the phishing kit files, identifying how the kit worked, locating where collected data was stored, and determining how stolen information was exfiltrated.

All sensitive values, including seed phrases, Telegram bot tokens, chat IDs, and actor identifiers, have been redacted from the screenshots and report.

---

## Skills Practiced

- Static analysis of suspicious files
- Phishing kit investigation
- PHP source code review
- Log file analysis
- Evidence collection
- Identifying credential exfiltration methods
- Extracting indicators of compromise
- Writing a security investigation report

---

## Repository Structure

```text
phishing-kit-analysis/
│
├── README.md
│
└── screenshots/
    ├── walletdirectory.png
    ├── metamaskphp.png
    ├── phpcontents.png
    └── logtxt.png
