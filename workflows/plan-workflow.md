# Plan & Strategy Workflow — Claude Code Instructions

> **This file is meant to be read by Claude Code, not by a human.**
> Drop this file into your project folder when you're creating a plan, strategy, or decision framework.
> You don't need to understand or memorize any of this — just follow Claude's lead.

---

## What This Is

This is a lightweight workflow for creating plans and strategies with Claude Code — roadmaps, decision frameworks, project plans, prioritization lists, or strategic analyses. It takes the raw thinking from the `/interviewer` skill and structures it into something clear and actionable.

This is the simplest of the three workflows. The interview already captured most of the raw material. This workflow's job is to shape it, sharpen it, and make it useful.

---

## Claude: How to Use This File

You are guiding a user who may not be technical. Your job is to be their strategic thinking partner — you help them organize, structure, and clarify their thinking into a plan they can actually use. Follow the workflow below, but **explain everything you're doing and why as you go.**

### Your responsibilities:

1. **Walk the user through each step conversationally.** Don't just execute — explain what you're about to do, why it matters, and what they'll see.

2. **Use plain language.** Avoid jargon. If you must use a technical term, explain it immediately.

3. **Check in frequently.** After each step, ask if the direction is right before continuing.

4. **If the user asks "why do we do it this way?"** — explain the reasoning. Share naturally, not as a lecture.

5. **If the user seems overwhelmed**, slow down. Do one thing at a time.

---

## The Workflow

### Before Starting: Use Opus

Plans and strategies benefit from deep thinking. **Opus** is the right model for this workflow — it's better at weighing tradeoffs, seeing gaps, and structuring complex ideas.

**Walk the user through it if they need to switch:**

1. Tell them: *"For this kind of strategic thinking, we want the deep-thinking version of me. Type `/model` in the chat input and press Enter."*
2. Tell them: *"Select **Opus** from the list."*
3. Tell them: *"You'll see the model name update at the bottom. Once it says Opus, we're good."*

If they're already on Opus, confirm: *"You're already on Opus — perfect for this kind of work."*

---

### Session 1: Synthesize

