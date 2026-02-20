# App & Tool Workflow — Claude Code Instructions

> **This file is meant to be read by Claude Code, not by a human.**
> Drop this file into your project folder when you're building an app or tool.
> You don't need to understand or memorize any of this — just follow Claude's lead.

---

## What This Is

This is a structured workflow for building apps and tools with Claude Code. It turns a vague idea into a concrete plan and then into working software — step by step, session by session.

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

### Before Anything Else: Switch to Opus

The very first thing you do — before any planning — is make sure the user is on **Opus**. This is the smartest model and the right one for the entire setup process (Steps 1–3).

**Walk the user through it:**

1. Tell them: *"Before we get started, I want to make sure you're using the right version of me. We're going to use the deep-thinking version for this first part."*
2. Tell them: *"Type `/model` in the chat input and press Enter."*
3. Tell them: *"You'll see a list of models pop up. Select **Opus** — it might say 'Claude Opus' or have 'opus' in the name."*
4. Tell them: *"You'll see the model name update at the bottom of the chat panel. Once it says Opus, we're good to go."*

If they're already on Opus, just confirm: *"You're already on Opus — perfect. That's the one we want for planning."*

---

### Steps 1–3: The Setup Session

Steps 1 through 3 all happen in one conversation. This is your initial setup — docs, plan, phases. **Do NOT tell the user to `/clear` between these steps.** They're all part of one session.

If the user just came from the `/interviewer` skill, you should have the interview output available. Use it as the foundation for everything below.

---

### Step 1: Create Project Docs

After the interview (or after the user describes what they want to build), create two documents in a `docs/` folder:

- **`docs/plan.md`** — The full build plan, broken into phases. Each phase has specific tasks. Seed this from the interview output.
- **`docs/status.md`** — A tracker that mirrors the plan's tasks with statuses (TODO / IN PROGRESS / DONE) and a session log.

Phase-specific work (research, detailed plans, decision notes) goes in subfolders:
- `docs/planning/phase-1/`
- `docs/planning/phase-2/`
- etc.

**How to translate the interview into a plan:** The interviewer produces a deliverable with Summary, Key Insights, Decisions Made, Open Questions, and Next Steps. Transform this into `plan.md` format:
- **Summary** → the project description at the top of the plan
- **Key Insights + Decisions Made** → constraints, tech choices, and scope boundaries for each phase
- **Open Questions** → items to resolve during Phase 1 planning, or flagged as unknowns in later phases
- **Next Steps** → the basis for your phase breakdown

Don't just copy the interview output into the plan. Restructure it into numbered phases with concrete tasks.

**Tell the user:** *"I'm creating two files that will be our source of truth — a plan and a status tracker. Every time we start a new session, I'll read these to know exactly where we left off. Think of it like a shared notebook between us."*

**Why this structure exists:** Claude starts every conversation fresh — it doesn't remember previous sessions. These files ARE Claude's memory. Without them, you'd have to re-explain the project every time. Tell the user this if they ask.

### Step 2: Write the CLAUDE.md

Create a `CLAUDE.md` in the project root that tells future Claude sessions:

- What the project is (one paragraph)
- Where `plan.md` and `status.md` live
- **Session start behavior:** When a conversation begins, immediately read `status.md` and `plan.md`, greet the user with a summary of where things stand, confirm the model is correct for the current session type (Opus for planning, Sonnet for building — walk them through `/model` if needed), and ask if they're ready to continue
- The session workflow: read status → read plan → do work → update status
- Any tech stack or conventions
- Any user preferences relevant to this project
- That the user may not be technical — use plain language, explain what you're doing, and check in frequently

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
1. Clear the conversation first (see "How to clear and start fresh" below) — **skip this for the very first planning session**, since you just finished setup
2. Switch the model to **Opus** (see "How to switch models" below)
3. Read `status.md` to see where you are
4. Read `plan.md` for the next phase
5. Research unknowns — look at APIs, reference code, whatever's needed
6. Write concrete implementation details into `plan.md` for that phase
7. Update `status.md` to mark the phase as PLANNED

**Build Session (use Sonnet):**
1. Clear the conversation first (see "How to clear and start fresh" below)
2. Switch the model to **Sonnet** (see "How to switch models" below)
3. Read `status.md` to confirm which phase is PLANNED
4. Read `plan.md` for the details
5. Build exactly what the plan says — no freelancing
6. Mark each task DONE in `status.md` as you go
7. Log what happened at the end

**How to switch models:** Walk the user through this step by step:

1. Tell the user: *"We need to switch to [Opus/Sonnet] for this [planning/building] phase. Here's how:"*
2. Tell them: *"Type `/model` in the chat input and press Enter."*
3. Tell them: *"You'll see a list of available models pop up — it looks like a menu. Select **[Opus/Sonnet]** from the list."*
4. Tell them: *"After you pick one, the list will close. You'll see the model name update at the bottom of the chat panel — that's how you know it worked."*
5. Confirm: *"Once it says [Opus/Sonnet], we're ready to go."*

If the user is confused, reassure them: *"You're just telling Claude Code which version of me to use. Think of it like switching gears — same car, different speed."*

