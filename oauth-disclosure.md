---
layout: legal
title: OAuth Disclosure
---

# OAuth Permissions Disclosure

**Last Updated:** 2026-05-13

This page explains, in plain language, every Google OAuth permission that **Verascribe Guardian** asks for when you first open the app — exactly what each one allows, and why each one is necessary. It is designed to satisfy Google's OAuth verification requirements and to give you a single, scannable place to verify what the app can — and cannot — do with your Google account.

For full detail, see our [Privacy Policy](./privacy-policy.md) and [Terms of Service](./terms-of-service.md).

> **Note for Google OAuth reviewers:** This page is linked directly from the OAuth consent screen and is intended for your review. Verascribe Guardian is published as a **Google Apps Script Web App** (executed as `USER_ACCESSING`, accessible to anyone with a Google account). The scopes listed below correspond to the declared scopes in the deployed web-app manifest (`appsscript.webapp.json`), in the same order they appear in that manifest. The product also includes a thin add-on launcher card that lives in Google Sheets (a separate manifest, `appsscript.addon.json`); the launcher is **not part of v1 Marketplace submission** and requests no Drive scopes. Users who install only the web app authorize only the scopes below.

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
| `spreadsheets.currentonly` | Read and edit a Google Sheet workbook only during the active app session | Combined with the file-picker handshake on `drive.file` (next row), this means the app can only ever read or edit the one workbook you explicitly selected. Persists your custody log, schedule, and settings into hidden system tabs of that workbook |
| `drive.file` | Access **only the files you explicitly select** via Google's file-picker dialog, plus files Verascribe Guardian creates in your Drive | Let you use Google's own file-picker to grant access to the one workbook you choose — the app can only see what you explicitly select. Also stores evidence attachments, generated PDF/CSV reports, and JSON backups in a Verascribe folder you own |
| `script.send_mail` | Send mail from your Gmail account | Email license-registration receipts to you and route "Contact Us" support messages. Mail is sent from your own account using Google's `MailApp` service — we never read your inbox, drafts, or any other mail |
| `script.external_request` | Make outbound HTTPS calls from the app's server code | Validate your license against `_registry.myverascribe.com`; fetch a fallback configuration file from `raw.githubusercontent.com` if the registry is unreachable; perform DNS-over-HTTPS lookups (`dns.google` and `cloudflare-dns.com`) to detect network tampering with the registry domain. These four hosts are the complete list permitted by the app's manifest |
| `script.scriptapp` | Manage time-based triggers | Install a daily maintenance trigger that refreshes rolling-window metrics and cleans up temporary files |

> **Note on the Verascribe Guardian Library (for Google reviewers):** The web app depends on a shared Apps Script library (Library ID: `1jn6m2AA4sSvniiT-FC6j_QgDunt3o60REnVM5PE1ekvoulIISTxOFUM0`). The library runs *inside* the web-app project — it is not installed separately by users and does not present its own OAuth consent screen. The library's `appsscript.json` declares a subset of the scopes above. The scopes listed in this document correspond to the **web-app project's manifest** (`appsscript.webapp.json`), which is the project users authorize on first launch.

---

## What we **do not** access

By design and by application code, Verascribe Guardian does not:

- Read or modify any Google Sheet other than the one workbook you select via Google's file-picker.
- Read, list, or modify any file in your Google Drive other than (a) files you explicitly select via the file-picker, or (b) files Verascribe Guardian itself creates in your "Verascribe Evidence" folder.
- Read your Gmail inbox, drafts, or any message we did not send through the app.
- See your Google Calendar, Contacts, Photos, YouTube, Search history, or any other Google product data.
- Track you across the web, build advertising profiles, or share your data with advertisers or data brokers.

---

## Where your data actually lives

The Service is **offline-first**. The custody, financial, and evidence data you create stays in three places, all of which **you** own and control:

1. **Your browser's IndexedDB** — a working copy on your device for fast offline access.
2. **Your Google Sheet** — durable storage in your chosen workbook. The first time you open Verascribe Guardian, you'll pick this workbook yourself using Google's file-picker. The app reads and writes hidden system tabs inside it (these hold your data — they're not visible during normal Sheets use and cannot be accidentally edited).
3. **Your Google Drive** — evidence attachments, generated reports, and backups in folders named `Verascribe Evidence — {Your Workbook Name}` and `Verascribe — Archived Evidence (Standalone)`. The folder names include your workbook name so each tracker has its own evidence folder.

### Outbound network calls

The only outbound transmission to Verascribe-controlled infrastructure that carries any of **your data** is a license-validation call. The app contacts `_registry.myverascribe.com` — a DNS record owned by Nemerai, LLC — which redirects to a Google Apps Script endpoint also owned and operated by Nemerai, LLC. The payload contains only your email address, a workbook identifier, your license token, and a cryptographic signature — nothing else. See [Section 5 of the Privacy Policy](./privacy-policy.md#5-information-transmitted-to-verascribe).

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

Email **myverascribe@gmail.com** and we will respond within a reasonable time, generally no more than 5 business days.
