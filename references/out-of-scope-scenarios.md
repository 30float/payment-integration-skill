# Out-of-Scope Scenarios

## Purpose

This file helps agents recognize when a request leaves the primary V1 path.

## Common out-of-scope or partial-fit scenarios

### One-time payments only
Not the primary V1 path. The current skill is optimized for recurring subscriptions.

### Usage-based or metered billing
This usually requires a different pricing model, different lifecycle logic, and potentially different entitlement handling.

### Credits or wallet systems
These add a separate balance/accounting layer and should not be treated as a trivial extension of subscriptions.

### Stripe Connect / marketplaces
This introduces payout and platform complexity beyond the V1 default architecture.

### Mobile subscription flows
Platform billing rules and store-specific constraints are outside the V1 web-focused path.

### Fully custom embedded payment UI
Possible, but not the recommended default for V1. If the user insists on this, the agent should clearly label the request as outside the default path.

## Agent rule

When a request is out of scope:
- say so plainly
- provide planning-oriented guidance if useful
- avoid pretending the current skill fully covers the scenario
