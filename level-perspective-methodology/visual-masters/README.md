---
type: readme
status: active
version: 1.0.0
last-updated: 2026-05-08
---

# visual-masters/

**This folder contains URL indexes only. The actual visual masters live in Figma, FigJam, Loop, or SharePoint.**

This repo is text-native. Visual files (Figma, FigJam, Loop projects, recorded videos, MP4 exports, PNG exports) are not stored here. They live in their native cloud tools, and this folder maintains the index of canonical URLs.

| File | Index of | Status |
|---|---|---|
| `figma-links.md` | Figma design files (async prep canvas mocks, presentation visuals) | Pending |
| `figjam-links.md` | FigJam operational canvases (async prep workbooks, sync session live boards) | Pending |
| `loop-links.md` | Loop projects (video drafts, recorded videos) | Pending |
| `sharepoint-binary-exports.md` | SharePoint paths to MP4 recordings and PDF exports | Pending |

## Source-of-truth rule

| Artifact | Source-of-truth lives in | Index URL captured here |
|---|---|---|
| Figma design file | Figma cloud | `figma-links.md` |
| FigJam canvas | FigJam cloud | `figjam-links.md` |
| Loop video draft | Loop cloud | `loop-links.md` |
| Recorded MP4 video | SharePoint | `sharepoint-binary-exports.md` |
| Exported PDF / PNG | SharePoint | `sharepoint-binary-exports.md` |

This separation is intentional. Git is not a binary-file storage system; trying to make it one creates pain. The repo is the source-of-truth for *text* (specs, prompts, scripts) and the *index* for visuals.

## Link integrity

Visual master URLs in this index get checked weekly by the link-integrity-check ritual (canonical prompt in `/canonical-prompts/daily-ops/`). Broken links surface during the Friday close.

When a Figma file is renamed or moved, the URL in this index needs updating. Claude can do this automatically if you tell it about the move.

## Per-engagement visuals

Per-engagement live FigJam canvases (created by duplicating a master at engagement start) are NOT indexed here. They live in per-engagement Figma projects and are referenced from the engagement workspace (Claude Project + SharePoint engagement folder).
