# Example: Next.js + Supabase + Stripe Subscriptions

## Scenario

A Next.js SaaS app uses Supabase Auth and Postgres. The app has user accounts, no true team/workspace concept, and wants to add a paid Pro plan with monthly and yearly billing.

## What the agent should detect

- Next.js app
- Supabase Auth
- user-centric product
- likely account settings entry point
- no existing Stripe integration

## Recommended direction

- classify as **in-scope**
- recommend **user-based billing**
- use **Stripe Checkout** for plan acquisition
- use **Stripe Customer Portal** for self-serve billing management
- sync Stripe customer/subscription state into user-owned billing fields or a user billing table
- gate Pro features using app-side entitlement state

## Key questions to ask

- monthly, yearly, or both?
- free trial or no?
- what exactly does Pro unlock?
- what should happen on cancellation or subscription lapse?
- are Stripe test keys already available?
