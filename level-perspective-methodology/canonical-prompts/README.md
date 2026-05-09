---
type: readme
status: active
version: 1.0.0
last-updated: 2026-05-08
---

# canonical-prompts/

Reusable prompt library across all playbooks. The library exists to prevent the failure mode of greenfielding prompts every time you need one.

## Subfolders

| Folder | Purpose |
|---|---|
| `methodology-authoring/` | Prompts used while building the methodology (specs, prompts, scripts) |
| `engagement-delivery/` | Prompts used while running an engagement (pre-session synthesis, post-session debrief) |
| `daily-ops/` | Rituals (Friday close, garage sale, retro, link integrity, graduation) |
| `visual-asset-generation/` | Image-generation prompts for video deck visuals (typically run in ChatGPT) |

## How to use

1. Open the relevant subfolder
2. Read the README (lists prompts with one-sentence descriptions)
3. Copy the prompt content
4. Paste into Claude (or ChatGPT for visual-asset-generation)
5. Provide the inputs the prompt asks for

## When to add a prompt to the library

Add to library when:
- You've used the prompt twice
- You expect to use it again
- It produces consistent, high-quality output that's not trivially regenerable

Don't add when:
- The prompt is one-off
- The prompt depends on engagement-specific context that won't be reusable
- The prompt is a refinement of an existing canonical prompt (update existing instead)

## Prompt file structure

Each prompt file contains:

```yaml
---
type: prompt
status: locked | draft
version: x.y.z
last-updated: YYYY-MM-DD
---
```

Then:

1. **Purpose** — what this prompt produces
2. **When to use** — trigger conditions
3. **Inputs needed** — what to paste in
4. **Output specification** — what the AI produces
5. **The prompt itself** — verbatim, copy-paste ready, in a fenced code block

## Maintenance

Quarterly garage-sale ritual reviews the prompt library: which prompts are stale, which need version bumps, which should be deprecated.
