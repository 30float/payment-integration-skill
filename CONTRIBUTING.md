# Contributing

Thanks for contributing. This repo is intentionally narrow, and keeping it sharp matters more than making it superficially broad.

## Current scope

V1 focuses on:
- Stripe
- recurring subscriptions
- Next.js SaaS apps
- user or workspace billing
- Stripe Checkout + Customer Portal + webhook-driven state sync

## Good contributions

Helpful contributions include:
- better examples for supported V1 scenarios
- clearer guidance for billing data modeling
- stronger webhook and entitlement safety guidance
- fixes to ambiguous or weak intake questions
- better templates for planning, dashboard setup, and verification
- issue reports where the skill makes a bad billing recommendation inside V1 scope

## Please do not

Please do not open broad “support everything” PRs that:
- add multiple providers with no examples or decision logic
- claim support for new frameworks without demonstrating implementation patterns
- add giant Stripe tutorials unrelated to the skill workflow
- blur V1 by stuffing in marketplaces, metering, or mobile billing without a clear scope expansion plan

## Quality bar for scope expansion

If you want to propose a new provider, billing model, or framework, include:
- the proposed scope boundary
- architecture heuristics
- safety implications
- at least one example scenario
- changes needed to templates and references
- a clear explanation of what remains unsupported

## Style expectations

Keep docs:
- direct
- technical
- explicit about tradeoffs
- honest about scope limits

Avoid hype, vague AI language, and promises the skill cannot back up.

## Opening issues

When reporting a problem, include:
- the app shape (for example: Next.js + Supabase, workspace-based SaaS)
- what the skill recommended
- what was wrong or incomplete
- what you expected instead

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