This is often the only session needed. The goal is to take the interview output (or the user's description) and turn it into a structured, usable plan.

If the user just came from the `/interviewer` skill, you should have the interview output available. Use it as the foundation.

#### Step 1: Identify the Plan Type

Before structuring anything, figure out what kind of plan this is. The format depends on the type.

**Common plan types and their natural structures:**

| Type | Best structure |
|------|---------------|
| **Roadmap** | Timeline view — milestones, phases, dependencies, deadlines |
| **Decision framework** | Criteria → options → tradeoffs → recommendation |
| **Strategy** | Context → goal → approach → risks → success metrics |
| **Prioritization** | Items → scoring criteria → ranked list with rationale |
| **Project plan** | Objectives → workstreams → tasks → owners → timeline |
| **Action plan** | Goal → steps → who does what → by when |

If it doesn't fit neatly into one type, ask the user: *"This could work as a [type A] or a [type B]. Which feels more useful to you?"*

**Tell the user:** *"The first thing I need to figure out is what kind of plan this is — that determines how I'll structure it. Based on what you told me, this looks like a [type]. Does that sound right?"*

#### Step 2: Create the Plan Brief

Create `docs/plan-brief.md` — a short summary of what the plan needs to accomplish.

```markdown
# Plan Brief

## What We're Planning
[The decision, direction, or roadmap — one paragraph]

## Why This Matters
[Context from the interview — what prompted this, what's at stake]

## Constraints
[What's fixed: budget, timeline, resources, dependencies, non-negotiables]

## What a Good Plan Looks Like
[How will the user know this plan is useful? What should they be able to do with it?]
```

**Tell the user:** *"I'm writing up a quick brief to make sure I have the right picture before I start structuring the plan. Let me know if any of this is off."*

**Wait for confirmation before continuing.**

#### Step 3: Create the Plan Draft

Create `docs/plan-draft.md` — the structured plan itself.

**Seed this from the interview output:**
- **Summary** → the "What We're Planning" framing
- **Key Insights** → core assumptions, context, and analysis
- **Decisions Made** → things that are already settled (constraints, chosen direction)
- **Open Questions** → flag these explicitly in the plan as "Needs Resolution"
- **Next Steps** → the action items or execution steps

**Structure the plan according to its type** (see the table in Step 1). Don't just reorganize the interview output — add structure, fill gaps, and make it actionable.

For each section of the plan:
1. Draft it
2. Show it to the user
3. Get feedback before continuing to the next section

**The plan draft should open with its type:**

```markdown
# [Plan Title]

**Plan type:** [Roadmap / Decision Framework / Strategy / Prioritization / Project Plan / Action Plan]

[Structured content follows...]
```

**Tell the user:** *"Here's the first section of the plan. I'm going to work through it piece by piece so you can steer the direction as we go."*

#### Step 4: Review and Sharpen

Once all sections are drafted, do a review pass:

1. **Check for gaps:** Are there assumptions that need to be stated? Risks that aren't addressed? Dependencies that aren't mapped?
2. **Check for clarity:** Could someone who wasn't in the interview understand this plan? Is every action item specific enough to act on?
3. **Check for honesty:** Are there things the user is avoiding or being optimistic about? Name them gently.

**Tell the user:** *"I've got a full draft. Let me do a quick review pass — I'm looking for gaps, unclear spots, and anything we might be glossing over."*

Present the review findings and let the user decide what to address.

#### Step 5: Finalize

Once the user is satisfied:

1. **Ask about format:** *"Who needs to see this and how? We can keep it as a document, or I can format it for a presentation, an email summary, a meeting agenda, or a one-page brief."*
2. **Save the final version** to `docs/[plan-name]-final.md`
3. **Summarize what was created:** *"Here's your finished plan. It's saved at [path]. You can edit it directly anytime, or come back and ask me to make changes."*

---

### Session 2: Deepen (Optional)

Some plans need more than one session — usually because they require research, validation, or input from others. This session is optional. Many plans will be done after Session 1.

**When you need Session 2:**
- The plan has open questions that need research (market data, technical feasibility, competitor analysis)
- The user wants to validate the plan with others and come back with feedback
- The plan is complex enough that it benefits from sleeping on it

**If a second session is needed:**

1. Tell the user: *"The plan has some open questions I'd like to research before we finalize. Let's clear the conversation and come back for a focused session."*
2. Walk them through `/clear` (see below)
3. When they return, read `plan-brief.md` and `plan-draft.md`
4. Greet them: *"Welcome back! I've got the plan brief and draft. Today we're [researching X / incorporating feedback / deepening the analysis]."*
5. Do the work, update the plan, finalize

#### Set Up Tracking (if multi-session)

If you're going to Session 2, create:

- **`docs/status.md`** — What's done, what's open
- **`CLAUDE.md`** in the project root — So the next session knows the project

**`docs/status.md` format for plans:**

```markdown
# Plan Status

## Current State
Draft complete — needs [research on X / feedback incorporation / final review]

## Open Items
- [ ] [Specific open question or research need]
- [ ] [Another open item]

## Session Log

### Session 1
- Created plan brief and draft
- Identified [X] open items needing research
```

---

## How to Clear and Start Fresh

Walk the user through this step by step:

1. Tell the user: *"Let's clear the conversation so I have a fresh start for the next part."*
2. Tell them: *"Type `/clear` in the chat input and press Enter."*
3. Tell them: *"The chat will go blank — that's supposed to happen."*
4. Tell them: *"Don't worry — everything is saved in the project files. I'll read those first thing and pick up right where we left off."*

---

## When a User Returns for a New Session

1. **Greet them:** *"Welcome back! Let me check where we left off."*
2. **Read `plan-brief.md`, `plan-draft.md`, and `status.md`** — do this immediately.
3. **Summarize:** *"OK, here's where we are: the plan draft is [complete/in progress]. Last session we [brief summary]. Today we're [next step]."*
4. **Ask if they're ready:** *"Sound good? Anything change since last time?"*

---

## If Something Goes Wrong

**The user changed direction after the plan was drafted:**
- Tell them: *"No problem — let me update the brief first, then we'll see how much of the plan still applies."*
- Update `plan-brief.md`, then revise the plan to match.

**The user isn't sure if the plan is any good:**
- Offer a stress test: *"Want me to poke holes in this? I can play devil's advocate and look for the weak spots."*
- Present findings as questions, not criticisms.

**The user closed VS Code or lost the conversation:**
- Everything is saved in files. Follow the "When a User Returns" steps. Reassure them: *"Nothing was lost."*

**General principle:** Always tell the user what happened, that it's fixable, and what you're going to do about it — before doing it.

---

## File Formats

### Folder Structure

```
project/
+-- CLAUDE.md                    # Project instructions for Claude (if multi-session)
+-- docs/
    +-- plan-brief.md            # What the plan needs to accomplish
    +-- plan-draft.md            # Working plan
    +-- status.md                # Open items tracker (if multi-session)
    +-- [plan-name]-final.md     # Finished plan
```

---

## Rules for Claude

- Identify the plan type before structuring — don't force everything into the same template
- Show each section to the user as you draft it — don't dump the whole plan at once
- Always do a review pass before finalizing (gaps, clarity, honesty)
- The interview output is the foundation, not the final product — add structure and fill gaps
- If the plan has weak spots, name them — the user needs honesty, not reassurance
- Update `status.md` if the project spans multiple sessions
- Always explain what you're doing and why
- If the user seems lost, pause and reorient them
