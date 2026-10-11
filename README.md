# AICD API — civic records API and MCP server for AI agents

AICD API gives AI agents and developers source-linked local-government records for
Dallas-Fort Worth, Texas: classified city council and commissioners court agenda items,
meeting cadence, and per-source health. Every result links back to the public government
page it came from. It is available as a REST API and as a remote MCP server.

- Website: https://aicdapi.com
- MCP setup guide: https://aicdapi.com/help/mcp-setup
- API reference: https://aicdapi.com/api-reference

## MCP endpoint

```
https://aicdapi.com/api/v1/mcp
```

Streamable HTTP transport, authenticated with `Authorization: Bearer <AICD API key>`.
Follow the setup guide at https://aicdapi.com/help/mcp-setup for client configuration.

## REST quickstart

No key needed for the public routes:

```bash
# Recent classified Dallas zoning agenda hits, each with meetingAt and sourceUrl
curl --fail --silent --show-error \
  'https://aicdapi.com/api/v1/public/agenda-hits?jurisdictionSlug=dallas&topicSlug=zoning'

# Dated DFW coverage catalog and known gaps
curl --fail --silent --show-error \
  'https://aicdapi.com/api/v1/public/coverage?limit=10'
```

With an API key (create one at https://aicdapi.com/account; see
https://aicdapi.com/help/api-keys):

```bash
curl --fail --silent --show-error \
  --header "Authorization: Bearer $AICD_API_KEY" \
  https://aicdapi.com/api/v1/data/health
```

## This repository

This repository also holds the MCP discovery record for AICD API.

- `server.json` — the record for the remote MCP server, following the official MCP
  Registry `server.json` schema (revision `2025-12-11`). Registry name:
  `com.aicdapi/records`.

The record is served by AICD API at `https://aicdapi.com/server.json`, with a
byte-identical, non-normative convenience alias at
`https://aicdapi.com/.well-known/mcp.json`; the alias path is not part of any adopted MCP
discovery standard. It is published in the Official MCP Registry — entry:
https://registry.modelcontextprotocol.io/v0.1/servers/com.aicdapi%2Frecords/versions/1.0.0

## Connection

- Transport: Streamable HTTP at `https://aicdapi.com/api/v1/mcp`
- Authentication: full header value `Authorization: Bearer <AICD API key>`. Keys start
  with `aicd_`, and the account needs current paid access for the civic tools. Create
  and revoke keys at https://aicdapi.com/help/api-keys.
- Setup guide: https://aicdapi.com/help/mcp-setup
- Full API and MCP reference: https://aicdapi.com/api-reference
- Agent index: https://aicdapi.com/llms.txt

## Tools

| Tool | Purpose |
| --- | --- |
| `search_agenda` | Find ranked civic agenda records |
| `get_agenda_item` | Read one agenda record by id |
| `get_coverage` | Check supported source health |
| `report_missing_data` | Report a missing public record |
| `get_data_report` | Read a missing-data report status |

## Coverage

Dallas-Fort Worth is the first coverage area; broader Texas coverage is planned. Every
result stays linked to the public source it came from, and source health is reported per
source. An empty result does not prove there was no government activity.

## Sources

- Public help and current limits: https://aicdapi.com/llms.txt
- Coverage research and gaps: https://aicdapi.com/api/v1/public/coverage

## Contact

hello@aicdapi.com
