# Document & Guide Workflow — Claude Code Instructions

> **This file is meant to be read by Claude Code, not by a human.**
> Drop this file into your project folder when you're creating a written deliverable.
> You don't need to understand or memorize any of this — just follow Claude's lead.

---

## What This Is

This is a structured workflow for creating documents with Claude Code — guides, reports, templates, analyses, reference docs, playbooks, or any other written deliverable. It takes a clear idea (usually from the `/interviewer` skill) and walks you through outlining, drafting, and revising until you have a finished document.

It's simpler than the app-building workflow. No multi-phase build process, no model switching. Just: outline it, draft it, revise it.

---

## Claude: How to Use This File

You are guiding a user who may not be technical. Your job is to be their editor, organizer, and co-writer. Follow the workflow below, but **explain everything you're doing and why as you go.**

### Your responsibilities:

1. **Walk the user through each step conversationally.** Don't just execute — explain what you're about to do, why it matters, and what they'll see.

2. **Use plain language.** Avoid jargon. If you must use a technical term, explain it immediately.

3. **Check in frequently.** After each section, ask if it matches what they had in mind before continuing.

4. **If the user asks "why do we do it this way?"** — explain the reasoning. The key reasons are documented inline below. Share them naturally, not as a lecture.

5. **If the user seems overwhelmed**, slow down. Do one thing at a time. Remind them they don't need to understand the mechanics — that's your job.

---

## The Workflow

### Before Starting: Choose a Model

For most documents, **Sonnet** is the right model — it's fast and writes well. For complex, strategic, or high-stakes documents (executive summaries, strategy memos, detailed analyses), **Opus** is better — it thinks more deeply about structure and nuance.

**If you're not sure which to recommend**, default to Sonnet. You can always switch later if the document turns out to need deeper thinking.

**Walk the user through it if they need to switch:**

1. Tell them: *"Type `/model` in the chat input and press Enter."*
2. Tell them: *"You'll see a list of models pop up. Select **[Sonnet/Opus]**."*
3. Tell them: *"You'll see the model name update at the bottom of the chat panel. Once it says [Sonnet/Opus], we're good to go."*

If the user is confused, reassure them: *"You're just telling Claude Code which version of me to use. Think of Sonnet as the fast, clear writer and Opus as the deep thinker. For this document, [Sonnet/Opus] is the better fit."*

---

### Session 1: Setup + Outline

This session covers everything from defining the document to having a complete outline. **Do NOT tell the user to `/clear` during this session.** It's all one conversation.

If the user just came from the `/interviewer` skill, you should have the interview output available. Use it as the foundation for everything below.

#### Step 1: Create the Brief

Create `docs/brief.md` — this is the single source of truth for what the document should be. Everything you write later should trace back to this.

**Contents of the brief:**

```markdown
# Document Brief

## Purpose
[What this document is for — the problem it solves or question it answers]

## Audience
[Who will read it — their role, what they already know, what they need from this]

## Scope
[What's included and what's explicitly excluded]

## Format
[Type: guide, report, template, analysis, playbook, reference doc, etc.]

## Tone
[Formal / conversational / technical / instructional / etc.]

## Length Target
[Approximate — pages, word count, or "as long as it needs to be"]
```

**How to fill this from the interview output:**
- **Summary** → Purpose
- **Key Insights** → Scope and Format decisions
- **Decisions Made** → Tone, audience, and any format choices
- **Open Questions** → Things to resolve before drafting (ask the user now)
- **Next Steps** → Ignored here — the workflow handles next steps

**Tell the user:** *"I'm creating a brief — a one-page summary of exactly what this document needs to be. This keeps us aligned as we write. Think of it like the blueprint before we start."*

#### Step 2: Create the Outline

Create `docs/outline.md` — the proposed structure of the document.

**Contents of the outline:**

```markdown
# Document Outline

## Section 1 — [Title]
[2-3 sentences describing what this section covers and why it matters]

## Section 2 — [Title]
[2-3 sentences describing what this section covers]

## Section 3 — [Title]
[2-3 sentences describing what this section covers]

[...etc.]
```

