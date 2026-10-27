# EFD TextFix

EFD TextFix is a lightweight Chrome extension developed by EfsunDev to help users correct and improve written text.

## Project Goals

The goal of EFD TextFix is to provide a simple, convenient, and professional tool for improving text directly in the browser.

This project is a one-month MVP experiment designed to validate the product concept, test the Chrome Web Store launch process, and gain practical experience delivering a software product.

## MVP Features

- Correct spelling, grammar, and punctuation.
- Improve and rewrite text.
- Copy processed text to the clipboard.
- Provide a clean and intuitive user interface.
- Display loading, success, and error states.

## Technology Stack

- JavaScript
- HTML5
- CSS3
- Chrome Extension Manifest V3
- Cloudflare Workers — proposed minimal backend
- OpenAI API — proposed AI provider

The AI model and final production configuration have not yet been approved.

## Architecture

The planned architecture consists of a Chrome extension communicating with a minimal Cloudflare Worker API endpoint, which will securely call the selected AI provider.

API credentials must remain server-side and must never be embedded in the extension's source code.

The backend will provide basic request validation and abuse prevention.

The project will avoid unnecessary complexity. User accounts, a database, payments, and advanced infrastructure are outside the initial MVP scope.

## Budget and Limits

- Total planned API budget: $5 for the one-month experiment.
- Proposed internal stop threshold: $4.
- Initial global request limit: 300 requests per month.
- Maximum input length: 5,000 characters.
- Proposed per-user limit: 20 requests per day.

These limits must be enforced and verified appropriately during implementation.

## Privacy Principles

- Do not persist submitted text by default.
- Do not include user text in application logs.
- Keep API credentials server-side.
- Clearly disclose how text is processed and shared.
- Prepare an appropriate privacy policy before public release.

## Project Structure

- `src/` — extension source code.
- `tests/` — project tests.
- `docs/` — technical documentation and project status.
- `manifest.json` — planned Chrome extension configuration.

## Development Principles

- Keep the architecture simple and maintainable.
- Implement features incrementally.
- Validate each development stage before proceeding.
- Follow Chrome Extension Manifest V3 requirements.
- Minimize permissions and prioritize user privacy.
- Do not begin implementation until the initial model evaluation requirements have been reviewed.

## Project Status

Day 01 — Project Setup, Planning, and Documentation.

The MVP scope, preliminary architecture, budget constraints, and initial AI model candidate have been documented.

The initial model candidate is GPT-6 Luna. It has not yet been tested or approved for production.

Implementation has not started.


## Copyright and License

Created by **Arslon Erkinov**.

Copyright © 2026 Arslon Erkinov and EfsunDev. All rights reserved.

EFD TextFix is proprietary software. Copying, redistribution, modification, or commercial use of its proprietary source code requires prior written permission from the rights holder, except where applicable law provides otherwise.

See [LICENSE.txt](LICENSE.txt) for the full license terms.

Third-party components remain subject to their respective licenses.