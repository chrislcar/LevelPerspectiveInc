---
type: readme
status: active
version: 1.0.0
last-updated: 2026-05-08
---

# canonical-prompts/daily-ops/

Ritual prompts — the operational glue that keeps the methodology layer maintained without depending on user discipline.

| File | Ritual | Cadence | Duration | Status |
|---|---|---|---|---|
| `weekly-close.md` | Friday close — review working branch, merge to main, identify stale items, capture pending commits | Weekly | 15 min | Pending |
| `methodology-garage-sale.md` | Quarterly review — walk repo, flag deprecation/archival/refinement candidates | Quarterly | 90 min | Pending |
| `engagement-close-retro.md` | Per-engagement retro — what worked, what failed, methodology backlog entries | Per engagement | 60 min | Pending |
| `disaster-recovery-test.md` | Annual continuity test — simulate Claude / GitHub / M365 outages | Annually | 2 hours | Pending |
| `link-integrity-check.md` | Walk all visual-master URLs in repo; flag broken | Weekly (automated by Friday close) | 5 min | Pending |
| `graduation-conversation.md` | Convert ephemeral OneNote note into canonical Markdown spec | On trigger | 15 min | Pending |
| `open-brain-mirror.md` | Export Open Brain to repo `/doctrine/open-brain-export.md` | Weekly (automated by Friday close) | 5 min | Pending |
| `stale-item-audit.md` | Find files in repo not updated in 90 days; flag for review | Monthly | 15 min | Pending |

## Ritual hierarchy

```
Annual: disaster-recovery-test
   └── Quarterly: methodology-garage-sale
          └── Monthly: stale-item-audit
                 └── Weekly: weekly-close (includes link-integrity-check, open-brain-mirror)
                        └── Per-engagement: engagement-close-retro
                               └── On-trigger: graduation-conversation
```

Higher-cadence rituals do small work; lower-cadence rituals do bigger work that aggregates from the higher-cadence rituals.

## How to use

1. Open the ritual prompt
2. Paste into Claude
3. Provide any inputs the prompt asks for
4. Approve actions Claude proposes
5. Claude executes (commits, files, tags)

The ritual prompt is the trigger. The system maintains itself via the rituals; you maintain the rituals (15 min/week is the floor).

## Calendar discipline

Block weekly close in calendar (Friday afternoon recommended). Block quarterly garage sale (one Friday afternoon every 3 months). Block annual DR test (one weekend day per year). Without calendar blocks, rituals don't fire and the system drifts.
