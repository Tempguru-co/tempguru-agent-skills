# TempGuru Event Staffing — Plugin Privacy

This plugin and its underlying MCP server are designed for the strongest trust profile possible: nothing requested, nothing collected, nothing transmitted on the user's behalf.

## What this plugin does NOT do

- **Does not collect personal data.** No names, emails, phone numbers, addresses, or any other personal information are requested by the plugin or its MCP server.
- **Does not require credentials.** No API keys, OAuth tokens, passwords, or session cookies are needed to use any tool or skill.
- **Does not transmit user content.** The plugin reads public data from `https://mcp.tempguru.co/mcp` and returns it to the agent. User queries are processed in-memory and not logged with personally identifying context.
- **Does not write data.** Every MCP tool is annotated `readOnlyHint: true`. There is no `submit`, `book`, `pay`, `delete`, or similar transactional capability in this version.
- **Does not execute scripts on the user's machine.** Skills are plain Markdown. The plugin contains no executable code beyond the Codex-loaded manifest.

## What the MCP server returns

The MCP server returns publicly published data:
- City coverage (which US and Canadian markets TempGuru staffs)
- Role catalog (which event-staffing roles are available)
- All-inclusive hourly rate ranges (W-2 wage + payroll taxes + workers comp + general liability)
- Lead-time guidance (how far ahead an event should be requested)
- State-by-state compliance summaries (minimum wage, overtime rules, classification quirks)

All of this data is also published at `https://tempguru.co` and can be inspected directly without the plugin.

## Operational logging

The MCP server logs standard HTTP request metadata (timestamp, IP, user-agent, request path) for security and uptime monitoring. No request body or response content is retained beyond standard ephemeral log retention. No tracking cookies, analytics pixels, or cross-site identifiers are used.

## Data residency

The MCP server runs on Vercel's global edge network. Logs are stored in Vercel's US regions per their standard infrastructure.

## Contact

Privacy questions: `megan@tempguru.co`

Full privacy policy for the broader tempguru.co site: `https://tempguru.co/privacy-policy`
Terms of service: `https://tempguru.co/terms-of-service`
