---
type: readme
status: active
version: 0.1.0
last-updated: 2026-05-09
---

# Methodology Changelog

Top-level log of methodology changes. Per-playbook changes are tracked in each playbook's README.

Format: each entry is a dated section. Releases are tagged in Git matching the version number.

---

## v0.2.0 — 2026-05-09

Step 9 sync facilitation spec locked. Branching architecture simplified to single-branch direct-to-`main` flow.

**Added:**
- Step 9 (Cross-element integration) sync facilitation spec — virtual variant — v1.0.0 locked, untested. Brightworks-aligned SGF geometry. Six-move structure with 70%-threshold identity-vs-aspiration protocol.

**Changed:**
- Branching architecture: dropped `working` branch and Friday merge gate to `main`. Commits now flow directly to `main`. Rationale: gate friction outweighed defensibility benefit at solo-author cadence. Friday weekly-close ritual continues as review + changelog + Open Brain mirror function. In-flight engagement protection preserved via Git tags rather than branches.
- Top-level README — Branching workflow section rewritten; Rituals table updated; graduation triggers paragraph updated to commit-to-`main`.
- `canonical-prompts/daily-ops/README.md` — `weekly-close.md` description updated to reflect review-not-merge function.
- `playbooks/p1-1-current-state/sync-facilitation/README.md` — Step 9 status flipped from Pending to v1.0.0 locked, untested.

**Engagement protection note:**
- No in-flight engagements at this date. Tag `engagement/[client]-[YYYY-QN]` protocol now load-bearing for any future engagement.

---

## v0.1.0 — 2026-05-08

Initial repo setup. Skeleton structure, canonical prompts library scaffolded, P1.1 v3.1 step architecture in place.

**Added:**
- Repo skeleton with frontmatter standard
- P1.1 v3.1 step architecture (18 steps, working hypothesis)
- Step 4 (Strategic Direction) async prep spec
- Step 5 (Brand Image) async prep spec
- Step 6 (Organizational Culture) async prep spec
- Step 6 sync facilitation spec — virtual variant
- Recovery procedures
- Operating principles and rituals

**Pending:**
- Steps 4, 5, 8, 9 sync facilitation specs
- In-person variant for Step 6 sync
- Learning video scripts (V1, V2, V3, V4, V_oc)
- AI synthesis prompts (per element + cross-element)
- Run-kit operational artifacts
- FigJam and Figma masters
- Open Brain export mirror

---

## Template for future entries

```markdown
## vX.Y.Z — YYYY-MM-DD

One-sentence summary of the release.

**Added:**
- New artifacts or capabilities

**Changed:**
- Modifications to existing artifacts (with rationale)

**Deprecated:**
- Artifacts marked deprecated (with successor reference)

**Removed:**
- Artifacts removed entirely (rare; usually deprecate instead)

**Fixed:**
- Corrections to errors in existing artifacts

**Engagement protection note (if applicable):**
- Which in-flight engagements are tagged at the prior version
- Whether this release is patch-compatible (safe to apply mid-engagement) or requires version locking
```
