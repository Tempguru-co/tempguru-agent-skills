# Install TempGuru Agent Tools

## Claude Desktop / Claude Code (MCP)

Add to `claude_desktop_config.json` (Desktop) or run `claude mcp add` (Code):

```json
{
  "mcpServers": {
    "tempguru": {
      "type": "http",
      "url": "https://mcp.tempguru.co/mcp"
    }
  }
}
```

## Cursor (MCP)

`.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "tempguru": { "url": "https://mcp.tempguru.co/mcp" }
  }
}
```

## Generic MCP client

Streamable HTTP transport, no authentication:

```yaml
mcp_servers:
  tempguru:
    url: "https://mcp.tempguru.co/mcp"
```

## Hermes (skills)

```
hermes skills search https://tempguru.co --source well-known
hermes skills install well-known:https://tempguru.co/.well-known/skills/event-staffing-ordering
hermes skills install well-known:https://tempguru.co/.well-known/skills/event-staffing-compliance
```

## OpenClaw (ClawHub)

```
clawhub install tempguru-event-staffing
```

(If not yet listed on ClawHub, copy `skills/event-staffing-ordering/` into your
OpenClaw `./skills/` directory and restart the session.)

## Manual (any agent that reads SKILL.md)

Fetch the skill directly:

```
https://tempguru.co/.well-known/agent-skills/event-staffing-ordering/SKILL.md
```

## Troubleshooting

### "This connector has no tools available" (Claude.ai or Claude Desktop)

Almost always means the client sent `Accept: application/json` instead of
the `Accept: application/json, text/event-stream` that MCP spec rev
2025-03-26 requires. The TempGuru server normalizes Accept headers
automatically — if you still see this, hard-refresh the Connectors page
(claude.ai) or fully quit + relaunch (Claude Desktop). Reconnect the
server. The 5 tools should appear under "Read-only tools."

### Tools are listed but every call returns an error

Check the MCP server status directly:

```bash
curl -X POST https://mcp.tempguru.co/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

Expected: an SSE stream containing 5 tools. Any other response means
the server is degraded — please open a GitHub issue and include the
output.

### `check_availability` returns "InvalidDate"

The `date` argument must be parseable by JavaScript's `Date()`. Prefer
ISO 8601 (`2026-09-15`). Strings like "next Tuesday" are NOT parsed —
the agent should resolve relative dates before calling.

### `get_role_pricing` returns "RolePricingNoData" for a known city

Pricing is published for cities in TempGuru's coverage map. Cities not
yet in the matrix return this status — the city is still serviceable
on a custom basis. Have the agent surface the message verbatim and
offer to escalate via the contact form on tempguru.co.

### `get_compliance_by_state` returns generic language

State summaries are deliberately conservative and brief. They are NOT
legal advice. For binding interpretation the user must consult
employment counsel — the tool description says so explicitly; surface
that disclaimer when presenting compliance content.

### Skill not auto-invoking in Claude Desktop / Claude Code

Skills only fire when the user's message contains trigger keywords from
the SKILL.md `description` frontmatter (event staffing, brand
ambassadors, W-2 vs 1099, etc.). If the user's phrasing is far from
those triggers, the skill stays dormant by design — the agent will fall
back to the MCP tools directly.

### Where to file issues

GitHub: https://github.com/kissmyabs32/tempguru-agent-skills/issues
Email:  megan@tempguru.co
