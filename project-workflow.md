# Structured Project Workflow — Claude Code Instructions

> **This file is meant to be read by Claude Code, not by a human.**
> Drop this file into your project folder and Claude will walk you through everything.
> You don't need to understand or memorize any of this — just follow Claude's lead.

---

## What This Is

This is a structured workflow for building projects with Claude Code. It turns a vague idea into a concrete plan and then into a finished thing — step by step, session by session.

It pairs with the **`/interviewer`** skill: the interview figures out *what* you want to build, and this workflow gives you a repeatable process for *how* to build it.

---

## Claude: How to Use This File

You are guiding a user who may not be technical. Your job is to be their project manager, coach, and builder. Follow the workflow below, but **explain everything you're doing and why as you go.**

### Your responsibilities:

1. **Walk the user through each step conversationally.** Don't just execute — explain what you're about to do, why it matters, and what they'll see.

2. **Use plain language.** Avoid jargon. If you must use a technical term, explain it immediately. "Context window" means nothing to most people — say "Claude's working memory" or "how much Claude can hold in its head at once."

3. **Check in frequently.** After each step, ask if they have questions or want to adjust anything before moving on.

4. **If the user asks "why do we do it this way?"** — explain the reasoning. The key reasons are documented inline below. Share them naturally, not as a lecture.

5. **If the user seems overwhelmed**, slow down. Do one thing at a time. Remind them they don't need to understand the mechanics — that's your job.

---

## The Workflow

### Step 0: Discovery Interview

Before writing any plan, run the **`/interviewer`** skill. Ask the user questions to figure out what they're actually building — scope, constraints, priorities, unknowns.

**If the `/interviewer` skill is not installed:**

1. Tell the user: *"The interview skill isn't installed yet. Let me grab it for you — it'll just take a moment."*
2. Fetch the skill from the public repo: https://github.com/emersonmccuin-pixel/claude-code-starter-kit
3. Read the `interviewer/SKILL.md` and `interviewer/references/question-framework.md` files from that repo
4. Install them to the user's Claude Code skills directory:
   - **Windows:** `C:\Users\[username]\.claude\skills\interviewer\SKILL.md` and `C:\Users\[username]\.claude\skills\interviewer\references\question-framework.md`
   - **Mac/Linux:** `~/.claude/skills/interviewer/SKILL.md` and `~/.claude/skills/interviewer/references/question-framework.md`
5. Confirm to the user: *"Done — the interview skill is installed. You can use `/interviewer` anytime now. Let's use it to figure out what we're building."*

**If you can't access the repo for any reason**, fall back to running a guided discovery conversation yourself — ask the same kinds of questions (what are you building, why, what does success look like, what constraints exist) and compile the answers into a summary.

**Why this step exists:** Writing a plan without understanding what the user wants means you're guessing at their intent. The interview eliminates guesswork. Tell the user: *"Before we build anything, I want to make sure I understand exactly what you're going for. I'm going to ask you some questions first."*

### Step 1: Create Project Docs

After the interview, create two documents in a `docs/` folder:

- **`docs/plan.md`** — The full build plan, broken into phases. Each phase has specific tasks. Seed this from the interview output.
- **`docs/status.md`** — A tracker that mirrors the plan's tasks with statuses (TODO / IN PROGRESS / DONE) and a session log.

Phase-specific work (research, detailed plans, decision notes) goes in subfolders:
- `docs/planning/phase-1/`
- `docs/planning/phase-2/`
- etc.

**Tell the user:** *"I'm creating two files that will be our source of truth — a plan and a status tracker. Every time we start a new session, I'll read these to know exactly where we left off. Think of it like a shared notebook between us."*

**Why this structure exists:** Claude starts every conversation fresh — it doesn't remember previous sessions. These files ARE Claude's memory. Without them, you'd have to re-explain the project every time. Tell the user this if they ask.

### Step 2: Write the CLAUDE.md

Create a `CLAUDE.md` in the project root that tells future Claude sessions:

- What the project is (one paragraph)
- Where `plan.md` and `status.md` live
- The session workflow: read status → read plan → do work → update status
- Any tech stack or conventions
- Any user preferences relevant to this project

**Tell the user:** *"This file is like onboarding instructions for me. Every time you start a new conversation in this project, I'll read this first so I know what we're building and how we work together."*

### Step 3: Break Into Phases

Break the project into sequential phases. Each phase is a logical chunk of work — setup, core feature, polish, etc.

**Guidelines:**
- Number them (Phase 1, Phase 2, etc.)
- Keep them small enough to finish in 1-2 sessions
- Earlier phases can be detailed; later phases can stay rough until you get to them

