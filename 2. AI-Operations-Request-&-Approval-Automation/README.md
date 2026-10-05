# AI Operations Request & Approval Automation

A hands-on Make.com project I built to practice classifying employee operations requests and routing them based on priority, risk, and approval requirements.

## What I Built

The workflow receives an operations request through a webhook and uses OpenAI to return structured classifications such as category, priority, risk level, approval requirement, routing decision, summary, and reason.

The result is logged in Google Sheets and then routed to the appropriate response.

## Workflow

**Webhook → OpenAI → Parse JSON → Create Request ID → Google Sheets → Router → Email Route**

### Key Logic

- Requests are classified using predefined category and priority values.
- Risk is classified as LOW, MEDIUM, or HIGH.
- Requests requiring management approval are routed to a management review email.
- Automation-eligible requests use the automation route.
- High-risk requests are escalated.
- Unmatched cases go to a fallback route.
- The original request and AI result are logged for tracking.

## Tools Used

- Make.com
- OpenAI
- Webhooks
- JSON / Parse JSON
- Routers & Filters
- Google Sheets
- Gmail

## What I Practiced

This project helped me practice structured AI classification, routing logic, approval workflows, risk-based decisions, and keeping an audit trail of automation requests.

## Note

This is a hands-on portfolio/training project. The AI provides recommendations; the Make.com workflow controls the routing rules.
