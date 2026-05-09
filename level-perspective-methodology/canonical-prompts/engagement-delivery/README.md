---
type: readme
status: active
version: 1.0.0
last-updated: 2026-05-08
---

# canonical-prompts/engagement-delivery/

Prompts used while running an engagement. Run these in Claude inside the per-engagement Claude Project (not in a methodology Project).

| File | Purpose | When run | Status |
|---|---|---|---|
| `spawn-engagement-workspace.md` | Stand up a new per-client Claude Project, SharePoint folder, engagement Git tag | At engagement start | Pending |
| `pre-session-synthesis-runner.md` | Wrap a P1.1 element AI synthesis prompt with engagement-specific context | 24h before each sync session | Pending |
| `pre-session-readiness-check.md` | Verify pre-work submission and video viewing for all stakeholders | 48h / 24h before each session | Pending |
| `post-session-handoff.md` | Capture session outputs, dissent, parking-lot items into engagement journal and handoff doc | After each sync session | Pending |
| `engagement-close-retro.md` | Structured retro at engagement close; produces methodology backlog entries | At engagement close | Pending |
| `engagement-archive.md` | Archive engagement: freeze SharePoint folder, archive Claude Project, close Git tag | After retro | Pending |

## When to use

These prompts are for delivery seat — when you have an actual client engagement underway. They reference methodology artifacts but don't modify them.

## Engagement isolation

Per-engagement work happens in per-engagement Claude Projects. These prompts are designed to operate in that context and reference the methodology layer read-only.

If a prompt produces output that should propagate back to the methodology layer (e.g., a refinement learned during the engagement), it surfaces as a methodology backlog entry — not as a direct edit. The engagement-close retro is the canonical path for engagement → methodology learning flow.
