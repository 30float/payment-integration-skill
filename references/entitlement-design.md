# Entitlement Design

## Goal

Billing state should translate into product access in a clean, explicit way.

## Entitlements should answer

The app should be able to answer:
- what features are free?
- what features are paid?
- who receives paid access?
- when does access end or downgrade?
- who can manage billing?

## User-based entitlement model

If billing belongs to the user:
- the signed-in user gets premium access based on their billing state
- billing management belongs in user account settings
- server-side checks should validate billing state before granting premium actions

## Workspace-based entitlement model

If billing belongs to the workspace:
- the workspace subscription controls member access
- owners/admins manage billing
- member-facing product access should derive from workspace billing state
- the app should clearly define whether all members share the same premium capabilities

## Downgrade behavior

The agent should explicitly clarify downgrade expectations, such as:
- immediate downgrade
- downgrade at period end
- grace period behavior

Do not leave downgrade behavior implicit.

## Agent rule

The skill should prefer clear, reviewable entitlement logic over scattered ad hoc checks. Premium access should not rely only on client-side UI state.
