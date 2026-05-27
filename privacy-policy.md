---
layout: legal
title: Privacy Policy
---

# Privacy Policy

**Effective Date:** 2026-04-27
**Last Updated:** 2026-05-16

This Privacy Policy explains how **Nemerai, LLC** ("Verascribe," "we," "us") handles information when you use **Verascribe Guardian** (the "Service"), a Google Apps Script web app — used alongside one or more Google Sheets workbooks you create through the app — that helps co-parents and guardians track custody schedules, communications, expenses, and related events.

We have written this policy to be specific and verifiable. Where Google's OAuth consent screen displays a permission, this document explains exactly what we do — and do not do — with the data that permission unlocks.

---

## Google API Limited Use Compliance

**Verascribe Guardian's use of information received from Google APIs adheres to the [Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy), including the Limited Use requirements.**

In particular:
- We use your Google Workspace data **only to provide and improve user-facing features** of the Service that are visible and prominent in the user interface.
- We do **not** transfer Google Workspace data to others except as necessary to provide the Service, comply with applicable law, or as part of a merger or acquisition where you are notified in advance.
- We do **not** use Google Workspace data for **serving advertisements**.
- We do **not** allow humans to read your Google Workspace data unless (a) we have obtained your affirmative consent for specific messages, (b) it is necessary for security purposes such as investigating abuse, (c) it is necessary to comply with applicable law, or (d) it is for internal operations and the data has been aggregated and anonymized.
- We do **not** use Google Workspace data to develop, improve, or train **generalized AI/ML models** of any kind.

---

## 1. The short version

- Verascribe Guardian is an **offline-first** web app. The data you enter is stored locally in your browser (IndexedDB) and in **your own** Google Sheets workbooks and Google Drive folders.
- We **do not** operate a cloud database that holds your custody, financial, or evidence records. There is no Verascribe-hosted copy of your data.
- We **do not** use Google Analytics, advertising trackers, Sentry, or any third-party telemetry.
- The only information transmitted to a Verascribe-controlled server is your **email address** and a **workbook identifier**, and only for the purpose of validating your license or trial. See Section 5.
- The Service handles information **about** minor children (names, birthdates, custody schedules) entered by the adult user. The Service is not directed to children and does not collect information **from** children. See Section 9.

---

## 2. Who this policy applies to

This policy applies to:
- Users who install Verascribe Guardian from the Google Workspace Marketplace (or, while Marketplace publication is pending, open it via the web-app URL).
- Visitors to **myverascribe.com**.

