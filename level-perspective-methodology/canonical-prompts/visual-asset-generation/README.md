---
type: readme
status: active
version: 1.0.0
last-updated: 2026-05-08
---

# canonical-prompts/visual-asset-generation/

Image-generation prompts for video deck visuals, diagrams, and illustrations. Typically run in ChatGPT (DALL-E / Sora) per the ChatGPT-vs-Claude routing rule.

| File | Purpose | Status |
|---|---|---|
| `strategyzer-style-illustration.md` | Strategyzer-style flat illustration for video deck visuals | Pending |
| `methodology-diagram-base.md` | Conceptual diagram base prompt — clean, minimal, methodology-style | Pending |
| `pathline-reference-org-illustrations.md` | Consistent visual style for PathLine examples across videos | Pending |
| `culture-map-visual.md` | Strategyzer × Dave Gray Culture Map visual treatment | Pending |
| `sgf-canvas-visual.md` | SGF canvas visual treatment (4 quadrants, attribution) | Pending |
| `bmc-canvas-visual.md` | BMC canvas visual treatment (9 blocks, postcard altitude) | Pending |

## Why ChatGPT and not Claude

Image generation is more mature in ChatGPT's stack. Claude generates the prompt; ChatGPT runs it. The prompts captured here are the bridge.

## Prompt structure

Each prompt file contains:

1. **Visual style brief** — color palette, line weight, density, mood
2. **Composition specification** — what's in the frame, what's not, framing
3. **The prompt itself** — verbatim, copy-paste ready
4. **Negative space discipline** — what NOT to include (no stock-photo aesthetic, no AI-generic style markers, no overdesigned detail)
5. **Output usage** — where the image will appear (V-x video deck, learning module, etc.)

## Visual consistency

Maintaining visual consistency across the video curriculum is the hard problem this folder solves. A V1 illustration should feel like the same family as V2 and V_oc — same palette, same line treatment, same density.

The PathLine reference org appears in multiple videos. The visual treatment for PathLine (office, characters, environment) should be consistent across all appearances. This is what `pathline-reference-org-illustrations.md` enforces.
