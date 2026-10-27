
# EFD TextFix — Technical Specification

## 1. Project Overview

**Project ID:** EXT-01  
**Product:** EFD TextFix  
**Company:** EfsunDev  
**Platform:** Google Chrome  
**Extension Standard:** Manifest V3  
**Project Type:** Browser Extension  
**Backend:** Cloudflare Workers (proposed; not implemented)

## 2. MVP Requirements

### FR-01: Text Input

The user must be able to enter or paste text into the extension interface.

### FR-02: Text Correction

The extension must support spelling, grammar, and punctuation correction.

### FR-03: Text Improvement

The extension must support improving and rewriting user-provided text.

### FR-04: Copy Result

The user must be able to copy the processed text to the clipboard.

### FR-05: User Interface

The interface must be clean, intuitive, responsive, and easy to use.

### FR-06: Error Handling

The extension must provide understandable feedback when text processing fails or the input is empty.

## 3. Technology Requirements

- JavaScript for application logic.
- HTML5 for interface structure.
- CSS3 for styling.
- Chrome Extension Manifest V3 for extension configuration.
- Chrome-provided APIs where appropriate.

No frontend framework is required for the initial version.

## 4. Architecture Constraints

- Chrome Extension Manifest V3.
- JavaScript, HTML5, and CSS3.
- One minimal Cloudflare Worker API endpoint is planned.
- No application database.
- No user accounts, payments, or unnecessary infrastructure.
- No secrets or API keys embedded in client-side source code.
- Provider API credentials must remain server-side.
- Validate requests and enforce usage limits on the backend.
- Do not persist submitted text by default.


## 5. Text Processing Strategy

The planned text-processing mechanism uses an external AI provider through a minimal backend API.

Planned approach:

1. The Chrome extension sends a user-requested text-processing request to the Cloudflare Worker endpoint.
2. The backend validates the request and applies usage limits.
3. The backend calls the selected AI provider using a server-side API credential.
4. The extension displays the result and allows the user to copy it.

The initial AI model candidate is GPT-6 Luna through the OpenAI API.

The model has not yet been approved for production.

Before implementation, verify API availability, actual pricing, correction quality, rewriting quality, supported languages, privacy requirements, and usage controls.

A provider API key must never be embedded in the extension.

Implementation must remain simple and within the $5 API budget for the one-month experiment.


## 6. Initial Project Structure

EFD-TextFix/
├── README.md
├── .gitignore
├── docs/
│   ├── PROJECT_STATUS.md
│   |── TECHNICAL_SPEC.md
│   ├── MODEL_TESTS.md
├── src/
└── tests/

The manifest and other runtime files will be placed in the appropriate location after the extension packaging structure is finalized.

## 7. Quality Requirements

- Clear separation of responsibilities.
- Readable and maintainable code.
- Basic input validation.
- Meaningful error messages.
- Testing of core functionality.
- Minimal permissions.
- No unnecessary collection or transmission of user text.

## 8. Acceptance Criteria

The MVP will be considered ready for initial validation when:

- The extension can be loaded into Chrome in developer mode.
- The interface accepts text.
- The selected text-processing mechanism works as documented.
- The user can copy the processed result.
- Empty input and processing failures are handled appropriately.
- Core functionality has been tested.
- The project documentation matches the implemented behavior.

## 9. Current Status

Day 01 — Project Setup, Planning, and Documentation.

Confirmed:
- Product scope and MVP features.
- JavaScript, HTML5, CSS3, and Chrome Extension Manifest V3.
- One-month MVP experiment.
- $5 total planned API budget.
- Initial global request limit of 300 requests per month.
- Cloudflare Workers + OpenAI API as the proposed architecture.
- GPT-6 Luna as the initial model candidate.

Pending:
- Model availability and quality evaluation.
- Actual API cost verification.
- Final production approval.
- Implementation and testing.
- Privacy policy and launch preparation.

Implementation has not started.


## 10. Initial Architecture Decision — Superseded

**Status: Superseded by Sections 11–15.**

This section documents the original no-backend approach.
It is retained for decision history only and does not represent
the current project architecture.

### Approved Constraints

- Chrome Extension Manifest V3.
- JavaScript, HTML5, and CSS3.
- No custom backend or application database.
- User-triggered text processing only.
- Minimal browser permissions.
- No embedded secret API credentials.