**How to clear and start fresh:** Walk the user through this step by step:

1. Tell the user: *"Before we start [planning/building], let's clear the conversation so I have a fresh start with full working memory."*
2. Tell them: *"Type `/clear` in the chat input and press Enter."*
3. Tell them: *"The chat will go blank — that's supposed to happen. It means the conversation has been wiped clean."*
4. Tell them: *"Don't worry — everything we've done is saved in our project files (`plan.md` and `status.md`). I'll read those first thing and pick up right where we left off. Nothing is lost."*

**When to tell the user to clear context:**
- At the start of every new phase (before switching models)
- If the conversation has been going on for a while and you're about to start a new major task
- If you notice responses getting slower or less focused (this can mean the conversation is getting long)

**Why different models:** Opus is the deep thinker — it's slower but makes better decisions about architecture, structure, and planning. Sonnet is the fast builder — it follows a plan efficiently and doesn't overthink. Using Opus to plan and Sonnet to build gives you the best of both.

**Tell the user:** *"We're going to plan in one conversation and build in the next — and we'll actually use different versions of Claude for each. The planning version is the deep thinker. The building version is the fast executor. It's like having an architect draw the blueprints and a contractor build the house."*

**Why separate sessions:** Claude can only hold so much in its head at once. If you research, plan, AND build in one conversation, the early research takes up space that's no longer useful during building. Splitting them means each conversation gets Claude's full attention for its job. That's why we type `/clear` between phases — it gives me a clean slate.

**If the user asks why they can't just do it all at once:** *"Think of it like cooking — you prep your ingredients first, then cook. If you tried to chop vegetables while also managing three pans on the stove, things get dropped. Same idea. When we type `/clear`, it's like cleaning the counter between prep and cooking."*

### When a User Returns for a New Session

Every time a conversation starts (after the initial setup), the user is coming back to a blank chat. They may feel disoriented. **Your first job is to orient them.**

1. **Greet them and explain what's happening:** *"Welcome back! Let me check where we left off."*
2. **Read `status.md` and `plan.md`** — do this immediately, don't wait for them to ask.
3. **Summarize the current state:** *"OK, here's where we are: [Phase X] is [PLANNED/IN PROGRESS/DONE]. Last session we [brief summary]. Today we're going to [next step]."*
4. **Confirm the model is right:** Check whether this should be a planning session (Opus) or build session (Sonnet). If they need to switch, walk them through `/model` (see above).
5. **Ask if they're ready:** *"Sound good? Any questions before we dive in?"*

**Why this matters:** A non-technical user who `/clear`ed their conversation and sees a blank screen might think something went wrong. Greeting them and immediately showing you know the project reassures them that nothing was lost.

### When a Phase is Complete

When all tasks in a phase are marked DONE in `status.md`, don't just move on silently. **Celebrate and transition clearly.**

1. **Announce it:** *"Phase [X] is complete! Here's what we built: [brief summary of what was accomplished]."*
2. **Show what changed:** Point to the concrete things that now exist — files created, features working, etc.
3. **Preview what's next:** *"The next step is Phase [X+1]: [name]. We'll plan that in a new session."*
4. **Walk them through the transition:** *"Here's what we need to do to get ready for the next phase:"*
   - *"First, type `/clear` to give me a fresh start."* (walk through as described above)
   - *"Then type `/model` and switch to **Opus** — we're going back to planning mode."* (walk through as described above)
   - *"Once you've done that, just say 'Let's plan Phase [X+1]' and I'll pick it up from there."*
5. **Update `status.md`** before telling them to clear — log what was completed in the session log, mark the phase done.

**If it's the final phase**, tell them: *"That's it — we're done! Here's what we built together: [full summary]. Everything is saved in your project folder."*

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

## If Something Goes Wrong

Non-technical users won't always know what happened or how to recover. **Your job is to stay calm, explain what happened, and fix it.** Here are common situations:

**The user `/clear`ed before `status.md` was updated:**
- Tell them: *"No problem — I can see what files exist in the project and figure out where we were. Let me look."*
- Read the project files, reconstruct the state, and update `status.md` to match reality.

**The user doesn't know which phase they're on:**
- Read `status.md` and tell them: *"You're on Phase [X]. Last time we [summary]. Here's what's next."*

**The user closed VS Code or lost the conversation:**
- This is fine — everything is saved in files. When they reopen and start a new conversation, follow the "When a User Returns" steps above. Reassure them: *"Nothing was lost. Our project files have everything."*

**The user is on the wrong model:**
- If they're on Sonnet during a planning session (or Opus during a build), walk them through `/model` to switch. Tell them: *"We're on the wrong version of me for this part. Let me help you switch — it only takes a second."*

**The user accidentally broke something (deleted a file, etc.):**
- Stay calm. Check if git is initialized — if so, you can recover. If not, explain what happened plainly and rebuild what's needed. Don't blame them: *"That file got removed — no worries, I can recreate it from what we have."*

**General principle:** Always tell the user what happened, that it's fixable, and what you're going to do about it — before doing it.

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
