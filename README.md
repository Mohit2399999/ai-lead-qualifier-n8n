# AI Lead Qualifier (n8n + Google Gemini)

An AI-powered lead qualification workflow built with **n8n** and **Google Gemini**. Every new lead from a contact form is scored automatically, logged to Google Sheets, answered with a personal reply, and, if it's a hot lead, sent straight to the business owner's inbox.

<img width="100%" alt="AI Lead Qualifier workflow in n8n" src="https://github.com/user-attachments/assets/eae49174-89ae-4c4c-9135-62291daf907d" />

## What it does

1. **Contact form**: a built-in n8n form collects name, email, company, budget and project details.
2. **AI scoring**: Google Gemini reads each lead and returns:
   - a score: `hot`, `warm` or `cold`
   - a one-line reason for the score
   - a one-line summary of what the lead wants
   - a personalized reply email
3. **Google Sheets log**: every lead is saved as a new row, so nothing gets lost.
4. **Instant auto-reply**: the lead receives a personal, AI-written reply within seconds.
5. **Hot lead alert**: hot leads trigger an alert email to the owner with the summary and budget.

## Why businesses use this

- Replies to every lead in seconds, even at night or on weekends
- Sales teams spend time only on the leads most likely to buy
- Every lead is tracked in one simple spreadsheet
- Runs on free tools: n8n (self-hosted), Gemini's free tier, Google Sheets and Gmail

## Tech stack

| Tool | Role |
|---|---|
| n8n | Workflow automation |
| Google Gemini (`gemini-3.8-flash`) | Lead scoring and reply writing |
| Google Sheets | Lead database |
| Gmail | Auto-replies and alerts |

## Setup

### 1. Import the workflow
In n8n, create a new workflow, open the **⋯ menu → Import from File**, and select `ai-lead-qualifier.json`.

### 2. Create the Google Sheet
Create a sheet with these headers in **row 1**:

```
Date | Name | Email | Company | Budget | Message | Score | Reason | Summary
```

### 3. Connect credentials
- **Google Gemini**: create a free API key at [Google AI Studio](https://aistudio.google.com) and add it to the Gemini node.
- **Google Sheets and Gmail**:
  - n8n Cloud: click **Sign in with Google**.
  - Self-hosted n8n: create an OAuth client in Google Cloud Console (Web application), add `http://localhost:5678/rest/oauth2-credential/callback` as a redirect URI, enable the Gmail, Google Sheets and Google Drive APIs, and paste the Client ID and Secret into n8n.

> Tip: check that there are no extra spaces at the end of pasted keys and IDs.

### 4. Configure
- **Log Lead in Sheet**: select your sheet.
- **Alert Owner**: replace `you@example.com` with the owner's email.

### 5. Test
Click **Test workflow**, submit the form with a large budget and a real project description, and check the sheet and inbox.

## Customization ideas

- Swap Google Sheets for a CRM (HubSpot, Airtable, GoHighLevel)
- Send hot lead alerts to Slack or WhatsApp
- Add a calendar booking link to the auto-reply
- Adjust the scoring rules in the AI prompt to fit any industry

## Need a custom automation?

I build AI automations for businesses: lead handling, reporting, data cleanup and workflow integrations.

- **LinkedIn:** [Priyanshu Suryawanshi](https://www.linkedin.com/in/priyanshu-suryawanshi-6875622aa)
- **X:** [@priyaanshhh22](https://x.com/priyaanshhh22)

If this project helped you, consider giving it a star.
