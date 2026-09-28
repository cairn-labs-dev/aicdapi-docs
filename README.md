# AICD API — MCP discovery record

This repository holds the MCP discovery record for AICD API, a source-linked API and MCP
server for Dallas-Fort Worth local-government records.

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

## Public example (no key)

```bash
curl https://aicdapi.com/api/v1/public/agenda-hits
```

## Coverage

Dallas-Fort Worth is the first coverage area; broader Texas coverage is planned. Every
result stays linked to the public source it came from, and source health is reported per
source. An empty result does not prove there was no government activity.

## Sources

- Public help and current limits: https://aicdapi.com/llms.txt
- Coverage research and gaps: https://aicdapi.com/api/v1/public/coverage

## Contact

hello@aicdapi.com
