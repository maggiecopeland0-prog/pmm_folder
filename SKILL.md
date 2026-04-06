---
name: folder-training
description: >
  Teaches Claude how to build and navigate team workspaces using a folder system built on the Interpretable Context Methodology (ICM),
  a five-layer system of markdown files and folders that structures context delivery for AI agents.
  Based on the Model Workspace Protocol (MWP) by Van Clief & McDermott. Use this skill whenever someone asks
  to "set up a workspace," "train Claude on my folder," "create a CLAUDE.md," "build an ICM workspace,"
  "organize my files for AI," or wants Claude to understand their team's work, terminology, and processes.
  Also trigger when someone mentions context layering, workspace routing, folder-based prompting, stage contracts,
  structured context for AI, or anything related to making Claude work better with a team's recurring workflows  - 
  even if they don't use the term ICM or MWP.
---

# Folder Training  -  PMM Workspace Builder (built on ICM)

This skill teaches you how to build structured workspaces that give Claude (or any AI agent) deep, role-aware context for a team's recurring work. The method is built on the Interpretable Context Methodology (ICM) and the Model Workspace Protocol (MWP), which replaces framework-level orchestration with filesystem structure. Plain markdown files carry the prompts and context. The folder hierarchy tells the agent what to do at each step. No code, no framework, no deployment step.

The core insight: if the prompts and context for each stage of a workflow already exist as files in a well-organized folder hierarchy, you do not need a coordination framework. You need one agent that reads the right files at the right moment.

---

## The Five Layers

ICM organizes context into five layers. Each layer answers a different question. The agent loads them progressively  -  never all at once.

```
Layer 0: CLAUDE.md ............. "Where am I?"      (~800 tokens)
Layer 1: CONTEXT.md ............ "Where do I go?"   (~300 tokens)
Layer 2: Stage CONTEXT.md ...... "What do I do?"    (200-500 tokens)
Layer 3: Reference material .... "What rules apply?" (500-2k tokens)
Layer 4: Working artifacts ..... "What am I working with?" (varies)
```

Layers 0-2 are **structural** (routing and stage instructions). Layers 3-4 are **content** (the factory settings and the raw ingredients).

### Layer 0  -  Identity (CLAUDE.md)
Lives at the workspace root. Always loaded first, every session.

Tells the agent: who it's working with, what the workspace contains, how the folder structure works, and what rules apply to every task without exception. Think of it as the boot sequence  -  self-contained enough for Claude to orient itself from scratch.

**Contains:** role description, workspace map (ASCII tree), loading instructions, critical rules, working style preferences.

**Does not contain:** task-specific instructions, process details, or reference data.

### Layer 1  -  Routing (root CONTEXT.md)
Lives at the workspace root alongside CLAUDE.md. Loaded second.

Contains the **routing table**  -  a lookup that maps task types to workspace folders and specifies which config files to load for each. This is what keeps context loading efficient. When someone says "write me a release note," the agent finds the matching row, navigates to the right folder, and loads only what's listed.

**Contains:** routing table (task → folder → config files), reference file index, workspace index, shared rules reminder.

### Layer 2  -  Stage Contract (workspace CONTEXT.md)
Lives inside each workspace folder. Loaded per-task.

This is the **stage contract**: what this workspace reads (inputs), what it does (process), and what it writes (outputs). Each workspace folder represents a single type of work with its own process, output format, and quality checks.

**Contains:** scope definition, input specifications (which Layer 3 + Layer 4 files), step-by-step process, output format with examples, file naming conventions.

### Layer 3  -  Reference Material (_config/ or references/)
Lives in `_config/` at the workspace root, or in `references/` within a stage folder. Loaded selectively per the routing table.

These are **stable files that persist across runs**  -  the factory configuration. Voice guides, terminology rules, audience profiles, product definitions, frameworks, templates. The model should internalize these as constraints: "write like this, follow these conventions."

**Critical rule:** Never load all config files at once. Each workspace's CONTEXT.md specifies exactly which ones it needs.

### Layer 4  -  Working Artifacts (per-run inputs)
Provided fresh each time. Not stored permanently in the workspace.

These are the **materials for a specific task instance**  -  a PRD, a brief, raw data, the output of a previous stage. They change every run. The model should process these as input: "transform this material according to the rules."

### The Layer 3 / Layer 4 Distinction

This separation matters because reference material and working artifacts ask different things of the model:

