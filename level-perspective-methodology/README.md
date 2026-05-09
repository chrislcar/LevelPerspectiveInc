---
type: repo-root
status: active
version: 0.1.0
last-updated: 2026-05-09
maintainer: Level Perspective (sole proprietor)
---

# Level Perspective — Methodology Repository

Source-of-truth for the Level Perspective methodology layer. Specs, prompts, scripts, doctrine, and run-kit artifacts for the AI Transformation portfolio (Journey 1 → 5).

This repo is the **methodology layer** in a two-layer system. Frozen client deliverables live in SharePoint; visual masters live in Figma / FigJam / Loop. This repo holds the text-native source-of-truth that drives both.

---

## Two-layer system

| Layer | Lives in | Purpose | Mutability |
|---|---|---|---|
| **Methodology layer** | This repo (text); Figma/FigJam/Loop (visual masters); SharePoint `Methodology Visual Masters/` (binary exports + recordings) | The offering. Refined every time it's delivered. | Living, versioned, evergreen |
| **Engagement layer** | SharePoint `Engagements/[client]/[date]/` | Frozen artifacts of what was delivered to a specific client | Append-only during engagement; frozen at close |

If you find yourself versioning a SharePoint file, it belongs in this repo instead. If you find yourself running engagement-specific work in a methodology Claude Project, spawn a per-engagement project instead.

---

## Repo structure

```
level-perspective-methodology/
├── README.md                          (this file)
├── changelog.md                       (top-level methodology change log)
├── doctrine/                          (cross-playbook doctrine, glossary, citations)
├── operations/                        (recovery procedures, ritual templates, release process)
├── playbooks/                         (one folder per Pn.x playbook)
│   └── p1-1-current-state/
│       ├── README.md                  (playbook scope and status)
│       ├── architecture/              (step architecture, working hypothesis versions)
│       ├── async-prep/                (per-step async prep specs)
│       ├── sync-facilitation/         (per-step sync facilitation specs, virtual + in-person)
│       ├── learning-videos/           (≤5 min flipped-classroom video scripts)
│       ├── prompts/                   (AI synthesis prompts run during the playbook)
│       ├── run-kit/                   (operational artifacts for delivery)
│       └── reference/                 (per-playbook reference orgs, examples)
├── canonical-prompts/                 (reusable prompt library across all playbooks)
│   ├── methodology-authoring/         (used while building the methodology)
│   ├── engagement-delivery/           (used while running an engagement)
│   ├── daily-ops/                     (Friday close, garage sale, retro, etc.)
│   └── visual-asset-generation/       (image-gen prompts for video decks, illustrations)
└── visual-masters/                    (INDEX ONLY — actual files in Figma/Loop/SharePoint)
```

---

## File metadata standard (YAML frontmatter)

Every Markdown file in this repo opens with YAML frontmatter. Claude maintains this automatically; you should not need to author it manually.

```yaml
---
type: spec | prompt | script | readme | doctrine | run-kit | reference
status: draft | locked | deprecated
version: x.y.z
last-updated: YYYY-MM-DD
supersedes: path/to/previous-file.md          # optional
referenced-by:                                  # optional, list of paths
  - path/to/other-spec.md
referenced-visual-masters:                      # optional, URLs
  - https://figma.com/...
  - https://loop.microsoft.com/...
playbook: p1-1                                  # if scoped to a playbook
step: 6                                         # if scoped to a step
---
```

**Status meanings:**

| Status | Meaning | Behavior |
|---|---|---|
| `draft` | In progress; subject to change | Do not use in client engagements |
| `locked` | Approved for use in engagements | Versioned at engagement-tag time; in-flight engagements protected |
| `deprecated` | Superseded; preserved for history | Do not use; `supersedes` field on successor file points back here |

---

## Branching workflow

Single-branch flow on `main`. Claude commits directly to `main` via Desktop Commander + git CLI. There is no staging branch.

| Branch | Purpose | Who writes |
|---|---|---|
| `main` | The live methodology. All commits land here. | Claude (via Desktop Commander); you (via VS Code or GitHub Desktop) |
| `engagement/[client]-[YYYY-QN]` | Tagged snapshot at engagement start; protects in-flight engagements from breaking changes | Tagged at engagement spawn; never modified after |

**Architecture rationale (locked 2026-05-09):** the prior architecture had a `working` branch with a Friday merge gate to `main`. That gate was dropped because the friction outweighed the defensibility benefit at solo-author cadence. The Friday weekly-close ritual continues as a review + changelog + Open Brain mirror function, but no longer gates canonicality.

**In-flight engagement protection:** preserved via Git tags rather than branches. When an engagement starts, the methodology version is tagged (`engagement/[client]-[YYYY-QN]`); the engagement uses that tagged version through to close, regardless of subsequent commits to `main`. See *Versioning* below.

**Risk acknowledged:** without a pre-commit gate, bad commits land on `main` immediately. Mitigations: every commit is reviewable via `git log` and `git diff`; Friday weekly-close audits last week's commits; locked specs carry a `version` and `spec-status: locked` frontmatter so accidental edits are visible; tags protect engagement-time snapshots.

---

## ChatGPT vs Claude routing rule

Claude is the primary methodology assistant. ChatGPT has narrow, high-value uses. Default to Claude unless one of the named ChatGPT use cases applies.

