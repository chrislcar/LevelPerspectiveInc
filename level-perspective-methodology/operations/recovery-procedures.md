---
type: doctrine
status: locked
version: 1.0.0
last-updated: 2026-05-08
---

# Recovery procedures

What to do when a layer of the system fails. Solo operators with no backup of their methodology IP are one mistake from ruin; this document exists to prevent that.

## Failure mode index

| Scenario | Severity | Recovery section |
|---|---|---|
| Claude account locked or suspended | High (operations stop) | [§1 Claude unavailable](#1-claude-unavailable) |
| GitHub repo deleted or corrupted | Critical (IP at risk) | [§2 GitHub failure](#2-github-failure) |
| M365 tenant locked (SharePoint, OneNote, Loop all down) | High | [§3 M365 unavailable](#3-m365-unavailable) |
| Open Brain unavailable | Medium | [§4 Open Brain unavailable](#4-open-brain-unavailable) |
| Maintainer (you) unavailable for >2 weeks | High (engagement risk) | [§5 Maintainer unavailable](#5-maintainer-unavailable) |
| Local Mac fails / lost | Medium | [§6 Local device loss](#6-local-device-loss) |
| MCP rate limits hit during heavy authoring | Low | [§7 MCP rate limit](#7-mcp-rate-limit) |

---

## 1. Claude unavailable

**Symptoms:** Claude account locked, suspended, service outage, MCP non-responsive.

**Immediate actions:**

1. **Check service status** at status.anthropic.com.
2. **Switch to web UI** if it's an MCP issue specifically — direct conversation still works.
3. **Operate the repo manually:**
   - Browse via GitHub web UI
   - Edit via VS Code (Source Control panel handles commits without terminal)
   - Or use GitHub Desktop for visual Git operations
4. **For methodology authoring,** ChatGPT can substitute temporarily for narrow tasks (drafting, refinement). Do not transfer doctrine work; Claude has the project knowledge ChatGPT does not.

**Workflows that survive without Claude:**
- Reading specs (web UI)
- Direct editing (VS Code)
- Committing changes (VS Code Source Control or GitHub Desktop)
- Reviewing PRs (web UI)
- Running sync sessions (facilitation specs already authored)

**Workflows that pause:**
- New methodology authoring at scale
- AI synthesis runs (the prompts are in the repo; can be run in ChatGPT but with reduced context fidelity)
- Open Brain interactions

**Resume conditions:** Claude available; engagement deliveries can proceed using already-authored specs.

---

## 2. GitHub failure

**Symptoms:** Repo deleted, account locked, force-push gone wrong, GitHub-wide outage.

**Critical: the local clone on your Mac is the primary backup.** Verify it is current at least weekly.

**Immediate actions:**

1. **Do not panic-act.** Force-pushes and deletions can sometimes be recovered through GitHub support within 90 days.
2. **Verify local clone exists and is current:**
   ```
   Open GitHub Desktop → repo should show "No local changes" if clean
   Or open VS Code → Source Control panel should show clean state
   ```
3. **If GitHub is up but repo is corrupted:**
   - Push local clone to a new GitHub repo
   - Update the working repo URL in this README
   - Verify Claude MCP reconnects to the new repo
4. **If GitHub is entirely down:**
   - Continue working in local clone via VS Code
   - When GitHub returns, push accumulated commits

**Backup chain:**
1. Local clone on Mac (continuous, automatic)
2. Weekly ZIP export to SharePoint `Methodology Visual Masters/Repo Backups/`
3. (Optional, future) Mirror to a second Git host (GitLab, Bitbucket, Codeberg)

**Recovery test:** annually, simulate "GitHub repo is gone" and recover from local clone + SharePoint ZIP. Verify the recovered repo is functional.

---

## 3. M365 unavailable

**Symptoms:** SharePoint, OneNote, Loop, or any M365 component down or account-locked.

**Immediate actions:**

1. **Check M365 status** at admin.microsoft.com/servicehealth.
2. **For SharePoint outage during engagement delivery:**
   - Frozen client deliverables are still backed up by M365 itself
   - Engagement comms may need to shift to email temporarily
3. **For OneNote outage:**
   - Use a Markdown file in repo `/scratch/` as fallback for ephemeral notes
   - When OneNote returns, graduate notes back into the canonical OneNote location
4. **For Loop outage:**
   - Defer video recording until restored
   - Recordings already exported to MP4 in SharePoint are unaffected

**Workflows that survive:**
- Methodology authoring (in repo; nothing M365-dependent for core work)
- Claude / Open Brain interactions
- Git operations

**Workflows that pause:**
- Engagement comms via SharePoint
- Ink-based scratch capture
- New video recording

**If M365 account locked:**
- Engage Microsoft support immediately
- If recovery exceeds 48 hours, manually reproduce critical client comms via alternate email
- All methodology IP is unaffected (lives in GitHub, not M365)

---

## 4. Open Brain unavailable

**Symptoms:** Open Brain MCP non-responsive, service down, captures not retrievable.

**Mitigation:** weekly export of Open Brain to `/doctrine/open-brain-export.md` in this repo. Run this ritual every Friday close.

**Immediate actions:**

1. **Reference the repo mirror** at `/doctrine/open-brain-export.md`.
2. **Suspend new Open Brain captures** until service restores; capture in OneNote temporarily, graduate to Open Brain when available.
3. **If outage persists >7 days,** consider whether captured doctrine should migrate to a repo-native format permanently (Markdown files in `/doctrine/`).

---

## 5. Maintainer unavailable

**Solo proprietorship continuity scenario.** If the maintainer is unavailable for >2 weeks (illness, accident, unforeseen circumstance), engagements need to either pause cleanly or hand off.

**Standing protocol — engagements:**

1. Active engagements receive notification within 5 business days. (Emergency contact list in `/operations/emergency-contacts.md`.)
2. Engagements at sync session phase pause; pre-work workbooks remain accessible.
3. Engagements at frozen-deliverable phase are unaffected (deliverables already in SharePoint).

**Standing protocol — methodology layer:**

1. Repo is intact and accessible to anyone with GitHub access (set on emergency-access list in `/operations/emergency-contacts.md`).
2. Methodology can be inherited by a successor consultant with sufficient methodology fluency. The repo's READMEs are sufficient onboarding.
3. Active client engagement contracts have force majeure / continuity clauses.

**Documentation maintained for handoff:**
- This recovery procedures document
- The repo's top-level README
- The Coaching Scoping Guide and Playbook Quality Rubric (in project knowledge)
- The canonical doctrine in `/doctrine/`
- Per-client engagement folders in SharePoint

**Annual review:** confirm emergency contacts are current; confirm successor consultant relationships if any are in place; confirm contract continuity clauses.

---

## 6. Local device loss

**Mac fails, stolen, or unusable.**

**Immediate actions:**

1. Acquire replacement device.
2. Re-clone repo from GitHub (full state recoverable).
3. Re-install VS Code, GitHub Desktop, OneNote, Claude desktop app.
4. Re-authenticate to all cloud services.
5. Verify Claude MCP reconnects to GitHub.

**Time to operational:** 4-6 hours including software install and authentication.

**What is lost:** any uncommitted local changes (typically <1 day of work given Friday-close ritual). Any local-only scratch files outside cloud-synced services.

**Mitigation:** all critical artifacts live in cloud (GitHub, SharePoint, OneNote sync, Figma cloud, Loop cloud). Local Mac is convenience, not source-of-truth.

---

## 7. MCP rate limit

**Symptoms:** Claude reports rate-limit errors when committing to GitHub.

**Immediate actions:**

1. **Batch commits:** ask Claude to prepare the commits as a single batched operation (10-15 files at once) rather than one-at-a-time.
2. **Defer non-urgent commits to Friday close ritual:** the weekly review can absorb a backlog.
3. **For urgent single commits:** use VS Code Source Control panel directly (does not consume MCP quota).

**Resume conditions:** rate limit window resets (typically hourly or daily); resume normal operations.

---

## Annual disaster-recovery test

Once per year, scheduled in calendar:

1. Simulate "Claude unavailable for one week."
2. Simulate "GitHub repo deleted, recovering from local clone."
3. Simulate "M365 account locked for 24 hours."
4. Confirm each procedure works with current tools and accounts.
5. Update this document for any procedural drift.

The test exists because solo operators who haven't tested recovery have not actually planned for failure — they've imagined planning for it.
