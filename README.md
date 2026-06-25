# Smart Customer Support Router

An n8n workflow that automatically triages incoming customer support messages, sends an instant acknowledgement, and routes the message based on content.

![n8n canvas](./screenshot.png)
*(Add a screenshot of the workflow canvas here — open the workflow in n8n and take a screenshot of the editor view.)*

## What it does

1. **Webhook** receives a customer feedback submission (e.g. from a contact form).
2. **Gmail** sends an instant "we received your message" reply to the customer.
3. A **JavaScript Code node** classifies the message into `Bug`, `Billing`, or `General` based on keywords.
4. A **Switch node** routes the message:
   - `Bug` / `General` → logged to a Google Sheet for tracking
   - `Billing` → an immediate alert email is sent to the billing team

## Stack

- n8n (Webhook, Code, Switch, Gmail, Google Sheets, Email Send nodes)
- JavaScript (custom classification logic)
- Google Sheets API
- Gmail / SMTP

## Setup

1. Import `workflow.json` into your n8n instance.
2. Connect your own credentials for Gmail, Google Sheets, and SMTP.
3. Replace `YOUR_GOOGLE_SHEET_ID` and `YOUR_GOOGLE_SHEET_ID_2` with your own spreadsheet IDs.
4. Update the `fromEmail` / `toEmail` fields in the "Send email" node.
5. Activate the workflow and point your feedback form to the generated webhook URL.

## Why I built it

To explore automated, rule-based triage for customer support — a common real-world use case for reducing response time and routing issues to the right place without manual sorting.
