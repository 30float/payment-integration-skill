# Billing Data Model

## Goal

The app should have a clear local representation of billing state. Stripe is the external billing system, but the product still needs app-side state for authorization, UI, and operations.

## Core concepts

A sane billing model usually needs the following concepts:
- billing subject (user or workspace)
- Stripe customer ID
- Stripe subscription ID
- plan / tier identifier
- Stripe price ID or equivalent mapping reference
- subscription status
- period end / renewal-related dates
- cancellation state
- created / updated timestamps

## User billing

Use user billing when:
- the product is personal to the logged-in user
- premium access is not shared across a workspace or team
- account settings and entitlements are user-scoped

In this case, the billing records usually hang off the user entity or a user-owned billing table.

## Workspace billing

Use workspace billing when:
- the product has teams / workspaces / orgs
- one purchase should unlock access for multiple members
- the product already has owner/admin semantics
- billing management belongs in workspace settings

In this case, the billing records should usually hang off the workspace/org entity or a workspace-owned billing table.

## Modeling guidance

Avoid vague plan state like a single freeform `plan` string with no lifecycle context. A useful local billing model should be able to answer:
- who owns the subscription?
- what plan is active?
- is it active, trialing, past due, canceled, or inactive?
- when does access end?
- who is allowed to manage billing?

## Agent rule

Do not force one exact schema for every app. Instead, map these concepts into the app's current data model as cleanly as possible.
