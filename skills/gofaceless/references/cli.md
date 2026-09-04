# GoFaceless CLI contract

Use `--json` for machine-readable stdout. Diagnostics and errors go to stderr.
Use `--no-input` in automation. `--wait N` bounds only local polling; Ctrl-C does
not cancel the durable server operation.

```bash
gofaceless auth login
gofaceless auth login --device
gofaceless auth status --json
gofaceless auth logout --json
gofaceless capabilities --json
gofaceless sessions list --json
gofaceless sessions get --session SESSION_ID --json
gofaceless sessions start --goal GOAL --request-id REQUEST_ID --json
gofaceless sessions instruct --session SESSION_ID --instruction TEXT \
  --turn-id TURN_ID --scene SCENE_ID --accept CRITERION --json
gofaceless sessions decide --session SESSION_ID --action ACTION_ID \
  --state-version STATE_VERSION --decision approve --decision-id DECISION_ID --json
gofaceless media add --session SESSION_ID --file PATH \
  --state-version STATE_VERSION --request-id REQUEST_ID \
  --purpose style_reference --confirm-rights --json
printf '%s' "$SIGNED_REFERENCE_URL" | gofaceless media add --session SESSION_ID \
  --url-stdin --state-version STATE_VERSION --request-id REQUEST_ID \
  --purpose video_reference --confirm-rights --json
gofaceless preview render --session SESSION_ID --state-version STATE_VERSION \
  --request-id REQUEST_ID --confirm-render --json
gofaceless changes undo --session SESSION_ID --state-version STATE_VERSION \
  --request-id REQUEST_ID --confirm-undo --json
gofaceless operations get --operation OPERATION_ID --json
gofaceless export --session SESSION_ID --action ACTION_ID \
  --state-version STATE_VERSION --request-id REQUEST_ID \
  --confirm-final-delivery --json
```

Browser PKCE is the default. Use `--device` only if discovery advertises a device
authorization endpoint. Otherwise use browser login or a scoped
`GOFACELESS_API_KEY` supplied by the environment/secret manager. Never accept or
suggest `--api-key`. `auth status` reports only non-secret connection metadata.
`auth logout` removes stored OAuth credentials; it reports when an environment
API key remains active because a process cannot erase its parent environment.
The CLI discovers the authorization server from the MCP resource's protected-
resource metadata and validates both the resource and issuer. Pilot builds may
require a reviewed `GOFACELESS_OAUTH_CLIENT_ID`; users should not invent an
issuer or paste credentials into configuration.

Exit codes are stable: `0` success, `1` terminal failure, `2` usage/input, `3`
authentication, `4` permission/scope/entitlement, `5` state/idempotency conflict,
`6` retryable failure, and `7` approval or explicit confirmation required.

For a retry, reuse the original request/turn ID and byte-identical input. If any
goal, instruction, target, file, decision, or state version changes, use a new ID.
A public query-free URL may use `--url`; any signed or query-bearing URL must use
`--url-stdin` so the credential never appears in the process list or shell history.
