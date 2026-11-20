---
name: faithworkz-agent-terminal
description: Keeps Abel's Private Agent Terminal dashboard current and handles its chat commands - "run sweep", "pause <agent>", "resume <agent>", "new agent for <project>", "show queue". Use when Abel types one of these commands or on the daily 09:00 IST sweep.
---

# Private Agent Terminal

The control room for the Super Agent and the Faithworkz pipeline. Private to Abel.

## Spec

| Field | Value |
|---|---|
| Name | Private Agent Terminal |
| Purpose | One place for Abel to see every project, agent, queued post, approval, error and weekly metric, and to steer agents from chat. |
| Trigger / schedule | Daily sweep 09:00 IST; also on every command below. |
| Inputs | Project Registry (Sheets artifact); agent run log; content queue; approvals; error log; post metrics. |
| Tools | Artifact data store (`ArtifactData`) for the dashboard; Claude Docs connector for the Registry sheet; scheduled tasks (pause/resume). |
| Output | Updated dashboard at the Terminal URL; a daily brief of 12 lines or fewer to Abel. |
| Approval gate | `new agent for <project>` only drafts a spec; creating the agent (skill + scheduled task) waits for Abel's yes. More than 2 new agents per sweep always need Abel's approval. |
| Success metric | Dashboard never more than 24 h stale; every command answered in one turn. |

Links (private):
- Terminal: https://claude.ai/artifact/QyRewWiPmNfEbo49tGq5ax
- Project Registry: https://claude.ai/artifact/9nZmLx3kR2dLGPhuJaSCz8

## Commands

| Command | What happens |
|---|---|
| `run sweep` | Discover projects (Notion, Drive, Gmail, Calendar), update the Registry, run due agents, refresh the dashboard, send the daily brief. |
| `pause <agent>` | Disable that agent's scheduled task; mark it `Paused` on the dashboard. |
| `resume <agent>` | Re-enable the scheduled task; mark it `Active`. |
| `new agent for <project>` | Write an Agent Spec (Name, Purpose, Trigger, Inputs, Tools, Output, Approval gate, Success metric) and ask Abel to approve. |
| `show queue` | List posts by stage: Idea, Draft, Awaiting approval, Scheduled, Posted, Rejected. |

## Where updates go

Daily brief, approval packs and alerts go to the WhatsApp group "Zoe Life · Agent Updates" (120363413269450366@g.us) through Blueticks, created 20 Nov 2026. Fallback: email to abel@zoelife.co. Never add anyone else to the group without Abel's approval.

## Daily brief format (12 lines or fewer)

1. Moved: what changed since yesterday.
2. Blocked: what is stuck and on whom.
3. Needs your decision: numbered, one line each.
4. New agents proposed.

Every status line must come from a tool result from this sweep. If a tool fails twice, say which step was skipped.
