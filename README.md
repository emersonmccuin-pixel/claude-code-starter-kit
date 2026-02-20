# Claude Code Starter Kit

Go from zero to creating your first project with Claude Code in under an hour. No coding experience required.

This kit includes an interviewer that helps you figure out what you want to create, and a set of workflows that help you actually do it — whether that's an app, a document, or a plan. All of it is written for Claude to read, not you. Your job is to install them and follow Claude's lead.
<br />

***

## The Whole Process at a Glance

```
Install VS Code --> Install Claude Code Extension --> Get Claude Pro ($20/mo)
    --> Create a workspace folder --> Install this starter kit
    --> /interviewer (figure out what you want to create)
    --> Workflow (create it step by step -- adapted to your output type)
    --> You have a thing. In under an hour.
```

***

## Step 1: Install VS Code (5 minutes)

VS Code is a free text editor. That's all it is — a place to work with files. You're not becoming a developer by installing it.

1. Go to <https://code.visualstudio.com>
2. Download the version for your computer (Windows, Mac, or Linux)
3. Install it like any other app
4. Open it

You'll see a welcome screen. You can close it — we won't need it.

***

## Step 2: Install Claude Code Extension (2 minutes)

The Claude Code extension adds a chat panel to VS Code where you can talk to Claude.

1. In VS Code, look for the square icon on the left sidebar (Extensions) — or press `Ctrl+Shift+X` (Windows) / `Cmd+Shift+X` (Mac)
2. In the search bar at the top, type **Claude Code**
3. Find the one by **Anthropic** and click **Install**
4. After it installs, you'll see a Claude icon appear in your left sidebar

***

## Step 3: Get a Claude Account (3 minutes)

Claude Code requires a paid Anthropic account. It's $20/month — about the same as Netflix. You can cancel anytime.

1. Go to <https://console.anthropic.com>
2. Create an account (email + password, or sign in with Google)
3. Subscribe to the **Pro plan** ($20/month)
4. That's it — no API keys, no configuration, no setup beyond this

**Not sure if it's worth it?** Try it for one month. If it doesn't change how you work, cancel. No contracts, no hassle.

***

## Step 4: Connect Claude Code (2 minutes)

Hit ctrl-shift-p (cmd-shift-p on Mac) and type "Claude Code" and select Claude Code: Focus Input.

1. A chat panel opens
2. It will ask you to sign in — follow the prompts to connect your Anthropic account
3. Once connected, you'll see a text input where you can type messages to Claude

Try typing: **"Hello, are you there?"** — Claude should respond. If it does, you're set.

***

## Step 5: Create Your Workspace (2 minutes)

You need a folder on your computer where your projects will live. Claude works with files and folders — this is its workspace.

