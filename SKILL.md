---
name: payment-integration-skill
description: Plan and implement Stripe subscription billing for Next.js SaaS apps using Checkout, Customer Portal, webhooks, and app-side entitlement sync.
version: 0.1.1
author: 30float
license: MIT
tags: [payments, stripe, billing, nextjs, saas, ai-agents]
---

# Payment Integration Skill

## Overview

Use this skill to help an AI coding agent plan and implement Stripe subscription billing for a Next.js SaaS app. V1 is intentionally narrow: Stripe-only, subscriptions-only, and optimized for a plan-first workflow using Stripe Checkout, Stripe Customer Portal, webhook-driven state sync, and app-side entitlement modeling.

This file is written to be **portable across agent ecosystems**. It should work as:
- an installable skill in agent platforms that support skills
- a reusable prompt module in agent platforms that use prompt bundles or task playbooks
- a structured internal operating guide for custom in-house agents

The frontmatter is intentionally minimal and generic. If a platform does not use frontmatter, the instructions below should still remain usable as plain Markdown.

This skill supports both:
- **user-based billing** for personal SaaS products
- **workspace-based billing** for team/org products

The skill should be used to inspect the application, identify missing business and billing details, recommend a billing architecture, produce a plan, and only then proceed to implementation if the user approves.

## Use this skill when

Use this skill when the request involves one or more of the following:
- adding Stripe subscriptions to a Next.js SaaS app
- deciding whether billing should belong to a user or a workspace/team
- planning Checkout + Customer Portal + webhook sync
- introducing or repairing entitlement modeling tied to billing state
- auditing a partial or inconsistent Stripe subscription integration
- preparing a Stripe rollout plan before making code changes

## Do not use this skill when

This skill is not the primary path for:
- one-time payment-only implementations
- usage-based or metered billing
- credits, wallets, or prepaid balance systems
- Stripe Connect / marketplaces / split payouts
- mobile-native subscription flows
- non-Next.js apps as first-class implementation targets
- deeply custom embedded card-entry UX as the default recommendation

If the request is partially outside V1 scope, provide a planning-oriented response, clearly label the limitation, and avoid pretending the request is fully supported by this skill.

## Supported V1 scope

This skill is currently optimized for:
- **provider:** Stripe
- **billing type:** recurring subscriptions
- **framework:** Next.js
- **billing owner:** user or workspace/team
- **default billing flow:** Stripe Checkout + Stripe Customer Portal
- **state synchronization:** verified webhook events synced into the app database
- **authorization pattern:** app-side entitlement state with server-side enforcement

## Required workflow

Follow this workflow in order.

### 1. Inspect the codebase first
Inspect the app before asking billing questions. Determine, where possible:
- Next.js app structure and routing style
- auth provider and session model
- database / ORM / schema shape
- user and workspace/team entities
- owner/admin role concepts
- account/settings pages or likely billing entry points
- existing payment or billing traces (`stripe`, `billing`, `subscription`, `checkout`, `portal`, `webhook`, `customer_id`, `price_id`)

### 2. Summarize findings before asking questions
Before asking the user anything, summarize:
- what stack was detected
- whether the app appears user-centric or workspace-centric
- what billing entry points likely exist
- what is still ambiguous and needs clarification

### 3. Classify scope fit
Classify the request as one of:
- **in-scope** — clean V1 fit
- **partial-fit** — mostly V1, but with extra complexity or existing messy billing code
- **out-of-scope** — beyond the primary V1 path

State the classification explicitly.

### 4. Ask only missing questions
Ask only the questions that are necessary to make implementation decisions. Do not ask the user to restate things the codebase already makes obvious.

Use the intake categories in `templates/intake-questionnaire.md`:
- billing model
- billing subject
- plan structure
- entitlement behavior
- Stripe setup state
- deployment context

### 5. Recommend an architecture
Recommend:
- whether billing belongs to a user or a workspace
- whether the app should use the default Checkout + Customer Portal flow
- where Stripe customer and subscription state should live in the app
- how entitlement state should be represented and enforced
- what implementation surfaces are likely to change

### 6. Produce a plan before implementation
Before changing code, produce a structured plan covering:
- data model changes
- routes/actions/endpoints
- webhook handling
- billing UI entry points
- entitlement checks
- env vars / config
- Stripe dashboard setup
- verification steps

