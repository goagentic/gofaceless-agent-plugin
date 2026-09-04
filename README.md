# GoFaceless Agent Plugin

Create, quote, authorize, monitor, retrieve, and revise durable GoFaceless
videos from an AI agent.

This package uses the open Agent Plugins 1.0 format. It contains one shared
GoFaceless skill and one remote Streamable HTTP MCP connection. The same package
can be used by Grok Bot and other compatible agent clients.

## What the plugin does

- Starts supervised GoFaceless video sessions.
- Reads server-authored cost quotes before paid generation.
- Submits only the exact action and state version the user authorizes.
- Monitors durable operations without holding a host conversation open.
- Retrieves previews and native editor links.
- Sends scoped revisions while preserving accepted parts of a video.

The plugin does not implement video generation itself. GoFaceless remains
authoritative for account access, organization isolation, typed video plans,
billing, credit ceilings, provider routing, rendering, quality evaluation,
retries, export, and delivery.

## Install

Install GoFaceless from the host's reviewed plugin marketplace. When prompted,
connect your GoFaceless account through OAuth. Never paste an API key or access
token into an agent conversation.

The package connects only to:

```text
https://mcp.gofaceless.ai/mcp
```

New connections should begin with the review-only profile. Create/edit and
delivery access are separate GoFaceless grants.

## Example

> Create a supervised 30-second portrait video about three ways a bakery can
> reduce food waste. Show me the quote before I authorize Generate.

The agent creates one durable session, reads the server-authored quote, and
stops before provider spend. If you authorize Generate for the displayed
amount, it submits the exact pending action and continues monitoring the same
session.

## Package structure

```text
plugin.json                         Agent Plugins 1.0 manifest
mcp.json                            Portable remote MCP configuration
icon.png                            Approved 512 by 512 marketplace icon
assets/icon.png                     Codex marketplace copy of the same icon
skills/gofaceless/SKILL.md          Agent workflow and safety contract
.codex-plugin/plugin.json           Codex-compatible manifest
.mcp.json                           Codex-compatible MCP configuration
```

See `grok-bot/README.md` for the marketplace handoff and
`grok-bot/test-cases.json` for the fixed acceptance tasks.

The release archive is built from an explicit public-file allowlist with
`python3 scripts/build_gofaceless_agent_plugin_release.py` in the private source
repository. The build rejects unreviewed files and produces a deterministic
archive for marketplace review.

## Support and security

- Support email: support@goagentic.com
- Support page: https://gofaceless.ai/support
- Privacy: https://gofaceless.ai/privacy
- Terms: https://gofaceless.ai/terms
- Security reports: see [SECURITY.md](SECURITY.md)

This Agent Plugin package is available under the MIT License. That license
applies only to the files distributed in this plugin package. It does not apply
to the private GoFaceless application, backend, session agent, prompts, billing,
provider routing, rendering, quality, infrastructure, or other service code.
