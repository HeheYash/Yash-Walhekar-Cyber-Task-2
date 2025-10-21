# Phishing Analysis Report

This report details the analysis of a sample phishing email as required by the internship task. The analysis follows the 8-step guide provided.

### 1. Obtain a sample phishing email
A safe phishing/spam sample in `.eml` format was obtained for analysis.
* **File:** `sample-1244 (1).eml`

### 2. Examine sender's email address for spoofing
Clear spoofing was identified.
* **Apparent Sender (in Body):** `*****Swagbucks*****`
* **Actual Sender (in Header):** `phishing@pot <phishing@pot>`

This is **Display Name Spoofing**, a social engineering tactic to make the email appear to be from a trusted brand.

### 3. Check email headers for discrepancies
The headers were analyzed using the **Google Admin Toolbox - Messageheader**.

![Google Toolbox Analysis](screenshots/1_google_toolbox.png)

At first glance, the headers appear legitimate:
* **SPF:** `pass`
* **DKIM:** `pass`
* **DMARC:** `pass`

However, this is a **deceptive finding**. These checks are passing for the *sender's actual domain* (a public email provider like `hotmail.com`), not the `swagbucks.com` domain. The attacker is using a legitimate, high-reputation email service to bypass simple filters, which is a key discrepancy.

A manual check of the raw header also revealed a high **Spam Confidence Level (SCL)** set by Microsoft's servers (`X-MS-Exchange-Organization-SCL: 5`), which flags the email as "Spam".

### 4. Identify suspicious links or attachments
* **Attachments:** No malicious attachments were found.
* **Suspicious Links:** A highly suspicious "Unsubscribe" link was identified at the bottom of the email.

### 5. Look for urgent or threatening language
The email does not use traditional "threatening" language (e.g., "your account will be suspended"). Instead, it uses a **lure-based social engineering** tactic, creating a sense of urgency to get "easy money."
* **Examples:** "The 6 Best Ways To Easily Make Money" and "earn SBs fast".

### 6. Note any mismatched URLs
A URL mismatch was confirmed on the suspicious link.
* **Displayed Link Text:** `Unsubscribe Here`
* **Actual URL (on hover):** `https://bit.ly/3OKKeaI`

![Link Hover Analysis](screenshots/3_link_hover.png)

This is a major red flag. Legitimate companies do not use public `bit.ly` shorteners for their official unsubscribe links. This link is obfuscated to hide its true, malicious destination.

### 7. Verify presence of spelling or grammar errors
The email body contains indicators of low-quality, automated content, such as a duplicated sentence:
* *"Signing up for various services is second only to money producers in terms of how quickly one may earn SBs."* (This sentence appears twice, nearly back-to-back).

![Email Body](screenshots/2_email_body.png)

### 8. Summarize phishing traits found in the email
This email is a clear phishing/spam attempt that combines multiple tactics:
1.  **Brand Impersonation:** Uses "Swagbucks" in the display name to gain false trust.
2.  **Authentication Bypass:** Sent from a legitimate public mail provider to pass `SPF/DKIM/DMARC` checks.
3.  **Link Obfuscation:** Hides a malicious destination behind a `bit.ly` shortener.
4.  **Social Engineering:** Uses "easy money" lures to encourage the user to click.
