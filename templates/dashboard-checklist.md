# Stripe Dashboard Checklist

## Account and keys
- Confirm Stripe account exists
- Confirm test mode secret key is available
- Confirm publishable key is available if needed by the app

## Products and prices
- Create product(s)
- Create monthly and/or yearly recurring price(s)
- Record the resulting Stripe price IDs

## Checkout / Portal
- Confirm success URL
- Confirm cancel URL
- Enable or configure Customer Portal settings as needed

## Webhooks
- Create webhook endpoint in Stripe
- Add required events
- store webhook signing secret in app env vars
- verify endpoint path matches the implementation plan

## Final verification
- Run a test checkout
- Confirm webhook delivery
- Confirm local billing sync
- Confirm billing portal access
