---
type: readme
status: active
version: 1.0.0
last-updated: 2026-05-08
playbook: p1-1
---

# p1-1-current-state/prompts/

AI synthesis prompts run during P1.1 delivery. These are playbook-specific prompts (run with specific stakeholder submissions as input).

For reusable prompts that span multiple playbooks, see `/canonical-prompts/`.

| File | Purpose | When run | Status |
|---|---|---|---|
| `ai-synthesis-strategic-direction.md` | Cross-lane stated-vs-operating contradiction surfacing | 24h before Step 4 sync | Pending |
| `ai-synthesis-brand-image.md` | Cross-lane overclaim/underclaim/incoherence map | 24h before Step 5 sync | Pending |
| `ai-synthesis-org-culture.md` | Two-way relational priming + walk/talk gap candidates | 24h before Step 6 sync | Pending |
| `ai-synthesis-cross-element.md` | Triangulates all four element outputs; Vision–Image, Image–Culture, Culture–Vision gaps | 24h before Step 9 sync | Pending |
| `ai-priming-center.md` | Surfaces narrative-as-throughline candidates from cross-element evidence | Before Step 8 sync | Pending |
| `ai-overclaim-review-checklist.md` | Methodologist-only artifact; vets AI synthesis output for hallucination, stale source, overclaim | 26h before each sync | Pending |
| `ai-selection-pattern-analysis.md` | Methodologist-only; surfaces convergence / divergence / avoidance across stakeholders | After workbook submission | Pending |

## Prompt structure

Each prompt file contains:

1. **Frontmatter** — type, status, version, playbook, step
2. **Purpose** — what this prompt produces
3. **Inputs** — what gets pasted in as context
4. **Output specification** — what the AI must produce; what the AI must NOT produce
5. **The prompt itself** — verbatim, copy-paste ready

## What AI does and does not do

Per Open Brain doctrine: AI normalizes evidence, dedupes, sorts to grid cells, proposes candidate articulations citing supporting evidence, and flags contradictions. AI does NOT author final commitments, resolve contradictions, or pick between candidate reads. Every prompt enforces this in its output spec.
