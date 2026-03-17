# CLAUDE.md  -  [YOUR TEAM NAME]'s Workspace
*Layer 0  -  Always load this file first. It tells you who I am, how this workspace is organized, and where to find things.*

---

## Who I Am

<!-- Replace this with 2-4 sentences about your role.
     Include: your title, what your work covers, key collaborators, and audiences. -->

I'm a [YOUR ROLE] at [YOUR COMPANY]. My work spans:
- [WORK AREA 1] (examples: talk tracks, FAQ docs, training decks)
- [WORK AREA 2] (examples: release notes, product updates, process docs)
- [WORK AREA 3] (examples: positioning, messaging, event prep)

I work across these audiences: [LIST YOUR AUDIENCES].

---

## Workspace Map

<!-- Update this tree to match your actual folder structure.
     Add or remove workspace folders as needed. -->

```
[your-workspace]/
├── CLAUDE.md                  ← you are here (Layer 0)
├── CONTEXT.md                 ← task routing (Layer 1)
│
├── _config/                   ← stable reference material (Layer 3)
│   ├── voice.md
│   ├── terminology.md
│   └── audiences.md
│
├── [workspace-1]/             ← workspace (Layer 2)
│   ├── CONTEXT.md
│   └── output/
├── [workspace-2]/             ← workspace (Layer 2)
│   ├── CONTEXT.md
│   └── output/
└── [workspace-3]/             ← workspace (Layer 2)
    ├── CONTEXT.md
    └── output/
```

---

## How to Use This Workspace

1. Read this file (CLAUDE.md) first  -  always.
2. Read CONTEXT.md to find the right workspace for the task.
3. Navigate to the relevant workspace folder and read its CONTEXT.md.
4. Load only the _config/ files that workspace specifies.
5. Do the work. Write output to the workspace's output/ folder.

**Never load all _config/ files at once.** Each workspace specifies exactly which reference files it needs.

---

## Critical Rules (Always Apply)

<!-- These are your non-negotiable rules. They apply to EVERY task.
     Think: terminology mandates, forbidden words, audience conventions,
     formatting rules that never change. 3-8 rules is typical. -->

- [RULE 1: e.g., Always say "customer," never "client"]
- [RULE 2: e.g., Always use [Product Name] exactly  -  no abbreviations]
- [RULE 3: e.g., Label content by audience: [Sales] [CS] [SC] [All]]
- [RULE 4: e.g., Lead with customer value, not product mechanics]

---

## Role Context

<!-- Working preferences that help Claude calibrate. -->

- [PREFERENCE 1: e.g., I prefer plain language and direct structure]
- [PREFERENCE 2: e.g., Drafts are more useful than polished first passes]
- [PREFERENCE 3: e.g., Outputs are usually shared via Slack or Google Slides]
