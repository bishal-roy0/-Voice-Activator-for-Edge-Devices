# Security policy

## Reporting a vulnerability

Do not open a public issue for exposed credentials, a device security problem, or another sensitive vulnerability. Contact the project leader privately and include the affected component, impact, and safe reproduction details.

## Secret handling

- Keep Wi-Fi passwords, tokens, API keys, and private certificates out of Git.
- Use local environment files or secure device provisioning for development credentials.
- Commit only documented placeholders such as `YOUR_SERVER_URL`.
- If a secret is committed, revoke or rotate it immediately, remove it from history with the project leader, and document the remediation privately.
