# Yash-Walhekar-Cyber-Task-2

# Cyber Security Internship: Task 2 - Phishing Analysis Report

This repository contains the submission for Task 2 of the cybersecurity internship, focusing on the analysis of a phishing email sample.

## Objective
The goal of this task was to obtain a sample phishing email, analyze its headers and content to identify phishing characteristics, and produce a detailed report on the findings.

## Analysis Summary
The provided email sample (`sample-1244 (1).eml`) was identified as a deceptive spam/phishing email. While it cleverly passed all technical authentication checks (`SPF`, `DKIM`, `DMARC`), its true malicious intent was hidden in classic social engineering tactics.

### Key Phishing Traits Identified:
* **Display Name Spoofing:** The sender's name was forged to appear as `*****Swagbucks*****`, while the actual sender address was `phishing@pot`.
* **Link Obfuscation:** A suspicious `bit.ly` URL shortener was hidden behind "Unsubscribe Here" text, a common tactic to redirect users to malicious sites.
* **Deceptive Authentication:** The email "passed" `SPF/DKIM/DMARC` checks. However, these checks only validated the attacker's public email account (e.g., `hotmail.com`), not the Swagbucks brand they were impersonating.
* **Social Engineering:** The email used "easy money" lures ("earn SBs fast") to create a sense of opportunity and rush the user into clicking.

## Repository Contents
* `README.md`: This file, providing an overview of the project.
* `ANALYSIS_REPORT.md`: The detailed report outlining the step-by-step analysis.
* `sample-1244 (1).eml`: The raw `.eml` file used as evidence for the analysis.
* `/screenshots`: A folder containing visual evidence, including header analysis results and email body screenshots.

## Tools Used
* **Google Admin Toolbox (Messageheader):** To analyze the email headers in a human-readable format.
* **Text Editor:** To inspect the raw `.eml` file content.
