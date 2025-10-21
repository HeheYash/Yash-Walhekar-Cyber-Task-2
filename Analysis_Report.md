#  Analysis Report

This report details the findings from analyzing a sample phishing email, following the 8 steps provided in the task description.

### 1. Obtain a sample phishing email
A safe sample email (`sample-1244 (1).eml`) was obtained for this analysis.

### 2. Examine sender's email address for spoofing
Clear sender spoofing was identified.
* **Apparent Sender (in Body):** `De: *****Swagbucks*****` (From: \*\*\*\*\*Swagbucks\*\*\*\*\*)
* **Actual Sender (in Header):** `From: phishing@pot <phishing@pot>`

This is a classic case of **Display Name Spoofing**. The attacker is relying on the email client to only show the "friendly" name, tricking the user into believing it's from the legitimate brand.

### 3. Check email headers for discrepancies
The email headers were analyzed using the **Google Admin Toolbox (Messageheader)** and by inspecting the raw file.

* **Google Toolbox Result:**
    * `SPF: pass`
    * `DKIM: pass`
    * `DMARC: pass`

* **Analysis:** This is a **deceptive finding** and a key discrepancy. These checks passed because the email was sent from a *technically valid* public email account (e.g., Hotmail, as seen in the server hops). These checks validate the *attacker's* sending domain, **not** the `Swagbucks.com` domain they are impersonating.

* **Raw Header Discrepancy:** A manual inspection of the raw header revealed the line: `X-MS-Exchange-Organization-SCL: 5`. This is Microsoft's Spam Confidence Level, where "5" explicitly flags the email as "Spam".

### 4. Identify suspicious links or attachments
No malicious attachments were present. However, a highly suspicious link was identified at the bottom of the email.

### 5. Look for urgent or threatening language
The email does not use "threatening" language. Instead, it uses **lure-based social engineering** to create a sense of urgency and opportunity.
* **Examples:** "The 6 Best Ways To Easily Make Money" and "earn SBs fast".
* **Tactic:** This is designed to lower the user's guard by appealing to a desire for easy money, prompting them to click without thinking.

### 6. Note any mismatched URLs
A clear URL mismatch was found on the suspicious link.
* **Displayed Link Text:** `Unsubscribe Here`
* **Actual Link (on hover):** `https://bit.ly/3OKKeaI`

Legitimate companies *never* use a public `bit.ly` shortener for their unsubscribe link. This is a common attacker technique to **obfuscate** (hide) the true, malicious destination of the link.

### 7. Verify presence of spelling or grammar errors
The email content showed signs of low-quality automation, including a repeated sentence:
> "Signing up for various services is second only to money producers in terms of how quickly one may earn SBs."

This sentence appears twice, one after the other, indicating a sloppy, copy-pasted email template.

### 8. Summarize phishing traits found in the email
This email is a phishing/spam attempt that combines several tactics to appear legitimate:

1.  **Social Engineering:** It uses **Display Name Spoofing** (`*****Swagbucks*****`) and **lure-based content** ("easy money") to build false trust.
2.  **Technical Deception:** It bypasses basic security filters by being sent from a valid public email account, resulting in misleading `SPF/DKIM/DMARC: pass` results.
3.  **Link Obfuscation:** It hides its malicious payload behind a `bit.ly` URL shortener, disguised as a harmless "Unsubscribe" link.

The email was ultimately (and correctly) flagged as spam by mail servers (SCL: 5), but it relies on fooling a human user who might trust the deceptive "pass" on authentication or the spoofed sender name.
