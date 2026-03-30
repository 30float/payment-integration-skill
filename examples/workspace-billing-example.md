# Example: Workspace Billing

## Scenario

A Next.js app has workspaces, workspace members, and owner/admin roles. Premium features are shared by the entire workspace.

## What the agent should detect

- clear workspace/team concept
- shared member access
- owner/admin role semantics
- billing likely belongs in workspace settings rather than personal account settings

## Recommended direction

- classify as **in-scope**
- recommend **workspace-based billing**
- attach Stripe customer/subscription state to the workspace or a workspace-owned billing record
- allow billing management only for workspace owners/admins
- apply premium entitlements across workspace members according to workspace billing state

## Key caution

Do not default to user billing just because the app also has user accounts. The billing owner should match how access is actually shared in the product.