Use `templates/implementation-plan.md` as the default plan structure.

### 7. Require explicit approval before implementation
Do not implement code changes until the user explicitly approves the plan.

### 8. Implement conservatively
When implementation is approved:
- preserve the app's auth and data model where reasonable
- prefer minimal, reliable changes over clever abstractions
- keep plan/price config centralized
- call out any conflict with existing billing logic before replacing it

### 9. Verify
After implementation, verify:
- checkout session creation
- return flow wiring
- webhook signature verification
- customer/subscription sync into local state
- billing portal session creation
- entitlement unlock and downgrade behavior

Use `templates/verification-checklist.md` as the default verification structure.

### 10. Produce a handoff checklist
Always provide:
- required environment variables
- Stripe dashboard setup/checklist
- test-mode validation steps
- production cutover notes
- assumptions and limitations

## Intake rules

Use these intake rules consistently.

### Inspect first, ask second
Infer what you can before interviewing the user.

### Ask the minimum necessary
Every question should affect one or more of:
- billing architecture
- data model placement
- entitlement logic
- Stripe configuration
- deployment checklist

### Only ask decision-driving questions
Do not ask curiosity questions that do not affect implementation.

### Adapt questions to the detected codebase
If the app clearly uses workspaces, ask whether billing should belong to the workspace rather than asking whether workspaces exist at all.

### Use grouped categories
Use the question groups in `templates/intake-questionnaire.md` and ask only unresolved items.

## Architecture heuristics

Use these heuristics unless the user has a strong reason to do otherwise.

### Prefer Stripe Checkout when
- the request is standard SaaS subscription billing
- hosted checkout is acceptable
- there is no hard requirement for a custom embedded payment form

### Prefer Stripe Customer Portal when
- users need to manage plans, cancellation, payment methods, or invoices
- the default Stripe-hosted management experience is acceptable

### Recommend workspace billing when
- the app has teams/workspaces/orgs
- premium access is shared across members
- owner/admin roles exist or should exist
- one subscription should unlock access for multiple users

### Recommend user billing when
- premium access is personal to the signed-in user
- there is no meaningful shared workspace concept
- account settings are user-scoped and entitlements are not shared

### Treat webhook events as billing truth
Do not rely on redirect success pages as proof of billing state.

### Keep plan/price configuration centralized
Avoid scattering Stripe IDs across random files. Use one clear mapping layer or config surface.

## Safety rules

### Never
- expose secrets in code, docs, or output
- hardcode API keys or signing secrets
- trust client-only billing state for entitlements
- treat a successful redirect as subscription truth
- silently replace existing billing logic without calling it out
- introduce destructive schema changes without explanation and approval

### Always
- preserve the app's existing auth and data model unless a justified change is needed
- call out conflicts and assumptions before implementation
- explain limitations clearly when the request leaves V1 scope
- keep entitlement logic explicit and reviewable
- prefer server-side checks for premium access

## Required outputs

### In planning mode
Produce the following:
1. findings summary
2. scope classification
3. unresolved questions
4. billing architecture recommendation
5. structured implementation plan
6. risks and assumptions
7. Stripe dashboard checklist
8. verification approach

### In implementation mode
Also produce:
- summary of changes made
- files affected
- environment variables required
- remaining manual Stripe/dashboard steps
- verification results
- known limitations or deferred edge cases

## References

Use the linked materials in this repository to guide behavior:
- `references/stripe-default-architecture.md`
- `references/billing-data-model.md`
- `references/webhook-truth-model.md`
- `references/entitlement-design.md`
- `references/out-of-scope-scenarios.md`
- `templates/intake-questionnaire.md`
- `templates/architecture-recommendation.md`
- `templates/implementation-plan.md`
- `templates/dashboard-checklist.md`
- `templates/verification-checklist.md`

## Example operating pattern

A good operating pattern looks like this:
1. inspect the app and detect Next.js + auth + data model
2. infer whether the app is user-centric or workspace-centric
3. summarize findings before asking questions
4. ask only the missing billing questions
5. recommend a Stripe billing architecture
6. produce a plan before code changes
7. implement only after approval
8. verify checkout, portal, webhook sync, and entitlements

The goal is not to dump Stripe trivia. The goal is to help the agent produce a sane, production-oriented billing integration plan and execute it carefully when approved.
