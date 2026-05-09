---
type: doctrine
status: locked
version: 1.0.0
last-updated: 2026-05-08
---

# Frontmatter standard

Every Markdown file in this repo opens with YAML frontmatter. This is the canonical schema.

## Required fields

| Field | Values | Example |
|---|---|---|
| `type` | spec, prompt, script, readme, doctrine, run-kit, reference, changelog | `type: spec` |
| `status` | draft, locked, deprecated | `status: draft` |
| `version` | semver: `x.y.z` | `version: 0.3.1` |
| `last-updated` | ISO date | `last-updated: 2026-05-08` |

## Optional fields

| Field | Values | When to use |
|---|---|---|
| `supersedes` | path to file | When this file replaces another |
| `superseded-by` | path to file | When this file has been replaced (and is now `deprecated`) |
| `referenced-by` | list of paths | Files that depend on this one |
| `referenced-visual-masters` | list of URLs | Figma / Loop / SharePoint links this file references |
| `playbook` | playbook ID | When the file is scoped to a playbook (`p1-1`, `p1-2`, etc.) |
| `step` | integer | When the file is scoped to a specific step |
| `maintainer` | name | When the file has a non-default owner |

## Worked example — spec file

```yaml
---
type: spec
status: locked
version: 1.2.0
last-updated: 2026-05-08
supersedes: playbooks/p1-1-current-state/async-prep/step-6-organizational-culture-spec-v1.md
referenced-by:
  - playbooks/p1-1-current-state/sync-facilitation/step-6-virtual.md
  - playbooks/p1-1-current-state/prompts/ai-synthesis-org-culture.md
referenced-visual-masters:
  - https://figma.com/file/abc123/p1-1-org-culture-canvas
  - https://loop.microsoft.com/.../v_oc-recording
playbook: p1-1
step: 6
---
```

## Worked example — prompt file

```yaml
---
type: prompt
status: locked
version: 0.2.0
last-updated: 2026-05-08
playbook: p1-1
step: 6
referenced-by:
  - playbooks/p1-1-current-state/run-kit/pre-session-readiness-check.md
---
```

## Worked example — README

```yaml
---
type: readme
status: active
version: 1.0.0
last-updated: 2026-05-08
---
```

(README files use `status: active` rather than draft/locked/deprecated.)

## Status transitions

```
draft ──→ locked ──→ deprecated
            │
            └──→ deprecated (with superseded-by pointing at successor)
```

`draft` files are not used in client engagements. `locked` files are the operational version. `deprecated` files are preserved for history; the successor file's `supersedes` field points back at the deprecated file.

## Maintenance

Claude maintains frontmatter automatically when editing files via GitHub MCP. If you edit a file directly in VS Code, update `last-updated` and `version` (semver bump rules below).

## Semver bump rules for individual files

| Bump | When |
|---|---|
| `patch` (x.y.Z) | Refinement that doesn't change meaning (typo fix, citation correction, clearer phrasing) |
| `minor` (x.Y.z) | Substantive addition that doesn't break downstream files (new section, expanded example) |
| `major` (X.y.z) | Breaking change (restructure, removal of section, change to deliverable shape) |

When a file's major version bumps, all files in `referenced-by` should be reviewed.
