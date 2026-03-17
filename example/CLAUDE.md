# CLAUDE.md  -  Product Marketing Workspace
*Layer 0  -  Always load this file first. It tells you who I am, how this workspace is organized, and where to find things.*

---

## Who I Am

I'm a Product Marketing Manager (PMM). My work spans sales enablement (talk tracks, FAQ docs, battlecards, training decks), internal documentation (release notes, product updates), go-to-market content (positioning, messaging), and event preparation (presenter briefs, talking points).

I work across multiple internal audiences: Sales reps, Customer Success Managers (CSMs), and Solutions Consultants (SCs). I collaborate frequently with Product teams and executive stakeholders.

---

## Workspace Map

```
pmm-workspace/
├── CLAUDE.md                  ← you are here (Layer 0)
├── CONTEXT.md                 ← task routing (Layer 1)
│
├── _config/                   ← stable reference material (Layer 3)
│   ├── voice.md
│   ├── terminology.md
│   └── audiences.md
│
├── release-notes/             ← workspace (Layer 2)
│   ├── CONTEXT.md
│   └── output/
├── enablement-decks/          ← workspace (Layer 2)
│   ├── CONTEXT.md
│   └── output/
└── event-prep/                ← workspace (Layer 2)
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

- Always say **customer**, never "client"
- Always say **overview**, never "summary" when describing AI-generated outputs
- Use audience labels [Sales] [CS] [SC] [All] when content varies by role
- Lead with customer value, not product mechanics
- Avoid em dashes  -  restructure the sentence instead

---

## Role Context

- I produce content for mixed audiences  -  some technical (SCs), some not (Sales, CS)
- Outputs are often shared directly via Slack or internal slides
- I prefer plain language, direct structure, and minimal jargon
- Drafts over perfection  -  a usable first pass is more valuable than a polished final
