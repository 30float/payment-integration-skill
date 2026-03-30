# Provider Scope

## V1 provider strategy

V1 is intentionally **Stripe-first and Stripe-only**.

That is not because other payment providers are unimportant. It is because a public skill becomes weak and vague if it claims broad provider support before the architecture, examples, and safety guidance are deep enough to be useful.

## Why Stripe first

Stripe is the best first provider for this skill because it is:
- commonly used in SaaS apps
- well understood by developers
- broad enough to support the default subscription path
- compatible with hosted Checkout and Customer Portal flows
- mature in webhook-driven subscription lifecycle handling

## Future providers

Future provider support may include:
- LemonSqueezy
- Paddle

Those additions should only land once the repo has:
- clear scope boundaries
- provider-specific architecture guidance
- provider-specific examples
- updated templates and verification guidance

## Rule for agents

If the user requests a provider outside the current first-class scope, do not pretend it is equally supported. Label the limitation clearly and either:
- provide planning-only guidance, or
- recommend the current Stripe path if that still fits the product requirements
