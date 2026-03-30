# Example: Next.js + Prisma + Stripe Subscriptions

## Scenario

A Next.js app uses Prisma with Postgres. It has user accounts and a settings area. The founder wants a single paid plan and wants a plan-first recommendation before any coding starts.

## What the agent should detect

- Next.js app
- Prisma schema and migration flow
- likely user-centric billing model
- no or minimal existing payment traces

## Recommended direction

- classify as **in-scope**
- recommend **user-based billing** unless the product model reveals shared workspace access
- create a centralized plan/price config
- add server-side checkout session creation
- add server-side billing portal session creation
- verify webhooks and sync customer/subscription state into the local data model

## Planning emphasis

The agent should produce a concrete implementation plan before making schema or route changes.
