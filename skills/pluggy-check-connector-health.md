---
name: pluggy-check-connector-health
title: Check Pluggy connector and platform health
description: Read the public status JSON to tell whether a failure is on the provider side before debugging an Item.
api: openapi/pluggy-status-api-openapi.yml
operations:
- status-snapshot
- status-connector-incidents
- status-summary
generated: '2026-10-18'
method: generated
source: Grounded in openapi/pluggy-status-api-openapi.yml; every operationId verified verbatim in the spec.
---

# Check Pluggy connector and platform health

Read the public status JSON to tell whether a failure is on the provider side before debugging an Item.

## Steps

1. No authentication; base URL https://status.pluggy.ai.
2. `status-connector-incidents` (GET /api/connectors-incidents) lists what is broken right now keyed by connector id; `status-snapshot` and `status-summary` give the full and summarised state.
3. The MCP tool `check_incidents` reads the same source.

## Rules

- Authenticate per the spec security scheme (X-API-KEY / x-api-key); keep secrets server-side.
- For live help, connect the hosted docs MCP: `claude mcp add --transport http pluggy-docs https://mcp.pluggy.ai/mcp`.
