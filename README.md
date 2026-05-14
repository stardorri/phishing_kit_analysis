# phishing_kit_analysis

## Overview

This project documents my analysis of a cryptocurrency phishing kit from a cybersecurity lab. The kit targeted MetaMask users and attempted to collect wallet recovery seed phrases through a fake wallet connection page.

The investigation focused on identifying how the kit worked, where collected data was stored, what services were used, and how stolen information was exfiltrated.

## Full Report

Read the full investigation report here:
[View Report](report.md)

## Key Findings

- The phishing kit targeted MetaMask users.
- The main phishing logic was contained in `metamask.php`.
- The kit was written in PHP.
- Victim IP and geolocation data were collected using Sypex Geo.
- Captured seed phrases were stored locally in `log.txt`.
- Stolen data was exfiltrated through Telegram.
- Three collected seed phrase entries were identified.
- Sensitive values were redacted before publication.

## Skills Demonstrated

- Static analysis
- Phishing kit investigation
- PHP source code review
- Log file analysis
- Evidence collection
- Indicator identification
- Security report writing

## Repository Contents

```text
phishing-kit-analysis/
│
├── README.md
├── report.md
└── screenshots/
    ├── walletdirectory.png
    ├── metamaskphp.png
    ├── phpcontents.png
    └── logtxt.png
