AI Employee Access Request Automation

A hands-on Make.com project I built to practice automating employee access requests using AI classification, validation, human review, and an API request.

What I Built

The workflow receives an employee access request through a webhook and uses OpenAI to classify the request.

The AI returns:

- Priority
- Category
- Action
- Summary
- Reason

Make.com then validates the AI output against predefined rules before deciding what happens next.

Workflow

Webhook → OpenAI → Parse JSON → Validation → Router → Human Review / API Request → Google Sheets Logging

Key Logic

- Invalid or incomplete requests are sent for human review.
- Sensitive requests such as admin, credential, payroll, or server access require human review.
- Valid normal requests can continue to the API step.
- Each request gets a unique Request ID.
- An idempotency key is included in the API request to demonstrate duplicate-request prevention.
- Requests and results are logged in Google Sheets for tracking.

Tools Used

- Make.com
- OpenAI
- Webhooks
- JSON / Parse JSON
- Routers & Filters
- HTTP/API
- Google Sheets
- Gmail

What I Practiced

This project helped me practice designing an automation where AI makes a recommendation, but Make.com applies the actual validation and business rules.

I also practiced human-in-the-loop approval, structured JSON, API requests, logging, and handling invalid requests.

Note

This is a hands-on portfolio/training project, not a production access-management system.

The API endpoint used in the project is a testing endpoint ("httpbin.org") to demonstrate the HTTP/API step.

Repository Structure

AI-Employee-Access-Automation/
├── README.md
├── blueprint/
│   └── scenario-blueprint.json
├── screenshots/
└── sample-data/
    └── sample-access-request.json