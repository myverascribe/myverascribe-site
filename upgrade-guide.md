---
layout: post
title: "How to Upgrade Your Data"
date: 2026-01-12
category: Guide
permalink: /upgrade-guide/
description: "A step-by-step guide to exporting and importing your workbook data."
---

## Upgrading In 3 Easy Steps

<div class="rounded-2xl border border-blue-500 border-opacity-40 bg-gradient-to-tl from-blue-900 via-blue-800 to-sky-900 p-6 text-slate-100 shadow-2xl">
  <p class="text-base font-semibold uppercase tracking-wide text-blue-200">Before You Begin</p>
  <div class="mt-4 space-y-6 text-base leading-relaxed text-slate-100">
    <div>
      <h4 class="mb-2 flex items-center gap-2 text-lg font-semibold text-blue-50">
        <span role="img" aria-label="Pro tip">💡</span>
        Pro-Tip: Preserve Your Paper Trail
      </h4>
      <p>Before you finalize your upgrade, remember: in family law, your data is your best defense. We strongly recommend archiving your previous workbooks in a dedicated "Legacy" folder within your Google Drive rather than deleting them.</p>
      <p class="mt-3">Data transfers are generally seamless, but think of your old file as your "Black Box" backup. Keeping the original record ensures that if an export or import is ever corrupted, your timestamped, legal-ready evidence remains 100% intact and retrievable.</p>
    </div>
    <div>
      <h4 class="mb-2 flex items-center gap-2 text-lg font-semibold text-blue-50">
        <span role="img" aria-label="Expert organization tip">📂</span>
        Expert Organization Tip
      </h4>
      <p>To keep your archives "audit-ready" for an attorney or mediator, avoid generic filenames like "Copy of Parent Record". Use a specific date-range format so you can locate specific evidence in seconds:</p>
      <p class="mt-3 font-semibold text-blue-100">Recommended Format: Archive_ParentRecord_YYYY-MM-DD_to_YYYY-MM-DD</p>
      <p class="mt-2 text-blue-100/90">Example: Archive_CustodyLog_2025-01-01_to_2026-02-11</p>
      <p class="mt-2">Why it works: This naming convention creates a chronological "Status Quo" history that is easy for legal teams to navigate without opening multiple files.</p>
    </div>
  </div>
</div>

### Step 1: Export your data.

<img src="{{ '/assets/images/guides/upgrade-guide/export-data.png' | relative_url }}" alt="Export Data" class="w-full rounded-lg border border-white/10 shadow-lg">

1. Open your existing workbook.
2. In the Verascribe Guardian sidebar menu, select "Export Data".
3. Click the "Export Now" button.
4. Choose a location to save your workbook data to your computer.
5. Click "Save".

### Step 2: Make a copy of the new workbook.

<img src="{{ '/assets/images/guides/upgrade-guide/make-a-copy.png' | relative_url }}" alt="Make a Copy" class="w-full rounded-lg border border-white/10 shadow-lg">

1. Open the link to the new workbook.
2. In the Google Sheets menu, select "File" > "Make a Copy".
3. Choose a location to save your workbook to your Google Drive.
4. Click "Save".

### Step 3: Import your data.

<img src="{{ '/assets/images/guides/upgrade-guide/import-data.png' | relative_url }}" alt="Import Data" class="w-full rounded-lg border border-white/10 shadow-lg">

1. Go to your copy of the new workbook.
2. In the Verascribe Guardian sidebar menu, select "Import Data".
3. Click the "Validate Import" button and select the file you exported in Step 1.
4. If the import is valid, click "Import File".
5. The import will begin. This may take a few minutes.

### Note: Pre-v2.1.0 Data

<img src="{{ '/assets/images/guides/upgrade-guide/import-warning-pre-210-data.png' | relative_url }}" alt="Import Data" class="w-full rounded-lg border border-white/10 shadow-lg">

If you are migrating from a version prior to v2.1.0, you will see a warning message indicating that some data columns are missing. **This is to be expected** and does not indicate an error.

1. **Payment_Method** column was added in 2.1.0 to support the addition of Personal Expenses tracking.
2. **Schedule_End_Date** column was added in 2.1.0 to support the addition of flexible scheduling.
3. **Reported_To** column was added in 2.4.0 to support the addition of Domestic Violence Incident tracking.
