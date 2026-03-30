# Intake Questionnaire

Use this template after inspecting the codebase. Ask only the unresolved questions that affect implementation.

## 1. Billing model
- Is this a recurring subscription product?
- Do you want monthly pricing, yearly pricing, or both?
- Do you want a free tier?
- Do you want a free trial in V1?

## 2. Billing subject
- Should billing belong to an individual user or a workspace/team?
- If the app has workspaces, should one workspace subscription unlock access for all members?
- Who should be allowed to manage billing (user, workspace owner, admins)?

## 3. Plan structure
- How many paid plans should V1 support?
- Are plans simple fixed tiers, or is there seat-based / usage-based complexity that should be treated as out-of-scope for V1?

## 4. Entitlement behavior
- What exactly does a paid subscription unlock?
- What should happen when a subscription becomes inactive or is canceled?
- Should downgrade happen immediately, at period end, or after a grace period?

## 5. Stripe setup state
- Do you already have a Stripe account?
- Are test mode API keys ready?
- Do products and prices already exist?
- Should the app be structured first with plan/price IDs bound later, or should the integration assume the IDs are already available?

## 6. Deployment context
- Is the initial target local/test mode only, deploy-ready test mode, or production-ready immediately?
- What hosting platform is in use?
- Is there already a stable domain/URL for callback and webhook configuration?
