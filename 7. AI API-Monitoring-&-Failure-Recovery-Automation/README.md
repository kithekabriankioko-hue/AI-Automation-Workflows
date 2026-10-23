# AI API Monitoring and Failure Recovery Automation

## Overview
A Make.com portfolio workflow that sends an HTTP request to a test endpoint, classifies the response, retries selected transient status codes through a bounded four-attempt chain, and records the final result in Google Sheets with email alerts for failures.

## Problem
An API monitoring check can fail for different reasons. Retrying every failure is inefficient: a temporary server error may recover, while an authentication error or malformed request generally needs investigation rather than repeated retries.

## Workflow
1. **Webhook intake** receives a monitoring description.
2. **Variable assignment** creates a unique request ID and timestamp.
3. **HTTP request** checks the configured endpoint.
4. **Conditional retry chain** retries selected temporary statuses (429, 500, 502, and 503) up to four total attempts.
5. **Merge modules** select the final status code from the latest executed attempt.
6. **Classification router** separates successful responses from error classes.
7. **Google Sheets** records the result and **Gmail** sends alerts for applicable failures.

## Tools and concepts
- Make.com
- Webhooks and variables
- HTTP / REST endpoint testing
- Conditional logic and routers
- Bounded retries and final-status selection
- Google Sheets audit logging
- Gmail failure alerts

## Tested scenarios
- **200:** success path; logged as success with no retry.
- **401:** authentication failure; logged and alerted without transient-error retries.
- **503:** temporary server-error path; retry chain reaches the fourth attempt, then logs the final failure and sends an alert.
- **400:** intended bad-request classification test; confirm the configured router filter and run it in your own Make workspace before presenting it as verified.

## Safety and design notes
- The blueprint defaults all four HTTP modules to `https://httpbin.org/status/200`.
- To test a different status, update all four HTTP module URLs to the same httpbin status endpoint, run the scenario, then restore them to `/status/200`.
- This is a portfolio demonstration using a public test endpoint, not a production uptime-monitoring system.
- Configure your own webhook, Google Sheets connection, Gmail connection, recipient, and destination sheet after importing.

## Sample input
See [`sample-data.json`](sample-data.json) for sample webhook descriptions, test endpoints, and expected behaviors.

## Import notes
Import `blueprint.json` into Make.com and review the nested retry branches, merge mappings, classification filters, and every downstream field mapping. Reconnect Google Sheets and Gmail with your own accounts before running tests.

## Screenshots
Place overview and focused-route screenshots in the `screenshots/` folder.
