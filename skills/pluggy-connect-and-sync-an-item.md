---
name: pluggy-connect-and-sync-an-item
title: Connect a bank account (Item) and keep it synced
description: Authenticate with Pluggy, mint a Connect Token for the Connect Widget, follow the Item through MFA to a synced
  state, and subscribe to webhooks.
api: openapi/pluggy-api-openapi.yml
operations:
- auth-create
- connect-token-create
- items-retrieve
- items-send-mfa
- items-update
- webhooks-create
generated: '2026-10-18'
method: generated
source: Grounded in openapi/pluggy-api-openapi.yml; every operationId verified verbatim in the spec. Mirrors the official
  skill pluggy-integration (skills/_original/pluggy-integration/SKILL.md).
---

# Connect a bank account (Item) and keep it synced

Authenticate with Pluggy, mint a Connect Token for the Connect Widget, follow the Item through MFA to a synced state, and subscribe to webhooks.

## Steps

1. `auth-create` (POST /auth) with clientId + clientSecret returns an API key; send it as the `X-API-KEY` header on every other call. It has no security requirement itself.
2. `connect-token-create` (POST /connect_token) mints a short-lived token for the frontend Connect Widget; never ship the API key to a browser.
3. After the user connects, poll `items-retrieve` (GET /items/{id}) or rely on webhooks; when the Item status is WAITING_USER_INPUT submit the code with `items-send-mfa` (POST /items/{id}/mfa).
4. `items-update` (PATCH /items/{id}) triggers a refresh / credential update.
5. Register a receiver with `webhooks-create` (POST /webhooks) instead of polling.

## Rules

- Authenticate per the spec security scheme (X-API-KEY / x-api-key); keep secrets server-side.
- For live help, connect the hosted docs MCP: `claude mcp add --transport http pluggy-docs https://mcp.pluggy.ai/mcp`.
