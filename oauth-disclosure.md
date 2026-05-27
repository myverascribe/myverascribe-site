---
layout: legal
title: OAuth Disclosure
---

# OAuth Permissions Disclosure

**Last Updated:** 2026-05-13

This page explains, in plain language, every Google OAuth permission that **Verascribe Guardian** asks for when you first open the app — exactly what each one allows, and why each one is necessary. It is designed to satisfy Google's OAuth verification requirements and to give you a single, scannable place to verify what the app can — and cannot — do with your Google account.

For full detail, see our [Privacy Policy](./privacy-policy.md) and [Terms of Service](./terms-of-service.md).

> **Note for Google OAuth reviewers:** This page is linked directly from the OAuth consent screen and is intended for your review. Verascribe Guardian is published as a **Google Apps Script Web App** (executed as `USER_ACCESSING`, accessible to anyone with a Google account). The scopes listed below correspond to the declared scopes in the deployed manifest (`appsscript.json`), in the same order they appear in that manifest.

---

## Limited Use compliance

Verascribe Guardian's use of information received from Google APIs adheres to the **[Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy)**, including the **Limited Use** requirements.

In particular:
- We use your Google Workspace data **only to provide and improve user-facing features** of the Service that are visible and prominent in the user interface.
- We do **not** transfer Google Workspace data to others except as necessary to provide the Service, comply with applicable law, or as part of a merger or acquisition. Our complete list of subprocessors is in [Section 8 of our Privacy Policy](./privacy-policy.md#8-sharing-and-third-party-recipients).
- We do **not** use Google Workspace data for **serving advertisements**.
- We do **not** allow humans to read your Google Workspace data unless (a) we have obtained your affirmative consent for specific messages, (b) it is necessary for security purposes (e.g., investigating abuse), (c) it is necessary to comply with applicable law, or (d) it is for internal operations and the data has been aggregated and anonymized.
- We do **not** use Google Workspace data to develop, improve, or train **generalized AI/ML models** of any kind.

---

## The permissions we request

| OAuth Scope | Plain-language summary | Why we need it |
|---|---|---|
| `userinfo.email` | See the email address on your Google Account | License registration, trial validation, and support correspondence |
| `drive.file` | Access only the files Verascribe Guardian creates in your Drive — workbooks, evidence attachments, reports, and backups | The app creates Google Sheets workbooks for your custody records. You can create more than one and switch between them inside the app. The same scope lets the app save evidence attachments, generated PDF/CSV reports, and JSON backups into Verascribe-named folders in your Drive. Verascribe Guardian cannot see any other file in your Drive that it did not create |
| `script.send_mail` | Send mail from your Gmail account | Used only when you submit a "Contact Us" support request from inside the app. The message is sent from your own Gmail to a fixed Verascribe support address — you cannot choose another recipient. Mail is sent using Google's `MailApp` service. We never read your inbox, drafts, or any other mail |
| `script.external_request` | Make outbound HTTPS calls from the app's server code, to a fixed list of six hosts | Four kinds of outbound HTTPS calls:<br><br>**Google's Sheets and Drive APIs** (`sheets.googleapis.com`, `www.googleapis.com`) — to read and write your workbook content and to manage your evidence files, reports, and backups. These endpoints belong to Google, not Verascribe; calls are governed by Google's Privacy Policy.<br><br>**License validation** — calls go to `_registry.myverascribe.com`, a CNAME (a DNS alias) that points to a Google Apps Script web app we own and operate at `script.google.com`.<br><br>**Fallback config** (`raw.githubusercontent.com`) — used only if the license registry is temporarily unreachable. No user data sent.<br><br>**DNS-over-HTTPS lookups** (`dns.google`, `cloudflare-dns.com`) — confirm the registry domain hasn't been redirected by a hostile network. Only the domain name is sent — never any of your data.<br><br>These six hosts are the complete list permitted by the app's `urlFetchWhitelist` |

> **Note on the Verascribe Guardian Library (for Google reviewers):** The web app depends on a shared Apps Script library (Library ID: `1jn6m2AA4sSvniiT-FC6j_QgDunt3o60REnVM5PE1ekvoulIISTxOFUM0`). The library runs *inside* the web-app project — it is not installed separately by users and does not present its own OAuth consent screen. The library's `appsscript.json` declares a subset of the scopes above. The scopes listed in this document correspond to the web-app project's manifest (`appsscript.json`), which is the project users authorize on first launch.

---

## What we **do not** access

By design and by application code, Verascribe Guardian does not:

- Read or modify any Google Sheet other than the workbooks Verascribe Guardian itself created for you.
- Read, list, or modify any file in your Google Drive other than the files Verascribe Guardian itself creates. That means: workbooks you create through the app, evidence attachments you upload through the app, and reports and backups the app generates in Verascribe-named folders.
- Read your Gmail inbox, drafts, or any message we did not send through the app.
- See your Google Calendar, Contacts, Photos, YouTube, Search history, or any other Google product data.
- Track you across the web, build advertising profiles, or share your data with advertisers or data brokers.

---

## Where your data actually lives

The Service is **offline-first**. The custody, financial, and evidence data you create stays in three places, all of which **you** own and control:

1. **Your browser's IndexedDB** — a working copy on your device for fast offline access.
2. **Your Google Sheets workbooks** — durable storage that mirrors your local working copy. When you first use Verascribe Guardian you create a workbook inside the app (you can create additional workbooks later and switch between them — for example, one per child or one per case). The app reads and writes inside each workbook to keep your durable copy in sync with the working copy in your browser.
3. **Your Google Drive** — evidence attachments, generated reports, and backups in folders named `Verascribe Evidence — {Your Workbook Name}` and `Verascribe — Archived Evidence (Standalone)`. The folder names include your workbook name so each tracker has its own evidence folder.

### Outbound network calls

The only outbound transmission to **Verascribe-controlled** infrastructure that carries any of your data is a license-validation call. The app contacts the `_registry.myverascribe.com` hostname (a DNS record on a domain owned by Nemerai, LLC). It is a CNAME alias for a Google Apps Script web app also owned and operated by Nemerai, LLC, hosted at `script.google.com`. The payload contains only your email address, a workbook identifier, your license token, and a cryptographic signature — nothing else. See [Section 5 of the Privacy Policy](./privacy-policy.md#5-information-transmitted-to-verascribe).

The app's other outbound calls go to Google's own infrastructure — the Sheets API and Drive API (`sheets.googleapis.com`, `www.googleapis.com`) — to read and write your workbook content. These calls are governed by [Google's Privacy Policy](https://policies.google.com/privacy).

For completeness, the app's network whitelist also permits two other kinds of outbound calls that do **not** carry your data:

- A fallback fetch to a public GitHub URL (`raw.githubusercontent.com`) for the license-registry configuration, used only if `_registry.myverascribe.com` is unreachable.
- DNS-over-HTTPS lookups to `dns.google` and `cloudflare-dns.com` to verify the registry domain hasn't been hijacked by a hostile network. These calls contain only the domain name being looked up.

---

## How to revoke access

You can withdraw your permissions at any time:

1. Visit **[myaccount.google.com/permissions](https://myaccount.google.com/permissions)**.
2. Find **Verascribe Guardian** in the list.
3. Click **Remove Access**.

Revoking access will stop the app from opening. If you change your mind, you can re-authorize by visiting the app link again — Google will ask you to approve permissions once more. Revoking does **not** delete the data already stored in your own Google Sheet or Google Drive — those remain in your account until you delete them.

---

## Questions?

Email **support@myverascribe.com** and we will respond within a reasonable time, generally no more than 5 business days.
