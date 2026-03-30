# Stripe Default Architecture

## Canonical V1 path

For standard SaaS subscription billing, the default architecture is:
- Stripe Checkout for acquisition
- Stripe Customer Portal for self-serve billing management
- verified Stripe webhooks for billing truth
- local app-side billing state for entitlements and product behavior

## Acquisition flow

1. User clicks upgrade in the app
2. App creates a Stripe Checkout Session on the server
3. User completes payment on the Stripe-hosted Checkout page
4. Stripe redirects back to success or cancel URLs
5. Stripe sends webhook events reflecting customer and subscription state
6. App verifies the webhook signature and syncs billing state locally

## Management flow

1. User opens billing settings
2. App creates a Stripe Customer Portal session on the server
3. Stripe-hosted portal handles plan changes, cancellation, payment methods, and invoices
4. Stripe sends webhook events for any resulting state changes
5. App syncs those changes back into local billing state

## Why this is the default

This architecture is a strong default because it:
- minimizes custom payment UI complexity
- reduces implementation risk for standard SaaS billing
- keeps sensitive payment collection on Stripe-hosted surfaces
- supports self-serve plan management without building a full custom billing console
- gives the app a stable local model for entitlements and product access

## Default recommendations

Unless there is a strong reason not to, agents should prefer:
- Checkout over a custom payment form
- Customer Portal over a custom billing management UI
- centralized plan/price configuration
- server-side entitlement checks tied to local billing state
