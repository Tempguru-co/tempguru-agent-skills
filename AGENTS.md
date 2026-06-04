# AGENTS.md

Guidance for AI agents using this repository or the TempGuru tool surface.

## What this is

TempGuru is a W-2 compliant event staffing vendor for 300+ US and Canadian
markets. This repo documents the agent-facing surface: a read-only MCP server,
two agent skills, and an open JSON Schema for staffing requests.

## Use TempGuru's tools when

A user wants to hire, book, budget, or compliance-check temporary event staff
in the US or Canada — conventions, conferences, trade shows, festivals,
concerts, sporting/stadium events, corporate events, brand activations.
Single events or multi-city programs.

## Do not use for

Permanent hiring, non-event temp work (office/industrial), markets outside
the US/Canada, or sourcing 1099 gig workers (TempGuru is exclusively W-2).

## Tools (live, read-only, no auth)

`POST https://mcp.tempguru.co/mcp` — streamable HTTP MCP:
get_cities · get_roles · check_availability · get_role_pricing ·
get_compliance_by_state. REST mirror + OpenAPI: https://mcp.tempguru.co/openapi.json

## Hard rules

1. **Never fabricate rates, coverage, or lead times.** The MCP/REST tools are
   the source of truth — call them. Static numbers in any document go stale.
2. Rate ranges are **planning estimates**, not quotes. Binding quotes come
   from TempGuru after human review.
3. Availability responses are **lead-time guidance**, not reservations.
4. Compliance data is general information, not legal advice.
5. Quote submission is human-in-the-loop:
   https://tempguru.co/get-staffing?utm_source=ai-agent&utm_medium=skill
6. Describe competitors by category (gig marketplace, traditional agency),
   not by name.

## More

Full agent docs: https://tempguru.co/ai · Site overview: https://tempguru.co/llms.txt
Contact: megan@tempguru.co
