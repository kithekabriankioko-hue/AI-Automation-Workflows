# AI Security Incident Triage and Escalation

## Overview
A Make.com portfolio workflow that accepts a simulated security incident through a webhook, asks an AI model to recommend a severity, category, summary, and next action, parses the structured response, validates the allowed values, and routes the incident for logging or review.

## Problem
Operational and security teams receive incident descriptions in different formats. Manually summarizing and categorizing each report can slow down triage. This demonstration explores how AI can assist with consistent first-pass classification while keeping validation and human review in the workflow.

## Workflow
1. **Webhook intake** receives an incident ID, timestamp, source, and description.
2. **Variable assignment** creates a request identifier and timestamp.
3. **OpenAI** proposes a severity, category, action, summary, and reason in JSON.
4. **Parse JSON** converts the response into structured fields.
5. **Validation variables and router** check that category, severity, and action use allowed values.
6. **Downstream routes** log results to Google Sheets and send email notifications; certain paths use an HTTP test request and separate logging or escalation behavior.

## Tools and concepts
- Make.com
- OpenAI
- Webhooks and structured JSON
- Conditional routing and business-rule validation
- Google Sheets audit logging
- Gmail notifications
- HTTP integration for a test route

## Safety and design notes
- AI output is advisory; it is not proof that an attack occurred.
- Invalid or unexpected values should not be treated as trusted decisions.
- Use synthetic incident data only in the public sample.
- Before using this blueprint, configure your own connections, recipient addresses, webhook, and destination sheet.
- This is a learning/portfolio workflow, not a production incident response platform.

## Sample input
See [`sample-data.json`](sample-data.json) for synthetic webhook examples and the expected AI output schema.

## Import notes
Import `blueprint.json` into Make.com, then review every module and filter. Reconnect OpenAI, Google Sheets, and Gmail using your own accounts. Confirm the route filters and mapped fields in your Make workspace before running a test.

## Screenshots
Place overview and focused-route screenshots in the `screenshots/` folder.
