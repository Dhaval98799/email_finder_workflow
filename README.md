# 🔍 Apollo Email Finder for International Buyers

> **n8n automation workflow** — Reads buyer names from Google Sheet, searches Apollo.io API, finds verified email IDs and contact details, writes back automatically.

---

## What This Does

| Input | Process | Output |
|-------|---------|--------|
| Company Name + Country (Google Sheet) | Apollo.io People Search API | Email, Phone, LinkedIn, Title → back to Sheet |

---

## Features

- ✅ Reads pending rows from Google Sheet automatically
- ✅ Searches Apollo.io for matching contacts
- ✅ Finds Owner / Director / CEO emails
- ✅ Verifies email deliverability
- ✅ Writes all data back to Google Sheet
- ✅ Marks each row Done / Not Found / Error
- ✅ Runs every 5 minutes on schedule

---

## Tools Used (All Free Tier Available)

| Tool | Purpose | Free Limit |
|------|---------|-----------|
| n8n | Automation platform | 2,500 runs/month |
| Apollo.io | Email + contact finder | 50 exports/month free |
| Google Sheets | Input + output database | Unlimited |
| Gmail | Notifications | Free |

---

## Google Sheet Setup

### Required Column Headers (Row 1)

```
A: Status
B: Row_Number  
C: Company_Name
D: Country
E: Country_Code
F: Industry
G: Apollo_Email_1
H: Apollo_Email_2
I: Apollo_Email_3
J: Contact_Name
K: Contact_Title
L: Contact_LinkedIn
M: Contact_Phone
N: Company_Domain
O: Apollo_Confidence
P: Research_Notes
Q: Last_Updated
```

### Status Values
- `Pending` → Not yet processed
- `Processing` → Currently running
- `Done` → Data found and written
- `Not Found` → Apollo returned no results
- `Error` → API error, will retry

---

## Setup Instructions

### Step 1 — Apollo.io API Key
1. Go to: https://app.apollo.io
2. Settings → Integrations → API
3. Copy your API Key

### Step 2 — n8n Import
1. Open n8n → New Workflow
2. Click `...` → Import from file
3. Select `apollo_email_finder_workflow.json`

### Step 3 — Replace These Values in Workflow

| Placeholder | Replace With |
|------------|-------------|
| `YOUR_SHEET_ID` | Your Google Sheet ID |
| `YOUR_APOLLO_KEY` | Apollo.io API Key |

### Step 4 — Connect Google Sheets
1. n8n → Credentials → Add → Google Sheets OAuth2
2. Authorize with your Google account

### Step 5 — Test
1. Add 1 row with Status = `Pending`
2. Click "Test Workflow"
3. Check Sheet for results

### Step 6 — Activate
- Toggle "Active" ON → Runs every 5 minutes automatically

---

## Apollo API Limits

| Plan | Monthly Exports | Cost |
|------|----------------|------|
| Free | 50 contacts | $0 |
| Basic | 1,000 contacts | $49/mo |
| Professional | 5,000 contacts | $99/mo |

---

## Folder Structure

```
project1_apollo_email_finder/
├── README.md                          ← This file
├── apollo_email_finder_workflow.json  ← Import into n8n
└── SETUP_GUIDE.md                     ← Detailed steps
