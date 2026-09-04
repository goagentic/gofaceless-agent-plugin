# GoFaceless OpenAI Plugin Submission Snapshot

This directory freezes the review material for the GoFaceless app-plus-skill
plugin. It contains no credentials, challenge token, private prompt, customer
identifier, signed media URL, or reviewer password.

The current snapshot is deliberately `pre_submission`: the reviewed production
MCP endpoint and public postflight are verified, while the portal-controlled and
reviewer prerequisites below remain pending. Before copying it into the OpenAI
Platform submission portal:

1. **Verified July 22:** the reviewed MCP adapter is deployed at
   `https://mcp.gofaceless.ai/mcp`; production health, narrow OpenAPI, protected
   resource metadata, OAuth challenge, and untrusted-Origin rejection pass.
2. Set one portal-generated challenge token in the MCP service environment and
   verify that `/.well-known/openai-apps-challenge` returns only that token as
   plain text with `Cache-Control: no-store`. Never commit or pass the token as a
   CLI argument. The secret-safe readiness command is
   `python3 scripts/check_mcp_launch_readiness.py --target remote --deployment production --require-openai-domain-challenge`;
   it reads `GOFACELESS_OPENAI_APPS_CHALLENGE_TOKEN` from the process environment
   and prints only pass/fail.
3. Scan Tools in the portal. Compare every discovered name, description, input
   and output schema, security scheme, `_meta` field, CSP domain, and annotation
   with the release revision. Server metadata is authoritative.
4. Create a least-privilege reviewer organization with sanitized fixture data
   and adequate test credits. Provide credentials through the portal only. They
   must work outside private networks without MFA, SMS, or email confirmation.
5. Run exactly the five positive and three negative cases in
   `test-cases.json` on ChatGPT web and mobile. Store only sanitized report
   references in `docs/mcp-launch-evidence.json`.
6. Capture optional screenshots only from the production MCP App using
   synthetic data. Check that no token, signed URL, private prompt, source URL,
   filename, or internal identifier is visible.
7. Verify the public website, support, privacy, and terms URLs and the selected
   publisher identity. Select only countries where product, support, and legal
   readiness have been approved.

The official preparation and portal fields are documented in OpenAI's
[plugin submission guide](https://developers.openai.com/codex/submit-plugins)
and [Apps SDK submission guide](https://developers.openai.com/apps-sdk/deploy/submission).
