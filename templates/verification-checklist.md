# Verification Checklist

## Checkout
- Upgrade action opens a Stripe Checkout session
- User can reach hosted Checkout successfully
- Success and cancel URLs are wired correctly

## Webhooks
- Webhook endpoint receives Stripe events
- Signature verification is working
- Relevant customer/subscription state is synced locally

## Billing state
- The app reflects the correct plan / status after a successful test purchase
- Billing ownership is attached to the right entity (user or workspace)
- Downgrade / inactive states are handled as planned

## Customer Portal
- Billing settings can launch a Stripe Customer Portal session
- Plan management / cancellation path is reachable

## Entitlements
- Premium access unlocks after billing sync
- Premium access is removed or downgraded according to the chosen lifecycle rules
- Client UI and server-side checks align on access state