| | Layer 3: Reference | Layer 4: Working |
|---|---|---|
| Changes between runs | No | Yes |
| Model should | Internalize as constraints | Process as input |
| Configured during | Workspace setup (once) | Each run |
| Folder location | `_config/`, `references/` | `output/`, user-provided |
| Analogy | The recipe | The ingredients |

Mixing persistent rules with per-run artifacts in an undifferentiated context window forces the model to sort them on its own. Separating them in the folder structure means the model receives already-organized context.

---

## Five Design Principles

These principles (from MWP) guide every decision when building a workspace:

**1. One stage, one job.** Each workspace folder handles a single step of the workflow and writes its output to its own folder. A stage that fetches data does not also filter it. A stage that filters does not also format the final output. This follows McIlroy's Unix principle and Parnas's information-hiding criterion.

**2. Plain text as the interface.** Stages communicate through markdown and JSON files. No binary formats, no database connections. Any tool that can read a text file can participate. Any human who can open a text editor can inspect or modify any artifact.

**3. Layered context loading.** Agents load only the context they need for the current stage. Less irrelevant context means better model performance. This is prevention rather than compression  -  avoid loading irrelevant context in the first place.

**4. Every output is an edit surface.** The intermediate output of each stage is a file a human can open, read, edit, and save before the next stage runs. The human works with visible, manipulable objects, and the system picks up whatever the human left there.

**5. Configure the factory, not the product.** A workspace is set up once with the user's preferences, brand, style, and structural decisions. After that, each run of the pipeline produces a new deliverable using the same configuration. Reference material (Layer 3) is the factory. Working artifacts (Layer 4) are what the factory produces.

---

## Building a Workspace

### Step 1: Discovery  -  Interview the Workspace Owner

Before writing any files, understand the domain. Ask these questions:

1. **What is your role?** Title, responsibilities, who you collaborate with.
2. **What types of work do you produce?** List every recurring deliverable.
3. **Who are your audiences?** Internal teams, external customers, leadership  -  and how does tone shift between them?
4. **What terminology rules does your team follow?** Required terms, forbidden terms, product name rules.
5. **What does "good" look like?** Ask for 2-3 examples of outputs they're proud of.
6. **What mistakes does AI keep making with your content?** These become critical rules.
7. **What source materials do you typically start from?** PRDs, briefs, data exports, previous outputs  -  this defines Layer 4.

### Step 2: Stage Mapping  -  Find the Natural Breakpoints

Group the deliverables into workspace categories. Each category that has a **distinct process** or **distinct reference needs** gets its own folder.

Rules of thumb:
- If two task types share the same process AND the same config files → they can share a workspace folder.
- If they differ in process OR in which config files they need → separate folders.
- Aim for 4-12 workspace folders. Fewer than 4 means the structure probably isn't adding value. More than 12 means you might be over-segmenting.

For **sequential multi-stage pipelines** (e.g., research → script → production), use numbered folders:
```
stages/
├── 01_research/
├── 02_script/
└── 03_production/
```
The output/ of stage 01 becomes the Layer 4 input for stage 02. The human reviews at each boundary.

### Step 3: Scaffold the Folder Structure

```
team-workspace/
├── CLAUDE.md                  ← Layer 0
├── CONTEXT.md                 ← Layer 1
├── _config/                   ← Layer 3 (shared reference)
│   ├── voice.md
│   ├── terminology.md
│   ├── audiences.md
│   └── [domain-specific].md
├── [workspace-1]/             ← Layer 2
│   ├── CONTEXT.md
│   ├── references/            ← Layer 3 (stage-specific)
│   └── output/                ← Layer 4
├── [workspace-2]/
│   ├── CONTEXT.md
│   ├── references/
│   └── output/
└── _session-log/              ← optional: cross-session memory
```

### Step 4: Write CLAUDE.md (Layer 0)

```markdown
# CLAUDE.md  -  [Team/Person]'s Workspace
*Layer 0  -  Always load this file first.*

## Who I Am
[2-4 sentences: role, what the work covers, key collaborators, audiences]

## Workspace Map
[ASCII tree of the full folder structure, with layer annotations]

## How to Use This Workspace
1. Read this file (CLAUDE.md) first  -  always.
2. Read CONTEXT.md to find the right workspace for the task.
3. Navigate to the relevant workspace folder and read its CONTEXT.md.
4. Load only the _config/ files that workspace specifies.
5. Do the work. Write output to the workspace's output/ folder.

**Never load all _config/ files at once.**

## Critical Rules (Always Apply)
[Non-negotiable rules: terminology, forbidden patterns, audience conventions.
These apply to EVERY task regardless of workspace.]

## Role Context
[Working style preferences, iteration speed, output format defaults]
```

