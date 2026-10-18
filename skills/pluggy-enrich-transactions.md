---
name: pluggy-enrich-transactions
title: Categorize and analyse transactions with the Enrichment API
description: Send raw transactions to the Enrichment API for categorization, behaviour analysis and recurring-payment detection.
api: openapi/pluggy-enrichment-api-openapi.yml
operations:
- categorize
- behavior-analysis
- recurring-payments
generated: '2026-10-18'
method: generated
source: Grounded in openapi/pluggy-enrichment-api-openapi.yml; every operationId verified verbatim in the spec.
---

# Categorize and analyse transactions with the Enrichment API

Send raw transactions to the Enrichment API for categorization, behaviour analysis and recurring-payment detection.

## Steps

1. Base URL https://enrichment-api.pluggy.ai, `x-api-key` header.
2. `categorize` (POST /categorize) assigns categories; `behavior-analysis` (POST /behavior-analysis) summarises spending behaviour; `recurring-payments` (POST /recurring-payments) detects recurring charges.

## Rules

- Authenticate per the spec security scheme (X-API-KEY / x-api-key); keep secrets server-side.
- For live help, connect the hosted docs MCP: `claude mcp add --transport http pluggy-docs https://mcp.pluggy.ai/mcp`.
