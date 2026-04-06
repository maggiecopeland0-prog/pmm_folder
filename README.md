# PMM Folder System - AI Agent Workspace Starter Kit

A skill and starter kit for building AI agent workspaces for product marketing teams, built on the [Interpretable Context Methodology (ICM)](https://github.com/RinDig/Model-Workspace-Protocol-MWP-) and the [Model Workspace Protocol (MWP)](https://github.com/RinDig/Model-Workspace-Protocol-MWP-) by Van Clief & McDermott.

---

## Who Built This and Why

I'm a Product Marketing Manager at Meltwater, where I lead product marketing for Mira AI, APIs & Governance, and Newsletters. I adopted ICM as the foundation for my own PMM workspace and quickly realized the pattern could work for any team that produces recurring deliverables with AI.

I use this system daily with Claude for sales enablement, release notes, event prep, and executive briefings. This repo packages what I learned into a starter kit so other teams - especially non-technical ones - can build their own version without writing any code.

---

## What This Is

This starter kit uses ICM's five-layer architecture to organize folders and markdown files so AI agents receive the right context at the right time for your team's recurring work. It's just a folder of plain text files that anyone can read, edit, and version-control — no code or framework needed.

The core idea: if the prompts and context for each type of work live in a well-organized folder hierarchy, you don't need a coordination framework. You need one agent that reads the right files at the right moment.

---

## The Five-Layer Architecture

Each layer loads progressively. The agent never loads everything at once - only what the current task requires.

| Layer | File | Question it answers | What it contains |
|-------|------|-------------------|------------------|
| 0 | `CLAUDE.md` | "Where am I?" | Identity, rules, workspace map |
| 1 | `CONTEXT.md` | "Where do I go?" | Task routing table |
| 2 | Stage `CONTEXT.md` | "What do I do?" | Process, format, quality checks |
| 3 | `_config/` files | "What rules apply?" | Voice, terminology, audiences |
| 4 | Working inputs | "What am I working with?" | Per-run material (PRDs, briefs, data) |

---

## What's in This Repo

| Folder | What it is |
|--------|-----------|
| **[example/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example)** | A filled-in PMM workspace with 3 workspaces and 3 config files. Start here to see the pattern. |
| **[template/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/template)** | A blank starter with placeholders and guidance comments. Fork this to build your own. |
| **[setup/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/setup)** | A 21-question interview guide that maps your answers to which template files to fill. |
| **[docs/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/docs)** | Design principles and FAQ. |
| [`SKILL.md`](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/SKILL.md) | Claude skill for building workspaces using this system. |

---

## Quick Start

### Option A: Use the template

1. Copy `template/` to your working directory and rename it.
2. Open [`setup/questionnaire.md`](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/setup/questionnaire.md) and work through the interview questions with Claude or on your own.
3. Fill in the placeholder files based on your answers.
4. Run a real task through the workspace and iterate.

---

### Option B: Use the skill with Claude

1. Install [`SKILL.md`](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/SKILL.md) as a Claude skill (Claude Code or Cowork).
2. Tell Claude: "Set up a workspace for my team."
3. Claude will interview you, build the folder structure, and populate the files.

---

### Option C: Learn from the example

1. Browse `example/` to see what a completed workspace looks like.
2. Read the files in order: `CLAUDE.md` > `CONTEXT.md` > any workspace `CONTEXT.md` > the config files it references.
3. Adapt the patterns for your own domain.

---

## Why Transparency and Control Matter

I came to this method with a specific perspective: I spent the last year bringing an AI-powered product to market. I've sat in the rooms where we talked about what users need from AI - and the answer always came back to the same things. People need to see what's happening. They need to know they can step in. They need confidence that the system is doing what they told it to, not something else.

When I turned around and started using AI for my own work, I wanted those same things. As a Product Marketer, not a developer, I don't write code. I can't debug a script or trace a function call. So if Claude is making decisions about what context to load and how to structure my content, I need to be able to see those decisions and change them.

That's what this system actually gives you. Every instruction Claude follows is a markdown file you can open and read. The routing table that tells Claude which files to load for a release note versus a deck? That's a table in CONTEXT.md - you can edit it in any text editor. The process Claude follows to write a release note? That's a numbered list in release-notes/CONTEXT.md. If the output isn't right, you don't guess at what went wrong. You open the file, find the step, and fix it.

You can see exactly how your instructions connect to what Claude produces. If something's off in the output, you can trace it back to what you wrote — and fix it. If you change a line in voice.md, you know exactly what that change will affect and when it will load. If you add a term to the correction log in terminology.md, it applies to every future task that loads that file. You're editing the system in plain language, and the system does what the files say.

This matters especially for no-code workflows. I don't need to understand prompt engineering theory or token optimization. I need to know that when I write "always say customer, never client" in a config file, Claude will follow that rule - and that I can verify it did by reading the file it loaded. The workspace is the documentation. The documentation is the workspace. Nothing is hidden.

---

## Why Product Marketers Are Set Up for This

Product marketers are uniquely positioned for this kind of work. We already think in frameworks — messaging guides, competitive battlecards, audience profiles, talk tracks. That kind of structured, opinionated documentation is exactly what trains an AI well. The deliverables we produce every day are already organized, consistent, and built around repeatable patterns.

If you already build deliverables from templates and reference docs, you're closer to a working AI workspace than you might think. You don't need to learn prompt engineering. You need to organize what you already know.

---

## Who This Is For

Any team with recurring AI-assisted workflows where:

- You produce the same types of deliverables repeatedly (reports, decks, docs, announcements)
- Quality depends on following specific conventions (terminology, tone, formatting)
- Multiple audiences need different versions or emphasis
- You want outputs to be reviewable and editable at every stage

Originally built for Product Marketing at Meltwater. Designed to work for any team.

---

## Credits

This project implements the [Interpretable Context Methodology (ICM)](https://github.com/RinDig/Model-Workspace-Protocol-MWP-), based on the Model Workspace Protocol (MWP) by Van Clief & McDermott. ICM provides the five-layer architecture and design principles; this repo adapts them into a starter kit for product marketing and other non-technical teams.

> Van Clief, J. & McDermott, D. (2026). "Interpretable Context Methodology: Folder Structure as Agent Architecture." Eduba, University of Edinburgh.

Protocol: [github.com/RinDig/Model-Workspace-Protocol-MWP-](https://github.com/RinDig/Model-Workspace-Protocol-MWP-)

---

## License

Open source - see [LICENSE](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/LICENSE).
