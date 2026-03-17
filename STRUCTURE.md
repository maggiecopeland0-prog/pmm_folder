# Folder Training - ICM for Product Marketing

## Why This Exists

I'm a PMM at Meltwater. I write release notes, enablement decks, FAQ docs, event briefs, and a dozen other things - all for different audiences (Sales, CS, Solutions Consultants) who each need different tone, depth, and framing.

When I started using Claude for this work, I hit three problems fast. First, the output was generic. Claude didn't know my products, my audiences, or how I write - so everything came back sounding like a template. Second, I was repeating myself every session. Every time I opened a new conversation, I'd re-explain my voice rules, my terminology ("say customer, never client"), and my formatting preferences. Third, I couldn't scale. I had one prompt for release notes, a different one for decks, another for event prep - and keeping them all consistent was its own job.

The Interpretable Context Methodology (ICM) solved all three. It's a way of organizing folders and markdown files so that Claude gets the right context for the right task, every time. No code, no framework - just plain text files in a folder structure that any human can read and edit.

The approach comes from an open-source protocol called the Model Workspace Protocol (MWP). I adapted it for Product Marketing work, and this repo packages that adaptation so other teams at Meltwater (or anywhere) can do the same.

---

## How It Works

The core idea is simple: instead of writing one massive prompt that tries to cover everything, you split your context into layers that load progressively based on what the task actually needs.

**CLAUDE.md** sits at the root of your workspace. It tells Claude who you are, what your role covers, how the folder structure works, and what rules apply to everything (like terminology mandates). This file loads every session, every task. It's the boot sequence.

**CONTEXT.md** (also at the root) is a routing table. When you say "write me a release note," Claude looks up that task type, finds which folder to navigate to, and sees which reference files to load. A release note needs voice and terminology. An enablement deck also needs audience profiles. The routing table prevents Claude from loading context it doesn't need.

**Each workspace folder** (release-notes/, enablement-decks/, event-prep/) has its own CONTEXT.md with a stage contract: what inputs it needs, the step-by-step process to follow, the output format, and quality checks. This is where domain expertise lives - the actual steps my team takes to produce good work, not generic instructions.

**The _config/ folder** holds stable reference files - voice guide, terminology rules, audience profiles. These don't change run to run. They're the factory settings. Claude loads only the ones the routing table specifies for the current task.

**Working inputs** (a PRD, a brief, raw data) are whatever you provide fresh each time. They're the ingredients the factory processes.

The result: Claude reads different files for different tasks, only loads what it needs, and the output stays consistent whether it's a Slack post or a 20-slide deck. The first drafts actually sound like me now, and I spend time refining instead of correcting.

---

## What's in This Repo

### Root

| File | What it is |
|------|-----------|
| `SKILL.md` | The skill itself (full ICM methodology) |
| `README.md` | Quick start guide |
| `LICENSE` | MIT |
| `.gitignore` | Excludes output folders and session logs |

---

### example/ - Working PMM workspace (filled in)

| File | What it contains |
|------|-----------------|
| `CLAUDE.md` | Identity and rules |
| `CONTEXT.md` | Task routing table |
| `_config/voice.md` | Tone, formatting, good/bad samples |
| `_config/terminology.md` | Required/forbidden terms, product names |
| `_config/audiences.md` | Audience profiles, mixed-audience rules |
| `release-notes/CONTEXT.md` | Stage contract: Slack posts, product updates |
| `enablement-decks/CONTEXT.md` | Stage contract: Training decks, FAQ docs |
| `event-prep/CONTEXT.md` | Stage contract: Briefs, talking points |

---

### template/ - Blank starter (fork and fill in)

| File | What it contains |
|------|-----------------|
| `CLAUDE.md` | Placeholders + guidance comments |
| `CONTEXT.md` | Placeholders + guidance comments |
| `_config/voice.md` | Template with example structure |
| `_config/terminology.md` | Template with correction log |
| `_config/audiences.md` | Template with profile format |
| `workspace-1/CONTEXT.md` | Generic stage contract template (duplicate for each workspace you need) |

---

### setup/ and docs/

| File | What it contains |
|------|-----------------|
| `setup/questionnaire.md` | 21-question interview guide |
| `docs/design-principles.md` | The 5 design principles explained |
| `docs/faq.md` | Common questions + troubleshooting |

---

## Getting Started

**Option A - Use the template.** Copy `template/`, rename it, work through `setup/questionnaire.md`, and fill in the placeholder files with your answers.

**Option B - Use the skill with Claude.** Install `SKILL.md` as a skill. Tell Claude "set up an ICM workspace for my team." It will interview you and build the structure.

**Option C - Learn from the example.** Browse `example/` to see what a completed workspace looks like. Read the files in order: CLAUDE.md, then CONTEXT.md, then any workspace CONTEXT.md and the config files it references.

---

## File count

| Section | Files | Purpose |
|---------|-------|---------|
| Root | 4 | SKILL.md, README, LICENSE, .gitignore |
| example/ | 9 | Fully populated PMM workspace |
| template/ | 7 | Blank starter with placeholders |
| setup/ + docs/ | 3 | Questionnaire + design principles + FAQ |

---

## References

This repo implements the Interpretable Context Methodology (ICM), based on the Model Workspace Protocol:

- [Interpretable Context Methodology: Folder Structure as Agent Architecture](https://github.com/RinDig/Model-Workspace-Protocol-MWP-) - Van Clief, J. & McDermott, D. (2026). Eduba, University of Edinburgh.
- [Model Workspace Protocol (MWP) - GitHub](https://github.com/RinDig/Model-Workspace-Protocol-MWP-) - Open-source protocol and workspace-builder (MIT License).
