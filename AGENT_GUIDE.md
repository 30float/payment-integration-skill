# Agent Guide: Payment Integration

This file is the **neutral entrypoint** for agent ecosystems that do not use a `SKILL.md` convention.

## Purpose

Use this guide when an AI coding agent needs to plan, audit, or implement **Stripe subscription billing for a Next.js SaaS app**.

It is intentionally written so it can work as:
- a prompt module
- an agent instruction bundle
- an internal operating guide
- a portable alias for the repo's main skill instructions

## Canonical instruction source

The canonical operating instructions live in [`SKILL.md`](./SKILL.md).

That file defines:
- supported scope
- required inspection-first workflow
- intake questions
- architecture recommendations
- planning requirements before implementation
- verification and rollout expectations
- safety boundaries

## How to use this repo

Choose the entrypoint that matches the host platform:

- use [`SKILL.md`](./SKILL.md) for platforms that support installable skills
- use this file (`AGENT_GUIDE.md`) for platforms that prefer a neutral guide or prompt module
- keep [`references/`](./references), [`templates/`](./templates), and [`examples/`](./examples) available alongside whichever entrypoint you use

## Portability rule

If `SKILL.md` and `AGENT_GUIDE.md` ever diverge, treat `SKILL.md` as canonical and update this file to match.

## Recommended next read

Open [`SKILL.md`](./SKILL.md) and follow it as the primary operating document.