It does **not** govern your use of Google Sheets, Google Drive, or any Google product itself — those are governed by [Google's Privacy Policy](https://policies.google.com/privacy).

---

## 3. Information we access via Google OAuth

When you first open Verascribe Guardian, Google's OAuth consent screen will ask you to authorize the following scopes. This section explains, scope by scope, exactly what each one does and why we need it.

### 3.1 `https://www.googleapis.com/auth/userinfo.email`

**What it lets us see:** The email address associated with your Google Account.

**Why we need it:** To register your free trial, validate your paid license against our license registry, route support emails sent through the in-app "Contact Us" feature, and identify you for future license-key recovery.

**Where it goes:** Stored in the Google Apps Script Document Properties of the workbook you selected, and transmitted to **`_registry.myverascribe.com`** for license validation.

### 3.2 `https://www.googleapis.com/auth/drive.file`

**What it lets us see:** Only the files that Verascribe Guardian itself creates in your Drive. We cannot see any of your other Drive files.

**Why we need it:** Two purposes:

1. **Workbook creation** — The app creates Google Sheets workbooks for your custody records. You can create more than one workbook and switch between them inside the app (for example, one per child or one per case). The `drive.file` scope lets the app create, read, write, and delete only the workbooks it creates — never any other file in your Drive.
2. **Evidence and exports** — Saves evidence attachments you upload, generated PDF/CSV reports, and JSON backups to Verascribe-managed folders in your own Drive.

**Where it goes:** Stays inside your own Google Drive. The app uses folders named `Verascribe Evidence — {Your Workbook Name}` and `Verascribe — Archived Evidence (Standalone)` for evidence and backups.

### 3.3 `https://www.googleapis.com/auth/script.send_mail`

**What it lets us see:** Nothing. This scope only allows the app to send mail **from your account**.

**Why we need it:** Used only when you submit a "Contact Us" support request from inside the app. The message is sent from your own Gmail to a fixed Verascribe support address — you cannot choose another recipient.

**Where it goes:** Mail is sent from your own Gmail account using Google's `MailApp` service. We do not read your inbox, drafts, or any other mail. The send is initiated only by your explicit action inside the app.

### 3.4 `https://www.googleapis.com/auth/script.external_request`

**What it lets us see:** Nothing. This scope allows the app's server-side code to make outbound HTTPS calls. The set of permitted destinations is fixed by the app's manifest:

- **`sheets.googleapis.com` and `www.googleapis.com`** — Google's Sheets API and Drive API. The app calls these to read and write your workbook content (Sheets API) and to create, read, and delete the workbooks, evidence files, reports, and backups it manages on your behalf (Drive API). These are Google's own services and are governed by [Google's Privacy Policy](https://policies.google.com/privacy).
- **`script.google.com`** — the host that runs our license-validation endpoint. The `_registry.myverascribe.com` hostname is a CNAME (a DNS alias) for a Google Apps Script web app we own that lives at `script.google.com`. Calls receive your email, workbook identifier, license token, and cryptographic signature for license validation. See Section 5.
- **`raw.githubusercontent.com`** — a public GitHub URL used as a fallback for the license-registry configuration only when the primary registry is unreachable. This call does **not** transmit any of your data.
- **`dns.google` and `cloudflare-dns.com`** — DNS-over-HTTPS lookups used to verify that the registry domain has not been hijacked by a hostile network. These calls transmit only the domain name being looked up — never any of your data.

---

## 4. Information you create using the Service

When you use Verascribe Guardian, you generate records about your family and custody situation. These typically include:

- **Children's information** — names, optional birthdates.
- **Parents/guardians** — names and roles (Parent A / Parent B / other).
- **Custody schedule** — schedule rules, planned assignments, exceptions and overrides.
- **Event logs** — custody exchanges, communications (with method: call/text/email), behavioral notes, finance entries.
- **Court / legal information** — case number, court name, attorney name, support order amounts.
- **Financial records** — child support obligations, expense entries, payment status (we do **not** collect credit card numbers, bank account numbers, or other payment instruments).
- **File attachments** — evidence files (photos, documents) you choose to upload.

**Where this data lives:**

| Storage | What's stored | Who can access it |
|---|---|---|
| Your browser's IndexedDB (Dexie) | Working copy of all of the above for offline-first performance | Only you, on the device/browser where you installed the add-on |
| Your Google Sheet | Durable copy synced from IndexedDB | You and anyone you share the Sheet with |
| Your Google Drive folders (`Verascribe Evidence — {Your Workbook Name}`, etc.) | Evidence attachments and exports | You and anyone you share those folders with |
| Google Apps Script Document Properties on your selected workbook | License email, license token, trial dates, workbook ID | You (Verascribe service can read these via the OAuth scopes you granted) |

**Verascribe never receives a copy** of your custody, financial, or evidence data. The license-registration call described in Section 5 is the **only** outbound transmission to Verascribe-controlled infrastructure.

When you submit a "Contact Us" support request, the contents of that message reach a Verascribe email inbox. If you choose to include specific details about your custody, financial, or evidence records in that message, Verascribe will receive that information only because you sent it — please include only what you want us to see.

---

## 5. Information transmitted to Verascribe

The only data sent to Verascribe-controlled servers is the minimum needed to operate the licensing system. Specifically, calls to **`_registry.myverascribe.com`** include:

- Your Google Account email address.
- A workbook identifier (a stable ID for the Google Sheets workbook the app created for you).
- A license token (if you have one) and an HMAC-SHA256 signature used to prevent tampering.
- A timestamp.

We use this data only to:
- Determine whether you have a valid trial or paid license.
- Prevent abuse (e.g., the same license being used across an unreasonable number of workbooks).
- May notify you of important **transactional** Service updates, such as expiration notices and critical security announcements (we do not send marketing or promotional emails).
- Maintain a continuous record of customer relationships. License-key recovery for past customers is handled manually: if you lose your license key, you contact us at the email address in Section 14 and we look up your record and respond. We also use the record to identify returning customers when they purchase a new license.

We do not use this data for advertising, profiling, or sale to third parties. License records are retained indefinitely by default to support the purposes above; you may request deletion at any time (see Sections 10 and 11).

---

## 6. Information we do **not** collect

To eliminate ambiguity, Verascribe Guardian does **not** collect, store, or transmit:

- Google Analytics, Mixpanel, or any other behavioral analytics signal.
- Crash/error telemetry to Sentry, Datadog, or comparable services.
- Tracking cookies or third-party advertising pixels. (The add-on uses no cookies. It uses small amounts of `sessionStorage` and `localStorage` strictly for UI state — for example, which dashboard sections you've collapsed. This storage is strictly necessary for Service functionality and is exempt from consent requirements under the EU ePrivacy Directive Art. 5(3).)
- Device fingerprints, IP-based geolocation, or browser-feature fingerprints beyond what your browser sends to Google as part of normal HTTPS traffic.
- Payment card numbers or bank account information (the Service is not a payment processor; it tracks support amounts and payment **status**, not payment **instruments**).

**Do Not Track signals:** The Service does not engage in cross-site tracking and therefore does not alter its behavior in response to browser Do Not Track ("DNT") signals. We do not track you across third-party websites or services.

---

## 7. How we use the limited information we do receive

| Information | Purpose |
|---|---|
| Your email address | License validation, trial registration, transactional service communications, long-term customer relationship records (returning-customer identification, license-key recovery for past customers) |
| Workbook identifier | Bind a license to a particular Sheet and detect over-use |
| License token + signature | Cryptographic verification that a license is genuine |
| "Contact Us" message body | Respond to your support request |

We do not sell, rent, or share any of the above with advertisers, data brokers, or unrelated third parties.

---

## 7a. Legal bases for processing (EU/UK users)

If you are located in the European Economic Area or United Kingdom, the following legal bases under GDPR Article 6 apply to our processing of your personal data:

| Personal data | Legal basis | Notes |
|---|---|---|
| Email address and workbook ID (license validation) | Art. 6(1)(b) — performance of a contract | Necessary to provide the licensed Service you requested |
| Email address (transactional service communications) | Art. 6(1)(b) / Art. 6(1)(f) — contract performance / legitimate interests | Sending expiration notices and critical security updates is necessary to perform the contract and serves our mutual interests |
| License records retained post-expiry (fraud prevention, customer relationship continuity, returning-customer identification) | Art. 6(1)(f) — legitimate interests | We have a legitimate interest in preventing license fraud, supporting recovery of license keys for past customers, maintaining a continuous record of customer relationships, and identifying customers who return to purchase a new license. License records are retained **indefinitely by default**, subject in all cases to your right of erasure described in Section 11. The data retained for these purposes is limited to email address, workbook identifier, and license dates; no custody, financial, or evidence data is retained. You may request deletion at any time and we will acknowledge your request within 72 hours and complete deletion within 30 days. |
| Support correspondence | Art. 6(1)(b) — contract performance | Necessary to respond to support requests you initiate |

Where we rely on legitimate interests (Art. 6(1)(f)), you have the right to object to that processing. To exercise that right, contact us at the address in Section 14.

**EU Representative (Art. 27 GDPR):** Verascribe is not established in the EU or UK but may process personal data of EU/UK residents. We rely on the Art. 27(2) exemption on the following basis: (a) the only personal data we receive from EU/UK residents is an email address and workbook identifier, transmitted once per license-validation event; (b) we do not actively target EU/UK users through EU-specific advertising, EU-language content, or EU-directed marketing — EU/UK users reach the Service through a global marketplace without Verascribe soliciting them specifically; (c) the processing is limited in scope, does not involve Art. 9 special-category data, and presents a low risk to the rights and freedoms of individuals. If a supervisory authority takes the view that a representative must be appointed, we will comply promptly. You may contact us to raise this concern.

---

## 8. Sharing and third-party recipients

We share information only with the following categories of recipients:

- **Google LLC** — because the Service runs entirely on Google Workspace infrastructure (Apps Script, Sheets, Drive, Gmail). Google's processing of your data is governed by Google's own privacy policy and the Google Workspace terms.
- **Porkbun, Inc.** — domain registrar and DNS provider for `myverascribe.com` and `_registry.myverascribe.com`. `_registry.myverascribe.com` is a DNS record that resolves to the actual Google Apps Script endpoint that processes license-validation calls. Porkbun's DNS servers may log the lookup of the registry domain (IP address and timestamp of the DNS query), but never receive the HTTP request itself or the license payload. Porkbun does not receive any custody, financial, or evidence data.
- **Google LLC** (see above) — the Google Apps Script endpoint that `_registry.myverascribe.com` resolves to is the system that actually receives and processes license-validation data (email address, workbook ID, token, signature).
- **Email infrastructure** — all outbound mail (in-app support requests, license receipts, and any replies from Verascribe) is sent via **Gmail / Google Workspace** and is therefore also covered under Google LLC.
- **Google LLC (infrastructure logging)** — The Google Apps Script web app that processes license-validation requests (`script.google.com/macros/s/…`) generates server-side request logs (IP address, timestamp, HTTP status code) as part of Google's standard Cloud Logging infrastructure. This logging is automatic and occurs on Google's side; it is governed by Google's Privacy Policy. Verascribe can access these logs as the project owner but does not routinely use them for any purpose other than debugging.
- **Legal authorities** — if required by law, court order, or to defend our legal rights.

We do not engage in "sale" or "sharing" of personal information as those terms are defined under the California Consumer Privacy Act ("CCPA") or the California Privacy Rights Act ("CPRA"). We do not sell or share the personal information of any consumer, including consumers under the age of 16, as those terms are defined under the CCPA/CPRA.

---

## 9. Children's data and COPPA

**Verascribe Guardian is intended for use by adults** (typically parents, guardians, attorneys, or family-court professionals) to record information **about** children in their care. The Service is **not directed to children** under 13, and we do not knowingly accept account creation or data entry from children.

We do, however, recognize that the Service stores information **about** minor children — including names, birthdates, and custody arrangements — when entered by the adult user. We treat that information with the same care as the adult user's own data: it remains in the user's IndexedDB, Google Sheet, and Google Drive, and is never transmitted to Verascribe.

Adult users are responsible for ensuring that any audio recordings, photographs, video files, or other media attached as evidence and depicting minors comply with applicable laws governing the recording and storage of content involving children.

**By entering information about third parties (including the other parent, minor children, or other individuals) into the Service, you represent that you have lawful authority to record, store, and document that information under the laws applicable to you.** This includes compliance with any state or local laws requiring the consent of all parties before recording a conversation.

If you are a parent or guardian and you believe a child has used the Service to enter information directly, please contact us at the address in Section 14 and we will **promptly delete** any personal information we determine was collected directly from a child without verifiable parental consent.

---

## 10. Data retention and deletion

Because we do not host your custody data, **deletion is in your hands** for most of what the Service generates:

| Data category | Where stored | Retention period | How to delete |
|---|---|---|---|
| Custody logs, schedules, settings (working copy) | Your browser's IndexedDB | Until you clear site data | Clear browser site data |
| Custody logs, schedules, settings (durable copy) | Your Google Sheet | Until you delete the Sheet | Delete the Sheet in Google Drive |
| Evidence attachments, exported reports, backups | Your Google Drive ("Verascribe Evidence" folders) | Until you delete those folders | Delete the folders in Google Drive |
| License email, workbook ID, license dates, trial dates | Verascribe license registry (`_registry.myverascribe.com`) | Retained **indefinitely** to support fraud prevention, license-key recovery for past customers, and identification of returning customers — subject to your right of erasure | Contact us (Section 14); we will acknowledge within 72 hours and complete deletion within 30 days. **Note:** deletion disables write functionality in the Service for that workbook, equivalent to license expiration. See Section 11 for details. |
| Support correspondence | Email (Gmail/Google Workspace) | Until you request deletion | Contact us (Section 14) |

Verascribe cannot delete data stored in your own Google Sheet or Google Drive — that data is yours and outside our control.

---

## 11. Your rights

Depending on where you live, you may have rights under applicable privacy laws. **Nemerai, LLC is a small business and typically does not meet the minimum processing thresholds that make companies "covered businesses" under most US state privacy laws** — for example, the Texas Data Privacy and Security Act (TDPSA), Oregon Consumer Privacy Act (OCPA), Maryland Online Data Privacy Act (MODPA), Colorado Privacy Act, Connecticut Data Privacy Act, Virginia CDPA, and Utah Consumer Privacy Act generally apply only to companies processing personal data of 100,000 or more consumers annually (or 25,000+ consumers where more than 25% of revenue comes from selling data). We provide the following rights voluntarily, regardless of whether we are legally required to do so under any specific state law. These rights also exist under the GDPR (European Economic Area and UK) and Quebec Law 25, as detailed below.

Your rights typically include:

- **Access** — Request a copy of the personal information we hold about you (which, in practice, is limited to the license records described in Section 5).
- **Correction** — Ask us to correct inaccurate information.
- **Deletion** — Ask us to delete your license records. Note that we cannot delete data stored in your own Sheet or Drive — only you can do that. **Important consequence:** Deleting your license record will cause license validation to fail on the next check, which will **disable the Service's write functionality** (creating new records) for the affected workbook — exactly as if your license had expired. Read access and the JSON/PDF export tools remain available, and the data in your Google Sheet and Google Drive is not affected. If you intend to continue actively using the Service, do not request deletion of your license record while your license is current.
- **Portability** — The Service includes built-in JSON export of your full dataset, which you can run at any time without contacting us.
- **Withdraw consent / object to processing** — Revoke our OAuth permissions at any time at [myaccount.google.com/permissions](https://myaccount.google.com/permissions). Doing so will stop the web app from opening but will not delete the data already in your Sheet or Drive. You may also object to processing based on legitimate interests (see Section 7a).
- **Lodge a complaint** — With your local supervisory authority (e.g., your state Attorney General, or an EU Data Protection Authority).

To exercise any of these rights, contact us at the address in Section 14. We will respond within the timeframes required by applicable law (generally 30 to 45 days).

### CCPA / CPRA categories of personal information (California)

For California residents, we provide the following summary of personal information categories we collect, as defined under Cal. Civ. Code § 1798.140:

| CCPA Category | Examples we collect | Source | Business purpose |
|---|---|---|---|
| Identifiers | Google Account email address, workbook identifier | Directly from your Google Account (via OAuth) | License validation and transactional service communications |
| Commercial information | License purchase date, license type, license expiry | Directly from your purchase action | Provide licensed Service; fraud prevention |

**Sensitive Personal Information (CPRA).** We do **not** collect Sensitive Personal Information (SPI, as defined under Cal. Civ. Code § 1798.140(ae)) through the license-validation pathway. This includes no precise geolocation, no health or biometric data, no racial or ethnic origin, no financial account credentials, and no government ID numbers. Data about minors that you enter into the Service (names, birthdates, custody schedules) is stored exclusively in your own Google Sheet and browser — it is never transmitted to Verascribe and therefore does not constitute SPI "collected by" Verascribe under the CPRA.

**Retention schedule.** Retention periods for each category of personal information we collect are set out in the table in **Section 10** above.

We do not sell or share any personal information, including the categories listed above.

### Quebec Law 25 (Quebec residents)

If you are a Quebec resident, the following additional information applies under *Loi modernisant des dispositions législatives en matière de protection des renseignements personnels* (Law 25 / formerly Bill 64):

- **Person responsible for personal information protection:** The principal of Nemerai, LLC, contactable at the address in Section 14.
- **Cross-border transfer:** Your email address and workbook identifier are transmitted to a Google Apps Script endpoint in the United States for license validation. A Privacy Impact Assessment (PIA) has been conducted confirming that this transfer presents an acceptable level of protection given the limited scope of data and the safeguards in place (HTTPS, HMAC-SHA256 signature, Google infrastructure security).
- **Breach notification:** In the event of a confidentiality incident (breach) affecting personal information we control, we will notify you and the Commission d'accès à l'information (CAI) within 72 hours of becoming aware of the incident, as required by Law 25 § 3.6.
- **Rights under Law 25:** You have the rights to access, correct, and request deletion of personal information we hold about you (limited to the license records in Section 5). Contact us at the address in Section 14. We will respond within 30 days.

---

## 12. Security

Verascribe Guardian's security model relies primarily on Google's infrastructure: your data lives in your own Google account, protected by your Google credentials and any two-factor authentication you have enabled. The license registry uses HTTPS in transit and HMAC signatures to protect license-validation calls from tampering.

No internet-connected service can be guaranteed 100% secure. If we ever become aware of a security incident affecting personal information we control (i.e., the license registry), we will notify affected users and applicable regulators in accordance with applicable breach-notification laws, including the Florida Information Protection Act (Fla. Stat. § 501.171), which requires notification within **30 days** of discovery for Florida residents.

---

## 13. International transfers

If you are located outside the United States, please be aware that the license registry is currently hosted in the **United States**. By using the Service, you consent to the transfer of the limited license-related information described in Section 5 to that jurisdiction.

While the Service does not specifically target EU/UK residents through localized advertising, EU-language content, or EU-directed marketing, EU and UK users may reach the Service through the Google Workspace Marketplace. Where they do, we apply the GDPR legal bases and rights described in Sections 7a and 11. If we begin actively directing the Service to those jurisdictions, this section will be updated and any additional transfer safeguards (such as Standard Contractual Clauses and a Transfer Impact Assessment) will be put in place before that offering goes live.

---

## 14. Contact us

If you have any questions about this policy, or wish to exercise any rights described above, please contact:

**Nemerai, LLC**
Email: **support@myverascribe.com**
Postal: 2113 Everglades Ln, #146, The Villages, FL 32163

**Person responsible for personal information protection (Quebec Law 25 / Loi 25):** Nem Le, Principal, Nemerai, LLC — contactable at the email and postal address above.

---

## 15. Changes to this policy

We may update this policy from time to time. The "Last Updated" date at the top of the page reflects the most recent version. Material changes will be announced inside the Service or by email to the address associated with your license at least **30 days** before they take effect. Continued use of the Service after a change takes effect constitutes acceptance of the revised policy.

**Next scheduled review: October 27, 2026.** Any addition of a new data category, change to third-party data recipients, new jurisdiction we actively enter, or applicable change in law triggers an immediate unscheduled review outside this cadence.

