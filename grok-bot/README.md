# Grok Bot Marketplace Handoff

Status: package ready, external publication and host verification pending

## Listing fields

- Name: GoFaceless
- Publisher: GoFaceless
- Category: Creativity
- Repository: https://github.com/goagentic/gofaceless-agent-plugin
- Website: https://gofaceless.ai
- Support: support@goagentic.com
- Privacy: https://gofaceless.ai/privacy
- Terms: https://gofaceless.ai/terms
- License: MIT
- Icon: `icon.png` (512 by 512 pixels)

Use the description, starter prompts, package paths, and prerequisite states in
`submission.json`. Do not replace the MCP URL or add a Grok-specific backend.

## Submission sequence

1. Build the allowlisted archive from the private source repository.
2. Compare the reported SHA-256 digest with the reviewed artifact.
3. Create the dedicated public repository named above from only the archive
   contents. Do not publish the containing GoFaceless repository.
4. Validate `plugin.json`, `mcp.json`, the skill, links, icon, license, support
   contact, and repository visibility from a signed-out browser.
5. Submit the repository through the Grok Bot or Cursor plugin marketplace
   process under the GoFaceless publisher identity.
6. Install the reviewed listing into a clean Grok Bot account and complete all
   fixed tasks in `test-cases.json` with generation disabled or mocked.
7. Record OAuth link, refresh, both revocation layers, fresh reconnect,
   review-only tool discovery, duplicate authorization, interrupted monitoring,
   and scoped revision evidence in the private readiness ledger.

Repository creation, marketplace submission, and any paid-provider canary are
external actions. They must not be inferred from building this package.

## Acceptance boundary

Marketplace acceptance proves distribution, not service authorization. The
host must use OAuth, and GoFaceless continues to enforce organization access,
profile-specific tool visibility, current-state approvals, cost ceilings,
idempotency, generation gates, exports, and delivery server-side.
