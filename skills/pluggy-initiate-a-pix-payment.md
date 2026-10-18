---
name: pluggy-initiate-a-pix-payment
title: Initiate a PIX payment
description: Create a recipient and a payment request, open a payment intent, and track the request to completion.
api: openapi/pluggy-api-openapi.yml
operations:
- payment-recipient-create
- payment-request-create
- payment-intent-create
- payment-request-retrieve
- payment-request-create-pix-qr
generated: '2026-10-18'
method: generated
source: Grounded in openapi/pluggy-api-openapi.yml; every operationId verified verbatim in the spec. Mirrors the official
  skill pluggy-payments (skills/_original/pluggy-payments/SKILL.md).
---

# Initiate a PIX payment

Create a recipient and a payment request, open a payment intent, and track the request to completion.

## Steps

1. Create the payee with `payment-recipient-create` (POST /payments/recipients).
2. Create the request with `payment-request-create` (POST /payments/requests), or `payment-request-create-pix-qr` from a PIX QR code.
3. Open the payer authorization with `payment-intent-create` (POST /payments/intents).
4. Track status with `payment-request-retrieve` (GET /payments/requests/{id}) or payment webhooks.

## Rules

- Authenticate per the spec security scheme (X-API-KEY / x-api-key); keep secrets server-side.
- For live help, connect the hosted docs MCP: `claude mcp add --transport http pluggy-docs https://mcp.pluggy.ai/mcp`.