1. Create a folder somewhere easy to find. Suggestions:

   * **Windows:** `C:\Claude Code Projects\`

   * **Mac:** `~/Claude Code Projects/`
2. In VS Code, go to **File > Open Folder** and select the folder you just created
3. You should see your empty folder in the file explorer on the left

**Tell Claude:**

> Create a subfolder called "My First Project" and open it. Then create a CLAUDE.md file that says I'm new to Claude Code and prefer simple, plain-English explanations. I'm not a developer.

Claude will create the folder and file for you. That CLAUDE.md file is how Claude remembers your preferences — it reads it every time you start a conversation.

***

## Step 6: Install the Starter Kit (2 minutes)

Now let's give Claude some tools to work with. Type this into the Claude chat:

> Please install the interviewer skill and project workflows from <https://github.com/emersonmccuin-pixel/claude-code-starter-kit> — read the README there for the file locations, then download and install everything.

Claude will:

* Read this repo

* Install the **interviewer skill** (so you can type `/interviewer` anytime)

* Download the **project workflows** into your project folder (one each for apps, documents, and plans)

When it's done, you'll have everything ready to go.

***

## Step 7: Figure Out What You Want to Create (10 minutes)

This is the fun part. Type:

> /interviewer

Claude will ask you three things: what interview style you want (casual questions, structured checklist, or rapid-fire), how deep to go, and what you want to end up with — an app, a document, or a plan. Then it'll ask you questions to help you figure out what you actually want to create.

**Not sure what to make?** Here are some ideas:

| Apps & Tools           | Documents & Guides             | Plans & Strategies             |
| ---------------------- | ------------------------------ | ------------------------------ |
| Budget tracker         | Onboarding guide for new hires | Vacation itinerary             |
| Habit tracker          | Team knowledge base            | Career decision framework      |
| Invoice generator      | Competitive analysis           | Home renovation roadmap        |
| Meeting notes app      | Email templates                | Product launch strategy        |
| Home inventory         | How-to reference doc           | Weekly priority list           |

Pick something small for your first project. You can always go bigger later.

At the end of the interview, Claude will give you a summary of what you're creating, key decisions, and next steps.

***

## Step 8: Create It (30-45 minutes)

Claude already knows what you want to create (from the interview). It'll tell you what to say next — something like "Let's start building based on the interview" or "Let's start the document" or "Let's structure the plan." Just follow its lead.

The workflow Claude uses adapts to what you're making:

* **An app** gets a multi-phase build process — plan, build, test, repeat
* **A document** gets an outline-draft-revise cycle — structured writing, one section at a time
* **A plan** gets structured and sharpened from the interview itself — often done in one session

In all cases, Claude will:

1. Create the right project files for your output type
2. Walk you through the process, explaining what it's doing and why
3. Check in with you along the way
4. Deliver a finished result

You don't need to understand the mechanics. Claude explains everything in plain English and asks before making decisions.

**If you get stuck at any point**, just tell Claude:

> I'm confused. Can you explain what's happening right now?

It will stop and reorient you. That's what it's designed to do.

***

## What's In This Repo

### Interviewer Skill

A guided interview that helps you figure out what you want to create. Claude asks thoughtful questions, then organizes your answers into a clear summary with next steps. It also asks what kind of output you want — an app, a document, or a plan — so the right workflow kicks in automatically.

Works for anything — building a tool, writing a guide, planning a strategy, making a decision, or just getting your thoughts organized.

**Use it by typing:** `/interviewer` in Claude Code

### Project Workflows (three types)

Structured processes that take the interview output and turn it into a finished thing. The interviewer figures out *what* you want to create — the workflow handles *how*.

* **App & Tool Workflow** — Multi-phase build process for software. Plan, build, test, repeat.
* **Document & Guide Workflow** — Outline, draft, revise cycle for written deliverables.
* **Plan & Strategy Workflow** — Structures your thinking into a clear, actionable plan.

The interviewer picks the right one based on your answer. You don't have to choose manually.

**Use them by:** dropping the `workflows/` folder into any project folder. Claude reads the right file and walks you through the rest.

### What These Files Actually Are

These files are **instructions for Claude**, not documentation for you. They tell Claude:

* What to do

* How to explain things in plain language

* When to check in with you

* Why the process works the way it does

You don't need to read or memorize them. Just install them and follow Claude's lead.

***

## Installing Manually (If You Prefer)

**Interviewer Skill:**

1. Copy the `interviewer/` folder (including `references/`) into your Claude Code skills directory:

   * **Windows:** `C:\Users\[you]\.claude\skills\interviewer\`

   * **Mac/Linux:** `~/.claude/skills/interviewer/`
2. That's it. Type `/interviewer` in Claude Code to use it.

**Project Workflows:**

1. Copy the `workflows/` folder into your project folder (or copy only the one you need):
   * `workflows/app-workflow.md` — for apps and tools
   * `workflows/document-workflow.md` — for documents and guides
   * `workflows/plan-workflow.md` — for plans and strategies
2. Start a Claude Code conversation in that project
3. Claude reads the right file and walks you through the process

***

## FAQ

**Do I need to know how to code?**
No. Claude handles the technical parts. You just need to know what you want.

**What if I don't know what I want?**
That's what the interviewer skill is for. It helps you figure it out.

**Is $20/month worth it?**
That depends on you. Try it for one month. Use it every day. If it doesn't change how you work, cancel.

**Can I use this for things that aren't apps?**
Yes — that's the whole point. The interviewer asks what you want to end up with, and the system adapts. Pick "A document or guide" and you get an outline-draft-revise process. Pick "A plan or strategy" and the interview output gets structured into something actionable. Pick "Other" and describe what you need — Claude will figure out the best approach.

**What if I don't know which workflow I need?**
You don't have to. The interviewer asks what you want to create and picks the right workflow automatically. If you're not sure, just describe what you're going for and Claude will suggest the best fit.

**What if something goes wrong?**
Tell Claude. Literally type "something went wrong" or "I'm stuck" and it will help you. You can also open an issue on this repo.

**Can I share this with other people?**
Yes. That's why it's public. Share the link: `github.com/emersonmccuin-pixel/claude-code-starter-kit`

*Built by Emerson for the AI @ Work Pittsburgh meetup, February 2026.*
*Questions? Open an issue or ask Claude Code — it knows how to help.*
