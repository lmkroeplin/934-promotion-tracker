# 934 Promotion Tracker

## Stack
Static HTML — promotion eligibility dashboard

## CI/CD Rules
- Always include a `.github/workflows/ci.yml` when scaffolding or significantly modifying this project
- CI runs: html-validate, axe-core accessibility checks
- All new linting/validation steps should use `continue-on-error: true` initially
- This project deploys to Cloudflare Pages — never break the push-to-deploy pipeline
- Include axe-core accessibility checks for all HTML output
