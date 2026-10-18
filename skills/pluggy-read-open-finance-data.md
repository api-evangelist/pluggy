---
name: pluggy-read-open-finance-data
title: Read accounts, transactions, investments and identity for an Item
description: Given a synced Item, list its accounts and balances, page through transactions with the cursor endpoint, and
  read investments, loans and identity.
api: openapi/pluggy-api-openapi.yml
operations:
- accounts-list
- account-balance-get
- transactions-list-by-cursor
- investments-list
- loans-list
- identity-find-by-item
generated: '2026-10-18'
method: generated
source: Grounded in openapi/pluggy-api-openapi.yml; every operationId verified verbatim in the spec. Mirrors the official
  skill pluggy-open-finance (skills/_original/pluggy-open-finance/SKILL.md).
---

# Read accounts, transactions, investments and identity for an Item

Given a synced Item, list its accounts and balances, page through transactions with the cursor endpoint, and read investments, loans and identity.

## Steps

1. `accounts-list` (GET /accounts?itemId=) returns the Item's accounts; `account-balance-get` (GET /accounts/{id}/balance) the current balance.
2. Prefer `transactions-list-by-cursor` (GET /v2/transactions, params accountId, dateFrom, dateTo, createdAtFrom, after) and follow the `after` cursor until exhausted.
3. `investments-list`, `loans-list` and `identity-find-by-item` read the other products by itemId.

## Rules

- Authenticate per the spec security scheme (X-API-KEY / x-api-key); keep secrets server-side.
- For live help, connect the hosted docs MCP: `claude mcp add --transport http pluggy-docs https://mcp.pluggy.ai/mcp`.
