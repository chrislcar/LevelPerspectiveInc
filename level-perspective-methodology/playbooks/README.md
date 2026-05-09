---
type: readme
status: active
version: 1.0.0
last-updated: 2026-05-08
---

# playbooks/

One folder per Pn.x catalog playbook. Each playbook folder contains its own README, step architecture, async preps, sync facilitation specs, learning videos, AI prompts, run-kit artifacts, and reference materials.

## Journey 1 catalog (current state)

| Playbook | Folder | Status |
|---|---|---|
| P1.1 — Current-State Diagnosis | `p1-1-current-state/` | Active authoring |
| P1.2 — Strategic Decisions | (not yet created) | Future |
| P1.3 — TBD | (not yet created) | Future |
| P1.4 — TBD | (not yet created) | Future |
| P1.5 — Governance Infrastructure & Identity Bookend | (not yet created) | Future |

The Journey 1 Catalog Reference (in this Claude Project's project knowledge) is the canonical source for scope boundaries, U-shape, and decision sequencing across P1.1 → P1.5.

## Spawning a new playbook folder

When authoring begins on a new playbook, Claude generates the standard folder structure (architecture / async-prep / sync-facilitation / learning-videos / prompts / run-kit / reference) along with skeleton READMEs. The folder structure is canonical across all playbooks for consistency.

## Cross-playbook references

When a playbook references doctrine that applies across multiple playbooks, the reference points to `/doctrine/` rather than duplicating the doctrine inline. This keeps doctrine evolution in one place.
