# payment-integration-skill

Public installable skill for AI coding agents to plan and implement production-ready Stripe subscription billing in Next.js SaaS apps.

## Why this exists

Adding billing to an app still takes too much manual work, and AI agents often implement payment flows inconsistently or unsafely. This repo provides a structured, opinionated path for introducing Stripe subscriptions into a SaaS app without relying on hand-wavy payment advice or redirect-page wishful thinking.

This skill is built around a few hard rules:
- inspect the codebase before making assumptions
- ask only the billing questions that actually affect implementation
- prefer Stripe Checkout and Customer Portal for standard SaaS billing
- treat verified webhook events as billing truth
- sync billing state into the app for entitlements and product behavior
- plan before implementation

## What it does

This skill helps an AI coding agent:
- inspect app architecture, auth, routing, and data model
- identify whether billing should belong to a user or a workspace/team
- ask only the minimum necessary intake questions
- recommend a sane Stripe subscription architecture
- produce an implementation plan before changing code
- implement Checkout, Customer Portal, webhook sync, and entitlement modeling when requested
- produce verification and deployment checklists for test and production rollout

## Supported in V1

This skill is currently optimized for:

- **Provider:** Stripe
- **Billing model:** recurring subscriptions
- **App type:** Next.js SaaS apps
- **Billing owner:** individual user or workspace/team
- **Preferred flow:** Stripe Checkout + Stripe Customer Portal
- **State sync:** webhook-driven customer/subscription sync into the app database
- **Authorization model:** app-side entitlement state with server-side enforcement

## Not yet supported

V1 intentionally does **not** try to cover every payment scenario. First-class support does not yet include:

- one-time payments
- usage-based or metered billing
- credits / wallet systems
- Stripe Connect / marketplaces / split payouts
- mobile-native subscription flows
- enterprise invoicing-heavy billing workflows
- non-Next.js frameworks as first-class implementation targets
- deeply custom embedded card-entry flows as the default recommendation

If a request falls outside that scope, the skill should say so clearly and switch into a planning-oriented response instead of pretending it is fully supported.

## Workflow

The skill is designed to guide an agent through this sequence:

1. Inspect the app and detect framework, auth, data model, and existing billing traces
2. Summarize what was found before asking questions
3. Ask only the missing implementation-relevant billing questions
4. Classify the request as in-scope, partial-fit, or out-of-scope for V1
5. Recommend a Stripe architecture suited to the app
6. Produce a plan before making code changes
7. Implement only after explicit approval
8. Verify checkout, portal, webhook sync, and entitlements
9. Produce a deploy-ready checklist for Stripe and hosting configuration

## Default architecture philosophy

This skill is intentionally opinionated.

For standard SaaS subscription billing, it prefers:
- **Stripe Checkout** over custom card-entry UI
- **Stripe Customer Portal** over hand-built billing settings UX
- **verified webhook events** over redirect success pages as payment truth
- **centralized plan/price configuration** over scattered Stripe IDs in random files
- **server-side entitlement checks** over client-only gating

That default path is not the only valid one, but it is a strong default for getting reliable billing into a real app without unnecessary complexity.

## Example prompts

- `Plan Stripe subscriptions for my Next.js + Supabase SaaS app.`
- `Add workspace billing to my Next.js app using Stripe Checkout and Customer Portal.`
- `Audit my existing Stripe integration and identify what is missing.`
- `Recommend whether my app should use user billing or workspace billing.`
- `Plan a Stripe subscription rollout for my Prisma-backed Next.js app before touching code.`

## Repository contents

- `SKILL.md` — the installable skill and operating instructions for agents
- `references/` — architecture, modeling, and safety guidance
- `templates/` — structured intake, planning, dashboard, and verification templates
- `examples/` — sample scenarios and agent interaction patterns
- `ROADMAP.md` — future scope and expansion areas
- `CONTRIBUTING.md` — contribution boundaries and quality expectations

## Agent compatibility

This repo is intended to be **agent-agnostic**.

It should be usable with Hermes, Claude Code, Codex-style agents, OpenCode, custom internal agents, or any other system that can consume structured prompt/skill instructions plus supporting reference files.

The core design choice is simple: keep the main operating instructions in plain Markdown, use only minimal generic frontmatter, and keep the surrounding materials modular.

## Installation / usage

The exact installation flow depends on the target agent platform, but the portable contract is:

- `SKILL.md` is the primary operating prompt / skill document
- `references/` contains supporting architecture and safety guidance
- `templates/` contains structured outputs and intake scaffolding
- `examples/` shows expected behavior and sample interaction patterns

If a platform supports installable skills, use `SKILL.md` as the entrypoint. If it does not, the same file can still be dropped into a system prompt, agent instruction bundle, or internal playbook with the support docs kept alongside it.

## Safety philosophy

This repo exists partly to reduce bad AI payment integrations.

The skill prefers:
- webhook-driven billing truth
- explicit app-side entitlement state
- environment variables for secrets
- plan-first execution
- minimal custom payment UI where hosted Stripe flows are sufficient
- preserving the app's existing auth and data model unless a change is justified

It should **not** encourage agents to treat a successful redirect as proof of payment, hardcode secrets, or silently bulldoze existing billing logic.

## Roadmap

Near-term expansion areas:
- stronger audit mode guidance
- clearer migration guidance for partial or messy Stripe setups
- LemonSqueezy and Paddle as future provider paths
- one-time payments and seat-based billing after the V1 subscription path is battle-tested
- broader stack support after the Next.js path is solid

See [ROADMAP.md](ROADMAP.md) for the fuller breakdown.

## Contributing

Contributions are welcome, but scope discipline matters here. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a PR so the repo does not turn into a giant vague “supports every billing thing” blob.

## License

MIT
