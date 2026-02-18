# Claude Code Starter Kit

Two tools to get you started with Claude Code. You don't need to understand what's in these files — they're written for Claude to read, not you. Your job is to install them and let Claude guide you.

---

## What's In Here

### 1. Interviewer Skill

A guided interview that helps you figure out what you want to build. Claude asks you thoughtful questions, then organizes your answers into a clear summary with next steps.

Works for anything — planning a project, making a decision, thinking through a career move, figuring out a vacation, or just getting your thoughts organized.

**Use it by typing:** `/interviewer` in Claude Code

### 2. Project Workflow

A structured process for building things with Claude Code. It turns a vague idea into a plan, and then into a finished thing — step by step, session by session.

Pairs with the interviewer: the interview figures out *what* you want to build, this workflow handles *how*.

**Use it by:** dropping `project-workflow.md` into any project folder. Claude reads it and walks you through the rest.

---

## How to Install

### Option A: Ask Claude to Do It (Easiest)

Open Claude Code in VS Code and paste this:

> Please install the interviewer skill and project workflow from https://github.com/emersonmccuin-pixel/claude-code-starter-kit — read the README there for the file locations, then download and install everything.

Claude will handle the rest.

### Option B: Manual Install

**Interviewer Skill:**

1. Copy the `interviewer/` folder (including `references/`) into your Claude Code skills directory:
   - **Windows:** `C:\Users\[you]\.claude\skills\interviewer\`
   - **Mac/Linux:** `~/.claude/skills/interviewer/`
2. That's it. Type `/interviewer` in Claude Code to use it.

**Project Workflow:**

1. Copy `project-workflow.md` into the root of any project you want to build
2. Start a Claude Code conversation in that project
3. Claude reads the file and walks you through the process

---

## What These Files Are

Both files are **instructions for Claude**, not documentation for you. They tell Claude:

- What to do
- How to explain things in plain language
- When to check in with you
- Why the process works the way it does

You don't need to read or memorize them. Just install them and follow Claude's lead.

---

## Questions?

Open an issue on this repo or ask Claude Code — it knows how to help.
