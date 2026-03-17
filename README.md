# Folder Training - ICM Workspace Builder

A skill and starter kit for building AI agent workspaces using the **Interpretable Context Methodology (ICM)**, based on the [Model Workspace Protocol (MWP)](https://github.com/RinDig/Model-Workspace-Protocol-MWP-) by Van Clief & McDermott.

---

## What This Is

ICM is a way to organize folders and markdown files so that an AI agent (Claude, or any LLM) gets the right context at the right time for your team's recurring work. No code, no framework - just a well-structured folder with plain text files that any human can read, edit, and version-control.

The core idea: if the prompts and context for each type of work live in a well-organized folder hierarchy, you don't need a coordination framework. You need one agent that reads the right files at the right moment.

---

## The Five-Layer Architecture

Each layer loads progressively. The agent never loads everything at once - only what the current task requires.

| Layer | File | Question it answers | What it contains |
|-------|------|---------------------|-----------------|
| 0 | `CLAUDE.md` | "Where am I?" | Identity, rules, workspace map |
| 1 | `CONTEXT.md` | "Where do I go?" | Task routing table |
| 2 | Stage `CONTEXT.md` | "What do I do?" | Process, format, quality checks |
| 3 | `_config/` files | "What rules apply?" | Voice, terminology, audiences |
| 4 | Working inputs | "What am I working with?" | Per-run material (PRDs, briefs, data) |

---

## What's in This Repo

| Folder | What it is |
|--------|-----------|
| **example/** | A filled-in PMM workspace with 3 workspaces and 3 config files. Start here to see the pattern. |
| **template/** | A blank starter with placeholders and guidance comments. Fork this to build your own. |
| **setup/** | A 21-question interview guide that maps your answers to which template files to fill. |
| **docs/** | Design principles and FAQ. |
| `SKILL.md` | The full ICM methodology as a Claude skill. |

---

## Quick Start

### Option A: Use the template

1. Copy `template/` to your working directory and rename it.
2. Open `setup/questionnaire.md` and work through the interview questions with Claude or on your own.
3. Fill in the placeholder files based on your answers.
4. Run a real task through the workspace and iterate.

---

### Option B: Use the skill with Claude

1. Install `SKILL.md` as a Claude skill (Claude Code or Cowork).
2. Tell Claude: "Set up an ICM workspace for my team."
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

That's what ICM actually gives you. Every instruction Claude follows is a markdown file you can open and read. The routing table that tells Claude which files to load for a release note versus a deck? That's a table in CONTEXT.md - you can edit it in any text editor. The process Claude follows to write a release note? That's a numbered list in release-notes/CONTEXT.md. If the output isn't right, you don't guess at what went wrong. You open the file, find the step, and fix it.

There's no hidden logic. No black box between what you told Claude and what it produces. If you change a line in voice.md, you know exactly what that change will affect and when it will load. If you add a term to the correction log in terminology.md, it applies to every future task that loads that file. You're editing the system in plain language, and the system does what the files say.

This matters especially for no-code workflows. I don't need to understand prompt engineering theory or token optimization. I need to know that when I write "always say customer, never client" in a config file, Claude will follow that rule - and that I can verify it did by reading the file it loaded. The workspace is the documentation. The documentation is the workspace. Nothing is hidden.

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

Based on the Interpretable Context Methodology (ICM), implementing the Model Workspace Protocol (MWP):

> Van Clief, J. & McDermott, D. (2026). "Interpretable Context Methodology: Folder Structure as Agent Architecture." Eduba, University of Edinburgh.

Protocol: [github.com/RinDig/Model-Workspace-Protocol-MWP-](https://github.com/RinDig/Model-Workspace-Protocol-MWP-)

---

## License

Open source - see [LICENSE](LICENSE).