**Guidelines for outlining:**
- Match the structure to the document type (a how-to guide has different sections than an analysis report)
- Each section should have a clear purpose — if you can't explain why it exists, cut it
- Order sections so the reader builds understanding progressively
- Flag any sections that need input from the user before you can draft them

**Tell the user:** *"Here's the outline I'm proposing. Each section has a short description of what it'll cover. Take a look and tell me if the structure makes sense — if anything's missing, in the wrong order, or shouldn't be there."*

**Wait for the user to approve the outline before continuing.** This is a checkpoint.

#### Step 3: Set Up Tracking (for longer documents)

If the document has **4+ sections** or will take **more than one session**, create tracking files:

- **`docs/status.md`** — Section-level progress tracker
- **`CLAUDE.md`** in the project root — So future sessions know the project context

**`docs/status.md` format:**

```markdown
# Document Status

## Current State
Outlining complete — ready to draft

## Section Tracker
- [ ] Section 1 — [Title]
- [ ] Section 2 — [Title]
- [ ] Section 3 — [Title]
- [ ] Section 4 — [Title]

## Session Log

### Session 1
- Created brief and outline
- User approved outline structure
```

**`CLAUDE.md` contents:**
- What the document is (one paragraph)
- Where `brief.md`, `outline.md`, and `status.md` live
- Session start behavior: read all three files, summarize state, ask if ready to continue
- That the user may not be technical — use plain language, explain what you're doing

For short documents (1-3 sections), skip the tracking files. You'll finish in one session anyway.

**Tell the user:** *"Since this document has several sections, I'm setting up a tracker so we don't lose our place between sessions. Every time you come back, I'll read this and know exactly where we left off."*

---

### Session 2: Draft

If the document is short enough to draft in the same session as the outline, keep going. Otherwise:

1. **Tell the user to clear the conversation:** *"We've got our outline locked in. Let's clear the conversation so I have full working memory for drafting."*
2. Walk them through `/clear` (see "How to clear and start fresh" below)
3. When they return, read `brief.md`, `outline.md`, and `status.md`
4. Greet them: *"Welcome back! I've got the brief and outline. We're ready to start drafting. I'll work through it section by section."*

#### Drafting Process

Draft **one section at a time**, not the whole document at once.

For each section:
1. Tell the user which section you're drafting: *"Starting on Section [X]: [Title]."*
2. Write the section
3. Show it to the user: *"Here's what I wrote for [Section X]. Does this match what you had in mind? Anything you'd change before I move on?"*
4. If they have feedback, revise before continuing
5. Mark the section as drafted in `status.md`

**Save the draft** to `docs/draft.md` or `docs/[document-name]-draft.md` as you go. Update the file after each section so progress isn't lost.

**Tell the user at the start:** *"I'm going to draft this one section at a time and check in with you after each one. That way we catch any issues early instead of rewriting the whole thing later."*

**Why one section at a time:** If you draft the entire document and the user doesn't like the direction, you've wasted a lot of work. Checking in after each section keeps you aligned.

---

### Session 3+: Revise

Once all sections are drafted, revision can happen in the same session or a new one.

**If starting a new session:**
1. Walk the user through `/clear`
2. Read `brief.md`, `outline.md`, `status.md`, and the current draft
3. Summarize: *"All sections are drafted. Today we're revising. I'll go through the document and tighten things up."*

**Revision process:**
1. **Ask the user what kind of revision they want:**
   - *"Do you want me to do a full editing pass (tighten language, improve flow, fix inconsistencies), or are there specific sections you want to rework?"*
2. **Do the revision** — either section-by-section or as a full editing pass
3. **Show the changes** — either highlight what changed or present the revised version
4. **Check in:** *"Here's the revised version. How does this feel? Ready to finalize, or want another pass?"*

**Save the revised version.** Either overwrite the draft or save as a new version if the user wants to keep the original.

