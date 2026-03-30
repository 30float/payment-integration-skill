# Webhook Truth Model

## Principle

A successful redirect is not billing truth.

After Stripe Checkout or Stripe Customer Portal actions, the app should rely on verified Stripe webhook events to confirm and synchronize billing state.

## Why redirects are not enough

A redirect page can tell you that a user returned from Stripe. It cannot, by itself, be trusted to establish the final subscription state. There may be timing issues, retries, incomplete payment flows, or later lifecycle changes that the redirect page never sees.

## What webhooks are for

Webhooks allow the app to receive authoritative lifecycle events from Stripe and update local billing state accordingly.

That local state is then used for:
- entitlement checks
- billing UI
- access revocation or downgrade behavior
- support and debugging

## Agent rule

Agents should not design a billing integration that relies solely on:
- a success redirect page
- client-side query params
- local optimistic UI state

They should instead design an integration where:
- the webhook verifies Stripe signatures
- customer/subscription state is synced to the app database
- the app reads local billing state to decide access