### Proposed Architecture

- Popup UI for text input and results.
- Dedicated grammar-service module for API communication.
- Utility module for text validation and formatting.
- Explicit loading, success, and error states.
- Clipboard functionality initiated by the user.
- External service integration restricted to an approved endpoint.

### External Service Requirements

Before production integration, verify:

- API terms permit the intended extension use.
- Authentication can be implemented securely without a custom backend.
- Rate limits and pricing are acceptable.
- Supported languages meet the MVP requirements.
- Data handling and privacy terms are suitable.
- Grammar correction and text rewriting requirements are covered.


### Outstanding Decisions

- Select a production-approved grammar API.
- Verify commercial usage and redistribution rights.
- Confirm browser-extension CORS compatibility.
- Confirm authentication and API-key handling.
- Verify supported languages, rate limits, and pricing.
- Confirm privacy and text-retention policies.
- Select a compatible text-rewriting solution.

### API Decision Status

No provider has been approved for production integration.

LanguageTool requires further verification of commercial authorization.
APIVerve and GrammarCheck.ai remain candidates pending technical,
commercial, and privacy validation.

Implementation must not begin until the selected integration
satisfies the project's no-backend and security requirements.


## 11. Updated Architecture Decision

### Product Model

EFD TextFix will offer a limited free usage tier.
Users should be able to start using the extension without
creating an account or supplying their own API key, if
the selected provider and abuse-prevention model permit it.

### Architecture

- Chrome Extension: JavaScript, HTML, CSS, Manifest V3.
- Minimal backend/API gateway for secure API access.
- External provider for grammar correction and text improvement.
- API credentials stored on the server, never in extension code.
- Server-side request limits and input validation.
- Provider-side spending limits where available.

### Initial Usage Limits

- Proposed allowance: 20 requests per day per user.
- Proposed maximum input: 5,000 characters.
- Final limits depend on provider pricing and technical validation.

### Privacy and Abuse Prevention

- Do not persist submitted text by default.
- Disclose external text processing in the privacy policy.
- Apply request throttling and abuse controls.
- Do not rely exclusively on client-side counters.
- Do not expose provider credentials to extension users.

### Outstanding Decisions

- Select and verify a production text API.
- Confirm commercial usage terms and pricing.
- Confirm support for correction and rewriting.
- Select a minimal backend deployment approach.
- Define anonymous-user identification and rate limiting.
- Finalize privacy disclosures and usage limits.



## 12. Production API Candidate

### Recommended Stack

- Frontend: Chrome Extension Manifest V3.
- UI: JavaScript, HTML5, CSS3.
- Backend: Cloudflare Workers.
- AI provider candidate: OpenAI API.
- Server-side secret storage for provider credentials.
- Server-side usage limits and input validation.

### MVP Features

- Grammar, spelling, and punctuation correction.
- Text improvement and rewriting.
- Copy processed text.
- Clear loading, success, and error states.

### Initial Usage Policy

- Proposed limit: 20 requests per user per day.
- Proposed maximum input: 5,000 characters.
- No text persistence by default.
- Anonymous access, subject to abuse-prevention validation.
- Enforce usage limits on the server, not only in the extension.

### Cost Controls

- Restrict input and output sizes.
- Select an appropriate low-cost model after evaluation.
- Monitor provider usage and configure available spending controls.
- Establish a maximum acceptable monthly budget before launch.
- Test real requests to estimate cost per operation.

### Security and Privacy

- Never expose provider API keys in extension code.
- Do not log submitted text or generated responses.
- Disclose external AI processing to users.
- Review provider data retention and applicable terms.
- Protect the backend against automated abuse.

### Decision Status

Cloudflare Workers + OpenAI API is the recommended
architecture for evaluation.

Final provider approval is pending cost, quality,
security, and privacy validation.


## 13. API Budget and Cost Controls

### Monthly Budget

- Maximum planned AI API budget: $5 per calendar month.
- Budget covers development, testing, and the first public launch.
- The initial server-side emergency cutoff is set at $4 of tracked API usage.
- Review actual usage before increasing any limits.

### Initial Usage Limits