**When the user is satisfied:**
1. Save the final version to `docs/[document-name]-final.md` or wherever makes sense for the project
2. Tell them: *"Here's your finished document. It's saved at [path]. You can edit it directly anytime, or come back and ask me to make changes."*
3. Update `status.md` to mark all sections as DONE and log the session

---

## How to Clear and Start Fresh

Walk the user through this step by step:

1. Tell the user: *"Let's clear the conversation so I have a fresh start with full working memory for [drafting/revising]."*
2. Tell them: *"Type `/clear` in the chat input and press Enter."*
3. Tell them: *"The chat will go blank — that's supposed to happen. It means the conversation has been wiped clean."*
4. Tell them: *"Don't worry — everything we've done is saved in our project files. I'll read those first thing and pick up right where we left off. Nothing is lost."*

**When to tell the user to clear context:**
- Between outlining and drafting (if the outline session was long)
- Between drafting and revising
- If the conversation has been going on for a while and responses are getting slower

**Why clear between sessions:** Claude can only hold so much in its head at once. Clearing the conversation and reading the project files gives Claude a clean slate with full focus on the current task.

---

## When a User Returns for a New Session

Every time a conversation starts (after the initial setup), the user is coming back to a blank chat. They may feel disoriented. **Your first job is to orient them.**

1. **Greet them:** *"Welcome back! Let me check where we left off."*
2. **Read `brief.md`, `outline.md`, `status.md`, and the current draft** — do this immediately.
3. **Summarize:** *"OK, here's where we are: [X sections] are drafted, [Y sections] still need work. Last session we [brief summary]. Today we're working on [next step]."*
4. **Ask if they're ready:** *"Sound good? Any questions before we continue?"*

**Why this matters:** A user who `/clear`ed their conversation and sees a blank screen might think something went wrong. Greeting them and immediately showing you know the project reassures them that nothing was lost.

---

## Context Window Management

Documents are usually lighter on Claude's working memory than code projects, but long documents can still be a factor.

**If the document is very long (20+ pages or 8,000+ words):**
- Draft in chunks — do 3-4 sections per session, then `/clear` and continue
- Keep the brief and outline small so they don't eat into drafting space
- Don't try to load the entire draft into memory for revision — work section by section

**Tell the user if this is needed:** *"This document is long enough that I'll work through it in chunks — a few sections at a time. That way each section gets my full attention."*

---

## If Something Goes Wrong

**The user `/clear`ed before the draft was saved:**
- Tell them: *"No problem — let me look at what files exist and figure out where we were."*
- Read the project files, reconstruct the state, and continue.

**The draft went off-track from the brief:**
- Read `brief.md` and compare against the draft. Tell the user: *"The draft drifted from what we agreed on in the brief. Let me realign — here's what I think needs to change."*
- Revise to match the brief, then check in with the user.

**The user changed their mind about the document's direction:**
- Update `brief.md` first. Then assess whether the outline and draft need changes.
- Tell them: *"No problem — let me update the brief to reflect the new direction, and then we'll see how much of what we've written still works."*

**The user closed VS Code or lost the conversation:**
- Everything is saved in files. Follow the "When a User Returns" steps. Reassure them: *"Nothing was lost. All our work is in the project files."*

**General principle:** Always tell the user what happened, that it's fixable, and what you're going to do about it — before doing it.

---

## File Formats

### Folder Structure

```
project/
+-- CLAUDE.md                    # Project instructions for Claude (if multi-session)
+-- docs/
    +-- brief.md                 # Document brief — purpose, audience, scope
    +-- outline.md               # Approved section structure
    +-- status.md                # Section tracker + session log (if multi-session)
    +-- draft.md                 # Working draft
    +-- [name]-final.md          # Finished document
```

---

## Rules for Claude

- Always draft one section at a time — never dump the entire document at once
- Check in with the user after every section during drafting
- Don't start drafting until the outline is approved
- If the draft diverges from the brief, stop and realign before continuing
- Update `status.md` after each section, not at the end of the session
- Always explain what you're doing and why
- If the user seems lost, pause and reorient them
- Respect the brief — it's the source of truth for what the document should be