| Use case | Tool |
|---|---|
| Methodology authoring (specs, prompts, scripts, sync facilitation, doctrine) | **Claude** |
| Long-context document analysis | **Claude** |
| GitHub repo operations via MCP | **Claude** |
| Open Brain interactions | **Claude** |
| Image generation for video deck visuals or illustrations | **ChatGPT (DALL-E / Sora)** |
| Voice mode while walking / thinking out loud | **ChatGPT** |
| Cross-check / second opinion on a high-stakes doctrine claim | **ChatGPT** |
| Quick web search lookups | Either; whichever is open |

If you find yourself doing methodology authoring in ChatGPT, stop and switch.

---

## Authoring workspace — canonical setup

When authoring methodology in this repo, the canonical setup is:

| Window / app | Purpose |
|---|---|
| **VS Code** | Repo browsing and direct file editing when needed |
| **Claude desktop or web** | Active methodology authoring conversation in the relevant Claude Project |
| **OneNote on iPad** | Ephemeral capture, ink notes, mid-session sketches |
| **Browser tab — Open Brain** | Doctrine reference |
| **Browser tab — relevant references** | SGF Briefing, Playbook Quality Rubric, etc. |
| **Browser tab — GitHub web UI** | Pull request review and merge (Friday ritual) |

Pin these so a methodology-authoring session is one click away from full context.

---

## Graduation triggers — ephemeral to canonical

Notes start ephemeral (OneNote scratch) and graduate to canonical (this repo) when any of the following triggers fire:

1. **Reference test:** I've referenced this idea twice or more.
2. **Engagement test:** I'm about to use this in a client engagement.
3. **Findability test:** I want Claude to find this later.
4. **Doctrine test:** This is a principle that applies across multiple playbooks.

When a trigger fires, ask Claude to graduate the note. Claude reads the OneNote page (photographed if handwritten), drafts a Markdown file with frontmatter, you review the diff, Claude commits to `main`.

Notes that don't fire any trigger after 30 days are candidates for archival in the next garage sale.

---

## Rituals — what gets done when

| Ritual | Cadence | Duration | What happens |
|---|---|---|---|
| **Weekly close (Friday)** | Weekly | 15 min | Review week's commits on `main`; update changelog; mirror Open Brain; identify stale items |
| **Engagement retro** | Per engagement, at close | 60 min | Structured retro; methodology backlog entries created; engagement archived |
| **Methodology garage sale** | Quarterly | 90 min | Walk repo with Claude; flag deprecation, archival, refinement candidates |
| **Disaster recovery test** | Annually | 2 hours | Simulate "Claude unavailable for a week"; verify recovery procedures still work |

Each ritual has a canonical Claude prompt in `/canonical-prompts/daily-ops/`. Open the prompt; paste into Claude; execute.

---

## Backups and continuity

| Layer | Primary | Backup 1 | Backup 2 |
|---|---|---|---|
| Repo (text) | GitHub remote | Local clone via GitHub Desktop on Mac | Weekly ZIP export to SharePoint `Methodology Visual Masters/Repo Backups/` |
| Visual masters | Figma / Loop cloud | Account export quarterly | — |
| Recordings | SharePoint | M365 backup (within tenant) | — |
| Open Brain | Open Brain cloud | Weekly export to `/doctrine/open-brain-export.md` in this repo | — |
| Engagement deliverables | SharePoint | M365 backup | Frozen exports never modified after engagement close |

Recovery procedures for each layer are in [`operations/recovery-procedures.md`](operations/recovery-procedures.md).

---

## Versioning

Semantic versioning for the methodology as a whole.

| Version part | Meaning | Example |
|---|---|---|
| `major` | Breaking change to a playbook structure or canonical doctrine | v3 → v4 |
| `minor` | New playbook released, or significant additions to an existing playbook | v3.1 → v3.2 |
| `patch` | Refinements that don't break in-flight engagements | v3.1.0 → v3.1.1 |

Methodology version is tracked at the repo root (this README) and on each playbook README. Releases are tagged in Git.

In-flight engagement protection: when an engagement starts, the methodology version is tagged (`engagement/[client]-[YYYY-QN]`). The engagement uses that tagged version through to close, regardless of subsequent releases.

---

## Quick command reference for working with Claude

| Goal | Phrase |
|---|---|
| Find an artifact | "Find me the latest [name] in the repo" |
| Update an artifact | "Update [path] to reflect [change]; show me the diff before committing" |
| Capture this conversation as an artifact | "Capture this as a spec / prompt / script in the repo" |
| Check what's stale | "What in the repo hasn't been updated in 90 days?" |
| Run the Friday ritual | "Run the weekly close ritual" |
| Spawn a new engagement | "Spawn a new engagement workspace for [client] starting [date]" |
| Mirror Open Brain | "Mirror Open Brain to /doctrine/open-brain-export.md" |
| Check link integrity | "Run the link-integrity check" |

Any of these should work as plain language. Claude knows the repo via GitHub MCP.

---

## Repo conventions

- **Filenames:** lowercase, hyphenated, descriptive. `step-6-organizational-culture-spec.md` not `Step6OrgCulture.md`.
- **One spec per file.** Don't combine specs.
- **Sentence case in document headings.** Title case in file/folder names where it improves readability.
- **No proprietary client information in this repo.** Client names appear only in `engagement/[client]-[YYYY-QN]` tags. Engagement-specific content lives in SharePoint, never here.
- **Cite sources.** When a spec makes a claim drawn from external literature, cite it. When it's drawn from Open Brain, attribute Open Brain. Inference and hypothesis are labeled as such.

---

## Maintainer notes

This repo is operated by Level Perspective (sole proprietorship). Daily operations are handled by Claude via GitHub MCP. The maintainer's role is approval, review, and merge.

If the maintainer becomes unavailable for >2 weeks, see `operations/recovery-procedures.md` for handoff procedures.
