---
name: Claude Code Starter Kit
description: >
  Go from zero to creating your first project with Claude Code in under an hour.
  Includes a guided discovery interviewer skill (/interviewer) that helps you figure
  out what to build, plus three structured workflows (app, document, plan) that walk
  you through actually creating it. No coding experience required.
version: 1.0.0
---

# Claude Code Starter Kit

An interviewer skill and three project workflows for Claude Code. The interviewer helps you figure out what you want to create. The workflows handle how to create it — whether that's an app, a document, or a plan.

## What's Included

- **Interviewer skill** (`interviewer/SKILL.md`) — Guided discovery interview triggered by `/interviewer`
- **App & Tool workflow** (`workflows/app-workflow.md`) — Multi-phase build process with Opus planning + Sonnet building
- **Document & Guide workflow** (`workflows/document-workflow.md`) — Outline, draft, revise cycle
- **Plan & Strategy workflow** (`workflows/plan-workflow.md`) — Structures thinking into actionable plans

## Installation

### Interviewer Skill

Copy the `interviewer/` folder (including `references/`) into your Claude Code skills directory:

- **Windows:** `C:\Users\[you]\.claude\skills\interviewer\`
- **Mac/Linux:** `~/.claude/skills/interviewer/`

Type `/interviewer` in Claude Code to use it.

### Project Workflows

Copy the `workflows/` folder into any project folder where you want to use them:

```
your-project/
  workflows/
    app-workflow.md
    document-workflow.md
    plan-workflow.md
```

The interviewer automatically picks the right workflow based on what you want to create.

## Usage Examples

### Start an interview

Type `/interviewer` in Claude Code. Claude will ask you to pick an interview style (exploratory, structured, or rapid-fire), depth level, and what you want to end up with. Then it asks questions to help you figure out what you're building.

### Build an app after the interview

After the interview, Claude will say something like *"Just say 'Let's start building based on the interview.'"* It reads `workflows/app-workflow.md` and walks you through a phased build process.

### Create a document

Pick "A document or guide" during the interview. Claude reads `workflows/document-workflow.md` and guides you through brief, outline, draft, and revision.

### Create a plan

Pick "A plan or strategy" during the interview. Claude reads `workflows/plan-workflow.md` and structures your thinking into a roadmap, decision framework, or action plan.

## Requirements

- VS Code with the Claude Code extension
- Claude Pro subscription ($20/month)
- No coding experience needed