Keep this under ~800 tokens. It should be fast to load and easy to skim.

### Step 5: Write CONTEXT.md (Layer 1)

```markdown
# CONTEXT.md  -  Task Router
*Layer 1  -  Read this after CLAUDE.md.*

## Task Routing Table
| Task | Workspace | Load from _config/ |
|------|-----------|-------------------|
| [task description] | `[folder]/` | `file1.md`, `file2.md` |
| [task description] | `[folder]/` | `file1.md`, `file3.md` |

## Reference File Index
| File | Contains | When to load |
|------|----------|-------------|
| `_config/voice.md` | Tone, formatting, samples | Any writing task |
| `_config/terminology.md` | Required/forbidden terms | Any [domain] content |

## Workspace Index
| Folder | What it produces |
|--------|-----------------|
| `[workspace-1]/` | [deliverable types] |
| `[workspace-2]/` | [deliverable types] |
```

### Step 6: Write Config Files (Layer 3)

Every team needs at minimum:
- **voice.md**  -  tone by audience, formatting preferences, what to avoid, good/bad examples
- **terminology.md**  -  required terms, forbidden terms, product name rules, correction log

Domain-specific configs depend on the team. Marketing might add `messaging-framework.md`. Engineering might add `architecture-decisions.md`. Support might add `escalation-rules.md`.

Each config file should:
- Start with a Layer 3 header explaining when to load it
- Use tables for rules and comparisons
- Include concrete good/bad examples  -  examples teach more than rules
- Stay under ~500 tokens each (they share the context window with everything else)

### Step 7: Write Workspace CONTEXT.md Files (Layer 2)

This is where domain expertise lives. Each workspace gets a stage contract:

```markdown
# [workspace-name]/CONTEXT.md
*Layer 2  -  Stage contract.*

## What This Workspace Does
[Scope: what it produces, what it does NOT produce]

## Inputs

### Always load from _config/
- `voice.md`
- `terminology.md`

### Load when [condition]
- `[file].md`  -  [when this applies]

### Layer 4  -  working inputs (provided per run)
- [What the user provides: PRD, brief, data, previous stage output]

## Process

### Step 1  -  [verb]
[Specific instructions]

### Step 2  -  [verb]
[Specific instructions]

### Step 3  -  Quality check
[Verification steps before output]

## Outputs
Write completed work to `[workspace-name]/output/`.

| Output type | File name format | Notes |
|-------------|-----------------|-------|
| [type] | `[naming-convention].md` | [details] |

## Format Reference
[Templates showing exact output structure, with examples]
```

The process section is the heart. Don't write generic instructions  -  capture the actual steps this team takes to produce good work. Include quality checks and common mistakes.

### Step 8: Test and Iterate

Run a real task through the workspace:
1. Pick a deliverable the team produces regularly.
2. Provide source material as Layer 4 input.
3. Watch how Claude navigates the layers.
4. Check: Did it load the right files? Only the right files? Did it follow the process?
5. Evaluate output against the team's standards.

Common issues:
- Claude loads too many config files → tighten the routing table
- Missing team terminology → strengthen terminology.md
- Wrong tone → add more voice samples to voice.md with good/bad comparisons
- Skipping process steps → make the stage contract more explicit

**The edit-source principle:** If you find yourself editing the same thing in outputs repeatedly, that's a signal to fix the source  -  update the stage contract, voice guide, or reference file rather than patching outputs each time. Editing the output fixes this run. Editing the source fixes every future run.

---

## Portability

A workspace is a folder. It can be copied to another machine, committed to Git, emailed as a zip file, or synced through any cloud storage service. It carries its own prompts, its own context structure, its own stage definitions. There is no server to configure, no environment to replicate, no deployment step.

Every change to a prompt, every edit to a stage output, every configuration adjustment is diffable and reversible. Stage outputs can be committed after each run, creating a version history of the entire pipeline's behavior over time.

To hand off a workspace to another team: copy the folder. They open it, read the CLAUDE.md, and understand the entire system. They edit CONTEXT.md files with a text editor. No developer required.

---

## Attribution

This skill implements the Interpretable Context Methodology (ICM), based on the Model Workspace Protocol (MWP) described in:

> Van Clief, J. & McDermott, D. (2026). "Interpretable Context Methodology: Folder Structure as Agent Architecture." Eduba, University of Edinburgh.
> https://github.com/RinDig/Model-Workspace-Protocol-MWP-

The protocol is open source under the MIT License.
