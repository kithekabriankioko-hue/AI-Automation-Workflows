# AI Incident Triage & Escalation

A hands-on Make.com project I built to practice using AI to classify IT and security incident reports and route them based on predefined rules.

## What I Built

The workflow receives an incident report through a webhook and uses OpenAI to recommend an action, priority, category, department, summary, and reason.

The AI result is parsed and checked before the workflow decides whether to continue, escalate, or reject the output.

## Workflow

**Webhook → OpenAI → Parse JSON → Validation → Router → API / Security Review / Invalid Output**

### Key Logic

- AI recommendations use predefined action, priority, and category values.
- Privileged production-system access is directed to human review.
- Valid normal incidents can continue to the API step.
- Security-sensitive cases are escalated by email.
- Invalid AI output is sent to a separate review route.
- Incident information is logged in Google Sheets.

## Tools Used

- Make.com
- OpenAI
- Webhooks
- JSON / Parse JSON
- Routers & Filters
- HTTP/API
- Google Sheets
- Gmail

## What I Practiced

This project helped me practice incident triage, AI-assisted classification, validation, security-based routing, escalation, API requests, and audit logging.

## Note

This is a hands-on portfolio/training project. The API endpoint is a testing endpoint used to demonstrate the HTTP step.
