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

## ChatGPT (custom connector — Pro/Business, developer mode)

Settings → Connectors → enable Developer mode → Create → paste
`https://mcp.tempguru.co/mcp` → No authentication.

## Perplexity (custom connector — Pro/Max/Enterprise)

Settings → Connectors → Add connector → paste
`https://mcp.tempguru.co/mcp` → authentication: Open (none). Org admins
can share the connector organization-wide.

## Gemini CLI (extension)

```
gemini extensions install https://github.com/tempguru-co/tempguru-agent-skills
```

## Manual (any agent that reads SKILL.md)

Fetch the skill directly:

```
https://tempguru.co/.well-known/agent-skills/event-staffing-ordering/SKILL.md
```
