# FacilityBot Agent Skill

Official read-only agent skill for [FacilityBot](https://facilitybot.co), a facility management and CMMS platform.

Use natural language to look up records, summarize maintenance requests, and review facility operations through a connected FacilityBot MCP. The skill supplies workflow instructions; the MCP connection supplies account access. Installing the skill does not connect an account or grant permissions.

## What it helps with

- Review requests using the account's standard and custom statuses.
- Summarize visible requests by location or fault classification.
- Look up assets, checklists, facilities, bookings, requestors, and other supported records.
- Check facility availability for a specified time range.
- Handle pagination, account configuration, and incomplete data explicitly.

Version 1.0.0 supports **read-only workflows**. It does not create requests, change statuses, submit checklists, or create bookings. Record visibility depends on the connected account and its permissions. The skill does not provide access to data outside that connection.

## Before you start

1. Use an AI client that supports Agent Skills and a remote MCP connection.
2. Configure the FacilityBot MCP connection for your intended account and environment using your FacilityBot MCP settings and official setup guidance.
3. Keep the connection credentials in the client's connection settings. Do not put them in this repository or in chat.

The skill does not automatically install or configure the MCP server. The public MCP resource page is planned at `https://facilitybot.co/resources/mcp`; it returned 404 when checked on November 3, 2026. Until that page is published, use your FacilityBot MCP settings or contact FacilityBot support for connection guidance. Do not substitute a UAT endpoint for production.

## Install

### With the Skills CLI

Requires Node.js 22.20 or later. Run from the project where you want the skill installed:

```sh
npx skills add FCBRTH/facilitybot-MCP-agent-skills --skill facilitybot
```

Select your supported AI client when prompted. For more installation options, see the [Skills CLI documentation](https://github.com/vercel-labs/skills).

### Download the ZIP

Download [facilitybot-skill-v1.0.0.zip](https://github.com/FCBRTH/facilitybot-MCP-agent-skills/releases/download/v1.0.0/facilitybot-skill-v1.0.0.zip) from the [v1.0.0 release](https://github.com/FCBRTH/facilitybot-MCP-agent-skills/releases/tag/v1.0.0).

For a client with a custom-skill ZIP uploader, follow that client's instructions and upload the ZIP. For a client using a skills directory, extract and copy the entire `facilitybot/` folder into that directory. Keep `SKILL.md`, `references/`, and `agents/` together. Restart or reload the client if it requires that to discover new skills.

Skill support and installation controls vary by client. An MCP connection alone does not mean the client can load a skill ZIP. If your client does not support Agent Skills, use the repository as reference documentation and follow the client's supported instruction mechanism.

## Example prompts

- "Summarize my open requests by location. State the date range and whether all pages were retrieved."
- "Show the details of request [request ID] and explain its current status."
- "Find the asset named [asset name] and summarize the details available to my account."
- "Check whether [facility name] is available tomorrow from 2 PM to 4 PM in the facility's timezone."

Replace bracketed text with your own record identifiers or names. For overdue or SLA analysis, the assistant must use actual deadlines and status rules available from the account; it must explain when those are missing.

## Package contents

```text
facilitybot/
  SKILL.md
  LICENSE
  agents/openai.yaml
  references/api-capabilities.md
```

See the [read-only endpoint reference](facilitybot/references/api-capabilities.md) for the supported surface. REST operation IDs in that document are reference identifiers; the assistant must discover actual connected tools and their schemas.

## Feedback and maintenance

Report documentation problems through [GitHub Issues](https://github.com/FCBRTH/facilitybot-MCP-agent-skills/issues). Include a description and a sanitized example. Do not include API keys or private operational records. This repository contains skill instructions, not the MCP server implementation.

## License

[MIT](LICENSE). Copyright 2026 FacilityBot.
