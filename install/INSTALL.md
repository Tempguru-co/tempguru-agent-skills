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
