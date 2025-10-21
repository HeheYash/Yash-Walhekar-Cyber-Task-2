# Yash-Walhekar-Cyber-Task-2

# Cyber Security Internship: Task 2 - Phishing Analysis Report

This repository contains the full analysis and report for Task 2 of the Elevate Labs Cyber Security Internship.

## Objective
The task was to obtain a sample phishing email, analyze its headers and content to identify phishing characteristics, and produce a report on the findings.

## Key Findings Summary
The email sample was definitively identified as a phishing/spam attempt. While it cleverly passed technical authentication checks (`SPF`, `DKIM`), it relied heavily on **social engineering** and **deceptive content** to lure a victim.

**Key phishing traits identified:**
* **Display Name Spoofing:** Impersonated the "Swagbucks" brand in the "From" field.
* **Link Obfuscation:** Hid a suspicious `bit.ly` URL shortener behind "Unsubscribe Here" text.
* **Social Engineering:** Used "easy money" lures to encourage clicks.

## Deliverables
* **[Full Analysis Report (ANALYSIS_REPORT.md)](./ANALYSIS_REPORT.md)**: A detailed, step-by-step report following the task guidelines.
* **[Evidence File (sample-1244 (1).eml)](./sample-1244%20(1).eml)**: The raw `.eml` file used for the analysis.
* **[Screenshots Folder](./screenshots/)**: A directory containing visual evidence from the analysis.