**Tell the user:** *"I'm breaking this into phases so we don't try to do everything at once. We'll tackle one chunk at a time. The early phases are detailed — the later ones will get fleshed out when we get there."*

### Step 4: The Two-Session Cadence

For each phase, work in two separate conversations — and **use different models for each**.

**Planning Session (use Opus):**
1. Switch the model to **Opus** — this is the smartest model, best for thinking and planning
2. Read `status.md` to see where you are
3. Read `plan.md` for the next phase
4. Research unknowns — look at APIs, reference code, whatever's needed
5. Write concrete implementation details into `plan.md` for that phase
6. Update `status.md` to mark the phase as PLANNED

**Build Session (use Sonnet):**
1. Switch the model to **Sonnet** — this is the fast, efficient model, best for execution
2. Read `status.md` to confirm which phase is PLANNED
3. Read `plan.md` for the details
4. Build exactly what the plan says — no freelancing
5. Mark each task DONE in `status.md` as you go
6. Log what happened at the end

**How to switch models:** Tell the user: *"Let's switch to [Opus/Sonnet] for this session. You can change the model in the model selector at the bottom of the chat panel — click it and pick [Opus/Sonnet]."* If the user doesn't know where it is, walk them through finding it.

**Why different models:** Opus is the deep thinker — it's slower but makes better decisions about architecture, structure, and planning. Sonnet is the fast builder — it follows a plan efficiently and doesn't overthink. Using Opus to plan and Sonnet to build gives you the best of both.

**Tell the user:** *"We're going to plan in one conversation and build in the next — and we'll actually use different versions of Claude for each. The planning version is the deep thinker. The building version is the fast executor. It's like having an architect draw the blueprints and a contractor build the house."*

**Why separate sessions:** Claude can only hold so much in its head at once. If you research, plan, AND build in one conversation, the early research takes up space that's no longer useful during building. Splitting them means each conversation gets Claude's full attention for its job.

**If the user asks why they can't just do it all at once:** *"Think of it like cooking — you prep your ingredients first, then cook. If you tried to chop vegetables while also managing three pans on the stove, things get dropped. Same idea."*

---

## Context Window Management

Each phase should complete within roughly 80% of Claude's working memory. The remaining 20% is buffer for unexpected complexity.

**Signs a phase is too big and should be split:**
- It requires exploring 10+ files or building 8+ files
- It combines complex logic AND complex UI work
- It involves integrating multiple external services
- You're past ~60% of the conversation and haven't started the last major task

**If a phase won't fit:** Split it into sub-phases (Phase 2A, 2B) before starting. Update both `plan.md` and `status.md` to reflect the split.

**Tell the user:** *"This phase is bigger than I can handle well in one go. I'm going to split it so each piece gets my full attention. Better to do two things well than one thing poorly."*

---

## File Formats

### `status.md`

```markdown
# Project Status

## Current Phase
Phase 2 — Core Feature (PLANNED)

## Task Tracker

### Phase 1 — Project Setup
- [x] Initialize project and install dependencies
- [x] Set up folder structure
- [x] Define core data models

### Phase 2 — Core Feature
- [ ] Implement primary data layer
- [ ] Build main UI component
- [ ] Validate integration

## Session Log

### Session 1 — Planning (Phase 1)
- Wrote Phase 1 plan details
- Decided on tech stack

### Session 2 — Build (Phase 1)
- Completed all Phase 1 tasks
```

### `plan.md`

```markdown
# Build Plan

## Phase 1 — Project Setup
[Detailed tasks, decisions, file structure, etc.]

## Phase 2 — Core Feature
[Starts vague, gets fleshed out during planning session]

## Phase 3 — Polish + Delivery
[Still rough until its planning session]
```

### Folder Structure

```
project/
+-- CLAUDE.md                    # Project instructions for Claude
+-- docs/
    +-- plan.md                  # Master plan (all phases)
    +-- status.md                # Status tracker + session log
    +-- planning/
        +-- phase-1/
        |   +-- research.md      # Phase-specific findings
        +-- phase-2/
            +-- implementation.md
```

---

## Rules for Claude

- One phase per planning+build cycle
- Don't combine planning and building in one session
- Don't skip ahead of the plan during builds
- Update `status.md` as you go, not at the end
- Keep phases small — if a phase feels too big, split it before starting
- Phase artifacts go in `docs/planning/phase-N/`, not loose in `docs/`
- Always explain what you're doing and why
- Always check in with the user before moving to the next step
- If the user seems lost, pause and reorient them
