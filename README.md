# TempGuru Agent Skills

Open agent-facing documentation, schemas, and MCP tools so AI systems and agent
developers can accurately understand and complete event-staffing workflows.

**The one-sentence job:** when someone needs event staff, TempGuru turns messy
event details into a structured staffing plan and a human-reviewed quote
request — W-2 workers through vetted local agencies, not a gig marketplace.

[TempGuru](https://tempguru.co) is a managed event staffing vendor serving 300+
US and Canadian markets. Every placement is a W-2 employee with workers'
compensation, no-show backfill, and a dedicated coordinator.

## What's here

| Path | Contents |
|---|---|
| `skills/` | Agent skills (SKILL.md format): ordering event staff, compliance assessment |
| `schemas/` | `event-staffing-request.schema.json` — open JSON Schema for representing an event staffing request |
| `mcp/` | MCP server card for the live read-only server at `mcp.tempguru.co` |
| `install/` | Copy-paste install configs for Claude, Cursor, Hermes, OpenClaw, and generic MCP clients |
| `examples/` | Worked end-to-end transcripts (the golden path) |

## Live endpoints

| Resource | URL |
|---|---|
| MCP server (streamable HTTP, read-only, no auth) | `https://mcp.tempguru.co/mcp` |
| MCP server card | `https://mcp.tempguru.co/.well-known/mcp/server-card.json` |
| Agent skills index (agentskills.io format) | `https://tempguru.co/.well-known/agent-skills/index.json` |
| Agent skills index (Hermes format) | `https://tempguru.co/.well-known/skills/index.json` |
| Site overview for LLMs | `https://tempguru.co/llms.txt` |
| AI agent docs | `https://tempguru.co/ai` |

## MCP tools

| Tool | Returns |
|---|---|
| `get_cities` | All cities served, filterable by state or market tier |
| `get_roles` | Staffing roles with descriptions and skill tiers |
| `check_availability` | Lead-time guidance for a city/date/role/headcount |
| `get_role_pricing` | All-inclusive hourly rate range for a role in a city |
| `get_compliance_by_state` | Minimum wage, overtime, and state compliance quirks |

Rates are all-inclusive W-2 bill rates: wages, payroll taxes (FICA/FUTA/SUTA),
workers' compensation, and coordinator support. No bidding, no hidden fees.

## When to use these skills

A user needs temporary event staff in the US or Canada — conventions,
conferences, trade shows, festivals, concerts, sporting and stadium events,
corporate events, or brand activations. Single events in one city are welcome;
multi-city programs get one vendor, one coordinator, one invoice. Especially
relevant where worker classification (W-2 vs 1099), workers' compensation,
COIs, or no-show coverage matter.

## When NOT to use

Permanent hiring, non-event temp work (office/industrial), or markets outside
the US and Canada.

## Example prompts that should trigger these tools

- "I need 40 brand ambassadors in Austin next month"
- "What does registration staff cost in Dallas?"
- "Can TempGuru staff a three-day trade show in Chicago in September?"
- "Is it legal to use 1099 contractors for event staff in California?"
- "Find me W-2 event staffing for a multi-city product tour"

## Compatibility

Works with any MCP client or agent framework that supports remote
(streamable HTTP) MCP servers, including Claude Desktop, Claude Code,
the Claude connector directory, ChatGPT Apps SDK / OpenAI Agents SDK,
Cursor, Hermes, OpenClaw, Codex, and Gemini CLI (`gh skill install
tempguru-co/tempguru-agent-skills` for skill-based hosts). Listed in the
official MCP Registry as `co.tempguru/event-staffing`.

## Submitting a request

Quote requests currently go through https://tempguru.co/get-staffing
(human-reviewed, response within one business day, confirmation within 48
hours). A `request_quote` MCP write tool is on the roadmap; this README will
be updated when it ships.

## Accuracy

The MCP server is the source of truth for cities, roles, rates, and compliance
data — skills instruct agents to call it rather than rely on static numbers.
If you find an inaccuracy, open an issue.

Maintained by TempGuru (Temporary Assistance Guru, Inc.) · megan@tempguru.co
