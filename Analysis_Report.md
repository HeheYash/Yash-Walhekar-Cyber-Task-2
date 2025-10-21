#  Analysis Report

An analysis of a sample phishing email was outlined in this report, following the 8 steps that were presented in the task description.

### 1. Obtain a sample phishing email
The analysis of this analysis received a safe sample email (`sample-1244.eml`)

### 2. Examine sender's email address for spoofing
Clear sender spoofing was detected.
* **Apparent Sender (in Body):** `De: *****Swagbucks*****` (From: \*\*\*\*\*Swagbucks\*\*\*\*\*)
* **Actual Sender (in Header):** `From: phishing@pot <phishing@pot>`

This is also a typical example of Display Name Spoofing. The email attacker is using the email client, which only displays the preferred name to fool the user, that it is an authentic brand.

### 3. Check email headers for discrepancies
Email headers were studied on the messageheader of the Google Admin Toolbox and also on the raw file.

* **Google Toolbox Result:**
    * `SPF: pass`
    * `DKIM: pass`
    * `DMARC: pass`

* **Analysis:** This is a **deceptive finding** and a major discrepancy. These checks worked since the email was dispatched using a technically valid public email account (e.g. Hotmail, which appeared in the hops of the server). These tests validate the **attacker's** sending domain, **not** the `Swagbucks.com` domain they are impersonating.

* **Raw Header Discrepancy:**  The line `X-MS-Exchange-Organization-SCL: 5` which was found to be insufficient on a manual examination of the raw header. It is the Spam Confidence Level of Microsoft, and the number 5 website clearly indicates the email as spam.

### 4. Identify suspicious links or attachments
There were no malevolent attaching. Nonetheless, some very suspicious attachment was discovered at the end of the mail.

### 5. Look for urgent or threatening language
The email is **not** applied in a **threatening tone**. It instead employs **lure-based social engineering** to create a sense of urgency and opportunity.
* **Examples:** "6 best ways to easily make money and earn SBs fast".
* **Tactic:** This is aimed at reminding the user that he or she wants to make a lot of money effortlessly, hence will request one to click without considering thinking.

### 6. Note any mismatched URLs
A clear URL mismatch was found on the suspicious link.
* **Displayed Link Text:** `Unsubscribe Here`
* **Actual Link (on hover):** `https://bit.ly/3OKKeaI`

A genuine company does not go through a public `bit.ly` shortener as an unsubscribe link. This is a popular obfuscator (user) attacker method of hiding (covering) the actual, malicious destination of the link.

### 7. Verify presence of spelling or grammar errors
The email content showed signs of low-quality automation, including a repeated sentence:
> "Signing up for various services is second only to money producers in terms of how quickly one may earn SBs."

This sentence is used twice, consecutively, which is a pointer to a copy-pasted email template that is sloppy.

### 8. Summarize phishing traits found in the email
This is an email phishing/spam which utilizes a number of tricks to make it warm and fuzzy:

1.  **Social Engineering:** It uses **Display Name Spoofing** (`*****Swagbucks*****`) and **lure-based content** ("easy money") to build false trust.
2.  **Technical Deception:** It will get around simple security filters by being submitted to a legitimate public-facing email, and it will fail to trigger `SPF/DKIM/DMARC: pass` results.
3.  **Link Obfuscation:** It conceals its malicious code with a shortener of URL `bit.ly`, with the help of a harmless Unsubscribe link.


The email finally (and appropriately) was identified as a spam mail by mail servers (SCL: 5), but it is dependent on convincing a human user who may trust the spoofed pass on authentication or the spoofed receiver name.
