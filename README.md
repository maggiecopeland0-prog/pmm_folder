# PMM Folder System: Setup & Walkthrough Guide

**Internal Reference.**
Product Marketing | April 2026

---

## What is this guide?

A step-by-step guide for setting up an AI workspace so Claude produces consistent, on-brand output every time you use it. This covers how to organize folders and markdown files so Claude knows your voice, your terminology, your audiences, and your process without you having to repeat yourself every session.

No code required. Everything here is plain text files in folders.

Personal note: I built this system as a Product Marketing Manager with zero technical background. If I can set this up, you can, too. 🐥

---

<details>
<summary><strong>Table of Contents</strong></summary>

- [What is this guide?](#what-is-this-guide)
- [Who Built This and Why](#who-built-this-and-why)
- [Key Terms](#key-terms)
- [How the Folder System Works](#how-the-folder-system-works)
- [The Five-Layer Architecture](#the-five-layer-architecture)
- [What's in This Repo](#whats-in-this-repo)
- [Step-by-Step: Set Up Your Workspace](#step-by-step-set-up-your-workspace)
  - [Step 1: Explore the Example](#step-1-explore-the-example)
  - [Step 2: Copy the Template](#step-2-copy-the-template)
  - [Step 3: Fill in CLAUDE.md (Your Identity File)](#step-3-fill-in-claudemd-your-identity-file)
  - [Step 4: Fill in CONTEXT.md (Your Routing Table)](#step-4-fill-in-contextmd-your-routing-table)
  - [Step 5: Set Up Your First Workspace Folder](#step-5-set-up-your-first-workspace-folder)
  - [Step 6: Add Your Config Files](#step-6-add-your-config-files)
  - [Step 7: Test It with a Real Task](#step-7-test-it-with-a-real-task)
- [Alternative: Use the Skill with Claude](#alternative-use-the-skill-with-claude)
- [Why Transparency and Control Matter](#why-transparency-and-control-matter)
- [Why Product Marketers Are Set Up for This](#why-product-marketers-are-set-up-for-this)
- [Who This Is For](#who-this-is-for)
- [Troubleshooting](#troubleshooting)
- [Resources](#resources)
- [Books on My Shelf](#books-on-my-shelf)
- [Credits](#credits)
- [License](#license)

</details>

---

## Who Built This and Why

I'm a Product Marketing Manager at Meltwater, where I lead product marketing for Mira AI, APIs & Governance. My work spans sales enablement, release notes, event prep, and executive briefing content, all for different audiences (Sales, CS, Solutions Consultants) who each need different tone, depth, and framing.

I use this system daily with Claude for sales enablement, release notes, event prep, and executive briefings. Before building it, I hit three problems fast: the output was generic, I was repeating myself every session, and I couldn't scale across deliverable types without losing consistency.

This starter kit packages what I learned so other teams can do the same.

---

## Key Terms

**Workspace:** A folder for one type of deliverable (e.g., `release-notes/`, `enablement-decks/`). Each workspace has its own process file that tells Claude exactly how to produce that deliverable.

**Layer:** Each file type in the system serves a different purpose. Claude loads them in order, not all at once. Think of layers like stages in an assembly line: each one adds something specific.

**Config file:** A stable reference file that lives in the `_config/` folder (voice rules, terminology, audience profiles). These don't change between tasks. They're the factory settings.

**Routing table:** A table in [CONTEXT.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/example/CONTEXT.md) that tells Claude which folder to go to and which config files to load for each task type. It prevents Claude from loading context it doesn't need.

**Stage contract:** The step-by-step process inside each workspace folder's CONTEXT.md. It defines inputs, process steps, output format, and quality checks for that deliverable type.

**Working inputs:** The materials you provide fresh each time: a PRD, a brief, raw data, a competitor article. These are the ingredients the system processes.

---

## How the Folder System Works

Think of this system like a well-organized kitchen. The `_config/` files are your pantry staples (always there, always the same). Each workspace folder is a different station (one for salads, one for entrees, one for desserts). The routing table is the ticket system that sends each order to the right station. And your working inputs are the fresh ingredients that arrive each day.

Without this system, every Claude session starts from zero. You paste your voice rules, re-explain your products, remind Claude about your audiences, and still get output that sounds like a template. With the folder system, Claude reads the right files for the right task and the first draft actually sounds like your team wrote it.

| Without folder structure | With folder structure |
|---|---|
| You paste your full context every session | Claude reads only the files relevant to this task |
| Long prompts repeat the same rules each time | Rules live in files that load automatically |
| More text in = more tokens used | Smaller, targeted context = fewer tokens |
| Output sounds generic across deliverables | Each deliverable type has its own process and voice |

---

## The Five-Layer Architecture

Each layer loads progressively. The agent never loads everything at once, only what the current task requires.

| Layer | File | Question it answers | What it contains |
|---|---|---|---|
| 0 | [CLAUDE.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/example/CLAUDE.md) | "Where am I?" | Identity, rules, workspace map |
| 1 | [CONTEXT.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/example/CONTEXT.md) | "Where do I go?" | Task routing table |
| 2 | Workspace [CONTEXT.md](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example/release-notes) | "What do I do?" | Process, format, quality checks |
| 3 | [_config/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example/_config) files | "What rules apply?" | Voice, terminology, audiences |
| 4 | Working inputs | "What am I working with?" | Per-run material (PRDs, briefs, data) |

**What this does:** Instead of writing one massive prompt that tries to cover everything, you split your context into layers that load based on what the task actually needs. A release note loads voice and terminology. An enablement deck also loads audience profiles. Claude only sees what's relevant.

---

## What's in This Repo

| Folder | What it is | Start here? |
|---|---|---|
| [example/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example) | A filled-in PMM workspace with 3 workspaces and 3 config files. Browse this to see the pattern. | Yes, look first |
| [template/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/template) | A blank starter with placeholders and guidance comments. Fork this to build your own. | Yes, use second |
| [setup/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/setup) | A [21-question interview guide](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/setup/questionnaire.md) that maps your answers to which template files to fill. | Yes, use with template |
| [docs/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/docs) | [Design principles](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/docs/design-principles.md) and [FAQ](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/docs/faq.md) for reference. | Optional |
| [SKILL.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/SKILL.md) | A Claude skill that builds the workspace for you through an interview. | Optional |
| [STRUCTURE.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/STRUCTURE.md) | Detailed explanation of every file and folder in this system. | Optional |

---

## Step-by-Step: Set Up Your Workspace

This is a self-paced process. You can do it in one sitting (~45 minutes) or spread it across a few sessions. Start with Steps 1-3 and add the rest as you go.

---

### Step 1: Explore the Example

Before building anything, spend 10 minutes reading the [example/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example) folder to see what the finished product looks like. Read the files in this order:

| Order | File | What you'll see |
|---|---|---|
| 1st | [example/CLAUDE.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/example/CLAUDE.md) | How to introduce yourself and your role to Claude |
| 2nd | [example/CONTEXT.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/example/CONTEXT.md) | A routing table that tells Claude which folder to use for each task type |
| 3rd | [example/release-notes/CONTEXT.md](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example/release-notes) | A step-by-step process for one type of deliverable |
| 4th | [example/_config/voice.md](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example/_config) | Rules about tone, formatting, and what to avoid |
| 5th | [example/_config/terminology.md](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example/_config) | Required and forbidden terms |

**What this does:** You're learning the pattern before applying it. Every workspace follows this same structure: identity file → routing table → workspace process → config files. Once you see it, you'll recognize it everywhere.

---

### Step 2: Copy the Template

Make a copy of the [template/](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/template) folder and rename it for your team or your role (e.g., `pmm-workspace/` or `content-ops-workspace/`). This is your workspace now. You own it, you maintain it.

Every file in the template has placeholder text and guidance comments that tell you what to fill in. You don't need to rename any files. The naming convention (`CLAUDE.md`, `CONTEXT.md`, `_config/`) is part of how the system works.

**What this does:** The template gives you the complete folder structure with all the right files in the right places. You just need to replace the placeholder content with your own.

---

### Step 3: Fill in CLAUDE.md (Your Identity File)

Open `CLAUDE.md` in your copied template. This is the file Claude reads first, every session, every task. It tells Claude who you are, what your role covers, how the folder structure works, and what rules apply to everything.

Fill in four sections:

1. **Who I Am** — Your role, your team, your company, what your work covers
2. **Workspace Map** — A text diagram showing your folder structure (update this as you add workspace folders)
3. **How to Use This Workspace** — Keep the default instructions. They tell Claude to read files in order.
4. **Critical Rules** — Non-negotiable rules that apply to every task, regardless of type

<details>
<summary><strong>Example: What a filled-in CLAUDE.md looks like</strong></summary>

```markdown
# CLAUDE.md - Product Marketing Workspace

## Who I Am

I'm a Product Marketing Manager (PMM). My work spans sales enablement
(talk tracks, FAQ docs, battlecards, training decks), internal documentation
(release notes, product updates), and event preparation (presenter briefs,
talking points).

I work across multiple internal audiences: Sales reps, Customer Success
Managers (CSMs), and Solutions Consultants (SCs).

## Critical Rules (Always Apply)

- Always say **customer**, never "client"
- Always say **overview**, never "summary" when describing AI outputs
- Use audience labels [Sales] [CS] [SC] [All] when content varies by role
- Avoid em dashes
```

</details>

**What this does:** With CLAUDE.md in place, Claude starts every session already knowing your role, your workspace layout, and your universal rules. You never have to re-explain these things.

**Tip:** If you want help filling this in, open a Claude session and say: *"Help me work through [this questionnaire](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/setup/questionnaire.md) to set up my workspace."* Parts 1 and 7 of the questionnaire map directly to CLAUDE.md.

---

### Step 4: Fill in CONTEXT.md (Your Routing Table)

Open `CONTEXT.md` in your workspace root. This is the file that tells Claude which folder to go to and which config files to load for any given task.

The key section is the **Task Routing Table**. Each row maps a task type to a workspace folder and the specific config files that task needs:

| Task | Workspace | Load from _config/ |
|---|---|---|
| Write a Slack release note | `release-notes/` | `voice.md`, `terminology.md` |
| Build a sales training deck | `enablement-decks/` | `voice.md`, `terminology.md`, `audiences.md` |
| Write a presenter brief | `event-prep/` | `voice.md`, `audiences.md` |

You'll also add a **Reference File Index** (what each config file contains and when to load it) and a **Workspace Index** (what each folder produces).

**What this does:** The routing table is what makes the system efficient. Instead of Claude loading all your context for every task, it loads only what's relevant. A release note doesn't need audience profiles. A presenter brief doesn't need terminology rules. The routing table enforces this.

**Tip:** Parts 2 and 6 of the [setup questionnaire](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/setup/questionnaire.md) map directly to CONTEXT.md. List every deliverable type you produce, then group them into clusters. Each cluster becomes a workspace folder.

---

### Step 5: Set Up Your First Workspace Folder

Pick the deliverable type you produce most often. Rename the `workspace-1/` folder in your template to match it (e.g., `release-notes/`). Open its `CONTEXT.md` and fill in the stage contract:

1. **Inputs Required** — What source material does this deliverable start from? (PRD, brief, data, previous output)
2. **Process** — The step-by-step process you follow. Be specific: what do you do first, second, third?
3. **Output Format** — What does the final deliverable look like? (Slack post, slide deck, Word doc)
4. **Quality Checks** — What do you verify before publishing? (Terminology review, tone check, audience appropriateness)

<details>
<summary><strong>Example: A release notes stage contract</strong></summary>

```markdown
## Inputs Required
- PRD or feature brief from Product
- Release date and version number

## Process
1. Read the PRD and identify the customer-facing change
2. Load voice.md and terminology.md
3. Write a Slack-format announcement: headline, what changed, why it matters, what to do
4. Keep it under 150 words
5. Lead with customer value, not product mechanics

## Output Format
Slack post (markdown). No attachments. Includes [All] audience label.

## Quality Checks
- Uses "customer" (not "client")
- Uses "overview" (not "summary") for AI outputs
- No em dashes
- Under 150 words
```

</details>

**What this does:** The stage contract is where your domain expertise lives. These are the actual steps your team takes to produce good work, not generic instructions. The more specific the process, the better the output.

**Why this matters:** Without a stage contract, Claude produces deliverables using generic best practices. With one, Claude follows your team's actual workflow. The difference shows up immediately in the first draft.

---

### Step 6: Add Your Config Files

Open the three files in your `_config/` folder and fill them in:

| File | What to fill in | Questionnaire section |
|---|---|---|
| `voice.md` | Your team's writing style, formatting rules, 2-3 good examples, 2-3 bad examples | [Part 3](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/setup/questionnaire.md) |
| `terminology.md` | Required terms, forbidden terms, product names, common AI mistakes | [Part 4](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/setup/questionnaire.md) |
| `audiences.md` | Who reads your content, what they need, what tone works, what format they prefer | [Part 5](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/setup/questionnaire.md) |

**The most important thing here is the voice samples.** Real examples of good and bad writing teach Claude more than any rule. Paste 2-3 pieces of work you're proud of and 2-3 that represent what you want to avoid.

**What this does:** Config files are the "factory settings" for your workspace. Once they're solid, every subsequent task benefits. You set them up once and they apply automatically through the routing table.

**Tip:** You don't need to fill in every config file on day one. Start with `voice.md` (it has the biggest impact on output quality) and add the others as you go.

---

### Step 7: Test It with a Real Task

Pick a deliverable you've produced recently. Give Claude the same source material you started from and ask it to produce the deliverable using your workspace.

Compare the output to what you'd normally get without the folder structure. Look for:

- **Tone:** Does it sound like your team, or like a generic template?
- **Terminology:** Does it use your required terms correctly?
- **Structure:** Does it follow your process steps?
- **Audience fit:** Is it appropriate for the target reader?

If something's off, trace it to the source file. Generic tone? Add more voice samples. Wrong terminology? Update the correction log. Missing steps? Refine the stage contract.

**This is the Edit-Source Principle:** when an output has a recurring problem, fix the source file (config or process), not just the output. Fixing the source fixes this run and every future run.

---

## Alternative: Use the Skill with Claude

If you'd rather have Claude build the workspace for you:

1. Install [SKILL.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/SKILL.md) as a Claude skill (Claude Code or Cowork).
2. Tell Claude: "Set up a workspace for my team."
3. Claude will interview you, build the folder structure, and populate the files.

This follows the same process as the manual walkthrough but Claude handles the file creation. You still make all the decisions about content, structure, and rules.

---

## Why Transparency and Control Matter

I came to this method with a specific perspective: I spent the last year bringing an AI-powered product to market, which meant I had to explain to customers how AI features worked, how the models processed their inputs, and what level of control they had over the outputs.

When I turned around and started using AI for my own work, I wanted those same things. As a Product Marketer, I needed to see and control every part of how Claude was working: what context it used, what rules it followed, and where I could make changes.

That's what this system actually gives you. Every instruction Claude follows is a markdown file you can open, read, and edit with any text editor. There's no hidden logic, no proprietary configuration, and no technical abstraction. If the output isn't right, you can trace it to a specific file and fix it there.

You can see exactly how your instructions connect to what Claude produces. If something's off in the output, you open the relevant file, make the change, and the next run reflects it. This transparency isn't a bonus feature. It's the core design principle.

---

## Why Product Marketers Are Set Up for This

Product marketers are uniquely positioned for this kind of work. We already think in frameworks: messaging hierarchies, audience segmentation, competitive positioning. We already maintain style guides and terminology lists. We already produce recurring deliverables from templates and reference docs.

If you already build deliverables from templates and reference docs, you're closer to a working AI workspace than you think. The folder system just makes what you're already doing legible to Claude.

---

## Who This Is For

Any team with recurring AI-assisted workflows where:

- You produce the same types of deliverables repeatedly (reports, decks, docs, announcements)
- Quality depends on following specific conventions (terminology, tone, formatting)
- Multiple audiences need different versions or emphasis
- You want outputs to be reviewable and editable at every stage

Originally built for Product Marketing at Meltwater. Designed to work for any team.

---

## Troubleshooting

### 1. "Claude isn't reading my files."

Check these in order:

1. **Is CLAUDE.md at the root of your workspace?** Claude looks for this file first. If it's nested inside a subfolder, Claude won't find it.
2. **Did you keep the exact file names?** The naming convention (`CLAUDE.md`, `CONTEXT.md`, `_config/`) matters. Renaming files will break the routing.
3. **Are you pointing Claude to the right folder?** Make sure your workspace folder is set as Claude's working directory or project folder.

### 2. "My output is still generic."

This usually means one of three things:

1. **Your voice samples are missing.** Config files without real good/bad examples produce generic output. Paste 2-3 real pieces of work you're proud of into `voice.md`.
2. **Your stage contract is too vague.** "Write a good release note" is too generic. "Write a Slack-format announcement under 150 words that leads with customer value" is specific enough to work.
3. **Your config files aren't being loaded.** Check your routing table in CONTEXT.md. Make sure the task type is listed and the right config files are specified.

### 3. "Do I need to fill in everything on day one?"

No. Start with three files: CLAUDE.md, CONTEXT.md, and one workspace folder's CONTEXT.md. Add config files and additional workspace folders as you go. A minimal workspace that you actually use beats a complete one that you never finish setting up.

### 4. "How many workspace folders should I have?"

Aim for 4-12. Fewer than 4 means the structure probably isn't adding value. More than 12 means you might be over-segmenting. The test: if two workspaces share the same process AND the same config files, merge them.

### 5. "What if I want to use this with a different AI model?"

The folder system is model-agnostic. The folder structure, file formats, and naming conventions don't depend on any model-specific capability. Point a different model at the same files and it works. The protocol imposes no vendor lock-in.

### 6. "How do I update the workspace over time?"

Edit the markdown files directly. If outputs consistently have the same problem, trace it to the source: update the voice guide, add a correction to `terminology.md`, or refine the process in a workspace CONTEXT.md. This is the Edit-Source Principle: fix the factory, not the product.

### 7. "Can multiple people use the same workspace?"

Yes. The workspace is a folder. Share it via Git, cloud storage, or a zip file. Each person can run it independently. If someone improves a config file, commit it so everyone benefits.

---

## Resources

**In This Repo**

- [Example workspace](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/example) | [Template](https://github.com/maggiecopeland0-prog/pmm_folder/tree/main/template) | [Setup questionnaire](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/setup/questionnaire.md)
- [Design principles](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/docs/design-principles.md) | [FAQ](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/docs/faq.md) | [Structure reference](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/STRUCTURE.md)
- [SKILL.md](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/SKILL.md) (Claude skill for automated setup)

**Background**

- [Interpretable Context Methodology (ICM)](https://github.com/RinDig/Model-Workspace-Protocol-MWP-) — Van Clief & McDermott (2026), Eduba, University of Edinburgh
- [Model Workspace Protocol (MWP)](https://github.com/RinDig/Model-Workspace-Protocol-MWP-) — Open-source protocol (MIT License)

Questions or feedback? Reach out to PMM.

---

## Books on My Shelf

A few of the books that shaped how I think about this work — from design systems to bureaucracy to the politics of algorithms.

<img width="600" alt="Books on my shelf: Co-Intelligence by Ethan Mollick, Looking Awry by Slavoj Žižek, The Design of Everyday Things by Donald Norman, The Utopia of Rules by David Graeber, Weapons of Math Destruction by Cathy O'Neil" src="screenshots/bookshelf.png" />

---

## Credits

This project implements the [Interpretable Context Methodology (ICM)](https://github.com/RinDig/Model-Workspace-Protocol-MWP-), based on the Model Workspace Protocol (MWP) by Van Clief & McDermott.

Van Clief, J. & McDermott, D. (2026). "Interpretable Context Methodology: Folder Structure as Agent Architecture." Eduba, University of Edinburgh.

Protocol: [github.com/RinDig/Model-Workspace-Protocol-MWP-](https://github.com/RinDig/Model-Workspace-Protocol-MWP-)

Co-authored with Claude, Anthropic

---

## License

Open source — see [LICENSE](https://github.com/maggiecopeland0-prog/pmm_folder/blob/main/LICENSE).
