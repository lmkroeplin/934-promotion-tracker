# 934 Promotion Tracker

## Purpose
934th CES Promotion Eligibility Worksheet & Dashboard for Air Force Reserve personnel tracking.

## Stack
- **Type:** Static HTML site
- **Assets:** HTML, research documents, implementation specs

## Architecture
- Static HTML files at root
- `BUILD_TASK.md`, `IMPLEMENTATION_SPEC.md` for project specs

## CI/CD
CI runs on push/PR to `main`: html-validate, axe-core accessibility. All steps use `continue-on-error: true`.

## Testing
No test suite — CI validates HTML structure and accessibility automatically.

## Deploy
Pushes to `main` auto-deploy via Cloudflare Pages.
