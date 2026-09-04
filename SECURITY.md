# Security Policy

## Report a vulnerability

Do not open a public issue for a suspected vulnerability or include customer
data, credentials, signed media URLs, private prompts, or provider payloads in a
report. Email support@goagentic.com and state that the message is a security
report.

Include only the minimum information needed to reproduce the problem safely.
GoFaceless support will provide a private channel if additional sensitive
evidence is required.

## Authentication

The hosted MCP server uses OAuth. Users should never paste an API key, access
token, refresh token, or authorization code into an agent conversation, URL,
issue, or log.

## Authorization boundary

Host tool visibility is not authorization. GoFaceless independently enforces
organization membership, connector grants, state-bound approvals, credit
ceilings, idempotency, generation switches, export permissions, and delivery
permissions on every request.

## Supported package

Only packages installed from the reviewed marketplace listing or an exact
GoFaceless release should be treated as supported. Do not install modified
packages that redirect `mcp.json` to another host.
