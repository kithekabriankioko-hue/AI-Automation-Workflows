# Management Access Review & Approval

A hands-on Make.com project I built to practice processing management decisions for employee access requests and updating the related records.

## What I Built

The workflow receives a management decision through a webhook and routes the request based on whether it was approved or rejected.

It searches the Google Sheet for the related Request ID and updates the existing record when it is found. If the record is not found, it creates a new tracking row.

## Workflow

**Webhook → Decision Router → Google Sheets Lookup → Update/Create Record → API Step for Approved Requests**

### Key Logic

- Rejected requests are recorded with the reviewer decision.
- Approved requests continue to the execution path.
- The workflow looks up the original request using its Request ID.
- Existing records are updated instead of creating duplicates.
- Missing records are added for tracking.
- Approved requests send a structured HTTP request and the result is logged back to the sheet.

## Tools Used

- Make.com
- Webhooks
- Routers & Filters
- Google Sheets
- HTTP/API

## What I Practiced

This project helped me practice approval workflows, record lookups, update-versus-create logic, request IDs, API execution, and maintaining an audit trail.

## Note

This is a hands-on portfolio/training project. The API endpoint is a testing endpoint used to demonstrate the execution step.
