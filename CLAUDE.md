# Personal OS

This is your personal operating system for managing tasks, context, and automation with Claude Code.

<!-- FIRST-RUN DETECTION:
     If the About You section still contains "[Your name]", this is a fresh install.
     Run the /setup skill immediately to guide the user through interactive setup.
     Do NOT show a help wall or feature list. Just start the setup conversation. -->

<!-- ============================================================
     HOW THIS FILE WORKS

     Claude Code automatically reads CLAUDE.md at project root.
     This file is your "router" — it tells Claude:
       1. Who you are (so it has context)
       2. Where to find information (routing table)
       3. How to behave (guidelines)
       4. What workflows exist (skills)

     You can also have a global CLAUDE.md at ~/.claude/CLAUDE.md
     for instructions that apply across ALL projects. Put portable
     preferences there (communication style, hard rules) and
     project-specific routing here.
     ============================================================ -->

## About You

<!-- CUSTOMIZE: Replace this section with your own context.
     The more specific you are, the better Claude can help. -->

- **Name:** [Your name]
- **Role:** [What you do — e.g., "Product Manager at Acme Corp"]
- **Location:** [City]
- **Key context:** [2-3 sentences about what makes your situation unique — current projects, career stage, what you're building toward]

## Current Priorities

<!-- CUSTOMIZE: List your top priorities in order.
     These drive task recommendations and daily briefings.
     Update these whenever your focus shifts. -->

1. **[Primary focus]** — [Brief description of what this is and why it matters]
2. **[Second priority]** — [Brief description]
3. **[Third priority]** — [Brief description]
4. **[Fourth priority]** — [Brief description]

## Directory Structure

```
/tasks/          — Individual task files (YAML front matter)
/tasks/archive/  — Completed tasks organized by YYYY-MM
/ideas/          — Ideas and projects you're thinking about (no pressure to act)
/llm-context/    — Context files by domain (work, personal, side-project, people, etc.)
.claude/skills/ — Reusable workflows (slash commands: /today, /commit, /debrief...)
/research/       — Paper summaries by topic
/learning/       — Learning plans, logs, and skill development tracking
```

## Context Routing

<!-- CUSTOMIZE: Map your domains to context files.
     Add rows as you create new context areas.
     Claude uses this table to know what to load for each topic. -->

Load relevant context based on what you ask:

| If asking about... | Load... |
|-------------------|---------|
| Work, job, day-to-day role | `/llm-context/work/index.md` |
| Personal life, health, goals | `/llm-context/personal/index.md` |
| Side project | `/llm-context/side-project/index.md` |
| A specific person | `/llm-context/people/[name].md` |
| Goals, priorities | `/llm-context/goals.md` |
| Past decisions | `/llm-context/decisions.md` |
| How this OS works | `/llm-context/your-os/design-philosophy.md` |
| Writing/drafting a message | `.claude/skills/your-voice/SKILL.md` + `llm-context/references/examples.md` + `/llm-context/people/[recipient].md` |
| Task prioritization, what to work on | `/llm-context/goals.md` then `/tasks/*.md` |

<!-- ADD YOUR OWN DOMAINS:
| Job search, applications, interviews | `/llm-context/job-search/index.md` |
| [Company name], role context | `/llm-context/[company]/index.md` |
| Community events, meetups | `/llm-context/community/index.md` |
-->

## Skills

Reusable workflows live in `.claude/skills/`. Each skill is a directory with a `SKILL.md` file and is invokable as a slash command — type `/skill-name` to run it directly, or describe what you need and Claude will load the right skill automatically.

<!-- CUSTOMIZE: Add your own skills by creating .claude/skills/<name>/SKILL.md.
     The directory name becomes the slash command. -->

| Slash Command | File | Trigger |
|--------------|------|---------|
| `/today` | `.claude/skills/today/SKILL.md` | "What's on for today?" |
| `/next` | `.claude/skills/task-recommend/SKILL.md` | "What should I work on?", "What's next?" |
| `/catchup` | `.claude/skills/catchup/SKILL.md` | "What did I miss?", "Catch me up" |
| `/review` | `.claude/skills/weekly-review/SKILL.md` | "How did this week go?" |
| `/debrief` | `.claude/skills/debrief/SKILL.md` | "I just met with...", "Debrief on..." |
| `/call-prep` | `.claude/skills/call-prep/SKILL.md` | "Prep me for [meeting]", "Brief me on [person]" |
| `/incoming-comms` | `.claude/skills/incoming-comms/SKILL.md` | Pasted text from an email, Slack, DM, or any communication without a specific question |
| `/process-meetings` | `.claude/skills/process-meetings/SKILL.md` | Meeting transcript dropped |
| `/session-end` | `.claude/skills/session-end/SKILL.md` | "What did we learn today?" — only for sessions with significant strategic or personal content |
| `/profile` | `.claude/skills/profile-update/SKILL.md` | End of substantive session |
| `/your-voice` | `.claude/skills/your-voice/SKILL.md` | Writing any communication — emails, Slack, LinkedIn, professional messages |
| `/voice-critic` | `.claude/skills/voice-critic/SKILL.md` | Automatically before outward-facing drafts |
| `/copywriting` | `.claude/skills/copywriting/SKILL.md` | "Write copy for...", "Draft landing page copy" |
| `/critique` | `.claude/skills/landing-page-critique/SKILL.md` | "Critique this page", "Review the landing page" |
| `/commit` | `.claude/skills/commit/SKILL.md` | "Commit this", "Commit my changes" |
| `/new-project` | `.claude/skills/new-project/SKILL.md` | "Let's build X", "Start a project" |
| `/task-create` | `.claude/skills/task-create/SKILL.md` | Casual mention of a task, "I need to..." |
| `/task-complete` | `.claude/skills/task-complete/SKILL.md` | "Mark [task] done", "I finished [task]" |
| `/interview-prep` | `.claude/skills/interview-prep/SKILL.md` | "Prep me for [company] interview" |
| `/outreach` | `.claude/skills/relationship-building/SKILL.md` | "Reach out to [person]" |
| `/pre-flight` | `.claude/skills/pre-flight/SKILL.md` | Auto on strategy sessions and multi-step deliverables |
| `/friction` | `.claude/skills/friction-log/SKILL.md` | "That was annoying", "Log friction" |
| `/paper-summary` | `.claude/skills/paper-summary/SKILL.md` | "Summarize this paper" |
| `/event-checklist` | `.claude/skills/event-checklist/SKILL.md` | "Set up a checklist for [event]" |
| `/post-event` | `.claude/skills/post-event/SKILL.md` | "How did the event go?" |
| `/health` | `.claude/skills/health/SKILL.md` | "System health", "How's the OS?" |
| `/import-chats` | `.claude/skills/import-chats/SKILL.md` | "Import my chats", "Organize my chat history" |
| `/setup` | `.claude/skills/setup/SKILL.md` | Auto-triggered on first run when `[Your name]` placeholder detected |

## People File Template

When creating new people files, use the template at `llm-context/templates/people-template.md`. All people files should have consistent structure: Basic Info table, How We Met, Context, Relationship History, Open Threads, and Notes.

## Task Format

Files in `/tasks/` use this structure:

```yaml
---
type: task | idea | bug
due: YYYY-MM-DD
tags: [domain, action-type]
status: todo | in-progress | done | blocked
---

[Description and notes]
```

## Tag Taxonomy

<!-- CUSTOMIZE: Replace these with your own domains and action types. -->

### Domains
- work
- personal
- side-project

### Action Types
- research
- write
- outreach
- build
- review
- follow-up

## Auto-Processing Triggers

These triggers fire automatically — you should never have to say "process this" or "update context."

| When you... | Automatically... |
|-------------|-----------------|
| Paste raw text from a message/email/DM without a question | Run `/incoming-comms` — triage, draft response, update all affected files |
| Say "prep me for [call/meeting with person]" | Run `/call-prep` — load person file, domain context, open tasks, active decisions → output briefing |
| Mention a new person by name with context | Create people file immediately from template |
| Complete work that overlaps with an open task | Archive the task and report |
| Have a substantive exchange on any topic | Update all affected context files in `/llm-context/` immediately |

## Behavioral Rules

**Full behavioral guidelines live in `.claude/skills/behaviors/SKILL.md`.** Load when context management, proactive nudges, or auto-routing questions arise.

**Key behaviors (always active):**
- Update context files in real-time after substantive exchanges — don't ask, just update and report
- Search existing context before asking for information
- Auto-create people files when new contacts are mentioned
- Auto-close tasks when work clearly completes them

## Hooks (Enforced by Shell)

<!-- Hooks are shell scripts that run automatically before or after Claude uses a tool.
     They enforce safety rules and keep the system in sync without relying on prompts alone.

     Configuration lives in .claude/settings.json. Three included hooks ship with this template:

     bash-guard.sh         — blocks destructive commands (rm -rf, force push, etc.)
     context-sync-nudge.sh — reminds Claude to check for ripple effects after context edits
     transcript-detector.sh — detects meeting transcripts and prompts processing

     OPTIONAL: If you add MCP tools for email/Slack/calendar, consider adding a send-guard
     hook that blocks outbound communication tools. You always want to send your own messages.
     See the README for an example send-guard.sh. -->

| Hook | Event | What it does |
|------|-------|-------------|
| `bash-guard.sh` | PreToolUse (Bash) | Blocks `rm -rf`, `git push --force`, etc. |
| `context-sync-nudge.sh` | PostToolUse (Write/Edit) | Nudges ripple-effect check on `/llm-context/` edits |
| `transcript-detector.sh` | PostToolUse (Bash/Write) | Detects meeting transcripts and prompts processing |

## Writing Voice

**Trigger:** Any time Claude is writing words that will come from you to another person — emails, Slack, DMs, LinkedIn, everything.

**Before every draft:**
1. Read `.claude/skills/your-voice/SKILL.md` and `llm-context/references/examples.md`
2. Load the recipient's people file if one exists
3. Match register to channel (Slack DM ≠ exec email ≠ LinkedIn post)

**For high-stakes content** (LinkedIn, exec memos, outreach): run `/voice-critic` on the draft.

## Hard Rules

<!-- CUSTOMIZE: Add your own non-negotiable rules here. -->

1. **NEVER send emails, messages, or any external communication without explicit approval.** Draft first, confirm, then you send manually.
2. **NEVER offer to send things.** You send your own messages. Claude only drafts.
3. **NEVER take actions visible to others without confirmation.** Calendar events with attendees, shared documents, external posts — always ask first.