- Maximum input length: 5,000 characters.
- Maximum requests per user: 20 per day.
- Initial global request limit: 300 requests per month.
- Enforce all limits on the backend.
- Do not rely on client-side counters for cost protection.

### Budget Monitoring

- Alert threshold: $2.50.
- Review threshold: $4.00.
- Stop accepting new paid requests when the backend budget threshold is reached.
- Track actual token usage and estimated API cost per request.
- Do not store submitted text or generated responses in usage logs.

### Provider Spend Controls

- Configure a separate API project for EFD TextFix.
- Enable the strongest available provider spend control.
- Treat provider spend limits as an additional safeguard, not the only safeguard.
- Keep the provider secret exclusively on the server.
- Verify how the provider reports usage and applies spend limits.

### Model Evaluation

- Evaluate a low-cost model candidate for correction and rewriting.
- Test grammar quality, rewriting quality, response time, and token usage.
- Measure the cost of representative short and long texts.
- Approve the production model only after reviewing test results.

### Decision Status

Monthly API budget: $5 — confirmed.

Initial backend cutoff: $4 — proposed.

Global monthly request limit: 300 — provisional.

Production model: pending evaluation.

Implementation: not started.

## 14. One-Month MVP Experiment

### Project Purpose

EFD TextFix is a small, time-limited Chrome Web Store experiment.

Its purpose is to demonstrate EfsunDev's ability to build and publish a useful browser extension, introduce the company to potential users, and gain practical product-launch experience.

This is not a SaaS platform or a long-term commercial service.

### Experiment Duration

- Initial public test period: one month.
- After the test, review results and decide whether to disable, archive, or improve the extension.
- If the backend is disabled, AI features will stop working.
- Do not imply that the service will remain available indefinitely.

### Simplified Architecture

- Chrome Extension using Manifest V3.
- JavaScript, HTML, and CSS for the interface.
- One minimal Cloudflare Worker API endpoint.
- OpenAI API for text correction and rewriting.
- Store the provider API key only on the server.
- No user accounts, database, payment system, or full analytics platform.

### Temporary Usage Limits

- Total planned API budget: $5 for the experiment.
- Maximum input length: 5,000 characters.
- Initial global request limit: 300 requests per month.
- Apply basic server-side request validation and rate limiting.
- Stop accepting paid requests when the internal spending threshold is reached.
- Do not rely on client-side limits alone.

### Privacy

- Do not persist submitted text or generated responses.
- Do not include user text in application logs.
- Disclose external AI processing and the relevant data handling practices.
- Publish an accurate privacy policy before public release.

### Out of Scope

- User accounts and authentication.
- Subscription or payment features.
- Multi-provider AI architecture.
- Complex analytics dashboards.
- Large-scale infrastructure and advanced scalability work.
- Long-term service commitments.

### Completion Criteria

- Correction and rewriting work reliably.
- Users can copy the result.
- API secrets are not exposed in extension code.
- Server-side limits are tested.
- Privacy disclosures and store listing are prepared.
- The extension is ready for a one-month experiment.

### Decision Status

Project scope: simplified one-month MVP.

API budget: $5.

Architecture candidate: Cloudflare Workers + OpenAI API.

Initial global request limit: 300 per month, provisional.

Implementation: not started.

## 15. Initial AI Model Evaluation

### Candidate

- Initial model candidate: GPT-6 Luna.
- Provider: OpenAI API.
- Purpose: text correction and text improvement.
- Status: candidate for testing, not yet approved for production.

### Preliminary Cost Estimate

- Example input: 2,000 tokens.
- Example output: 1,000 tokens.
- Estimated cost per request at published standard rates: approximately $0.0007.
- Estimated cost for 300 requests under these assumptions: approximately $0.21.
- These figures are illustrative and must be validated with actual API usage.

### Test Requirements

Test the candidate with:
- Text containing spelling and grammar errors.
- Text requiring punctuation correction.
- Text requiring clearer wording.
- Text requiring a rewrite while preserving its meaning.
- Short and long inputs.
- English and Russian text.

Evaluate:
- Correction accuracy.
- Preservation of the original meaning.
- Rewrite quality.
- Response time.
- Actual input and output token usage.
- Actual cost per request.

### Approval Rule

Do not approve the model for public use until basic quality tests pass and actual API costs have been reviewed.

Implementation remains not started.