# Operating a Workspace

The setup guide and the design principles cover how to *build* a workspace. This doc covers how to *live with one* after it exists. These are the lessons that only show up once a workspace has been in daily use for a while: state that carries across sessions, workspaces that finish or go quiet, and folder counts that grow past the original guidance.

None of this changes the five-layer model. It extends it with the operational patterns that keep a workspace healthy over time.

---

## The Memory Layer

The five layers describe everything an agent needs to do a task *in a single session*. But work doesn't happen in single sessions. You start a deliverable on Monday, get interrupted, and come back Thursday. Between those two points, the agent forgets everything: the decisions you made, the dead ends you ruled out, the correction you gave it, the half-finished artifact and what was left to do.

A session log is where that state lives. It's an optional extension to the five-layer model: a folder (commonly `_session-log/`) holding short markdown notes that let a future session pick up where the last one left off.

This is content, not structure. Like Layer 4 working artifacts, session logs are written fresh as work happens rather than configured once during setup. The difference is that they're written *by* the agent (or you) at the *end* of a session, for the *next* session to read.

### What goes in a session log

A useful log captures the things that won't survive on their own:

- **Decisions made**, and the reasoning behind them, so they don't get relitigated.
- **Open questions** still unresolved when the session ended.
- **Mental-model corrections**, the moments where the agent misunderstood something and you set it straight. These are the highest-value notes, because the same misunderstanding will recur otherwise.
- **Artifact state**, what's done, what's half-done, and what's next.

It does *not* need to be a transcript. A log that's longer than the work it describes isn't earning its place. A few lines per topic is usually enough.

### The resume protocol

The memory layer only works if the agent actually reads it when resuming. Make that explicit in your Layer 0 file (`CLAUDE.md`): when the user references previous work ("let's continue X," "pick up where we left off," "the thing we were building"), the agent should check `_session-log/` for the most recent entry on that topic *before* doing anything else, read it fully, then proceed.

Without this instruction, the logs exist but never get loaded, and the memory layer does nothing.

### Keep one naming convention

Session logs accumulate fast, and it's easy to end up with several overlapping naming schemes for what is essentially the same kind of note. Pick one convention early (for example, `YYYY-MM-DD-topic.md`) and keep a lightweight index file so the agent can find the right entry without scanning every file.

**In practice:** treat the session log as the workspace's working memory. The discipline is to write a short note at the end of any session whose state matters, and to read the latest note at the start of any session that resumes prior work.

---

## Workspace Lifecycle

The setup guide tends to imply that workspace folders are permanent. In practice they have a lifecycle. Some are used constantly. Some served a one-time project and are now finished. Some are seasonal, quiet for months and then suddenly relevant again.

A workspace that doesn't account for this slowly fills with folders that look active but aren't, which makes the structure harder to read and tempts the routing table into loading things that no longer apply.

The fix is to give every workspace a status:

| Status | Meaning | How it's treated |
|---|---|---|
| **Active** | In regular use | Listed in the routing table; loaded normally |
| **Dormant** | Not currently in use, but may return | Kept in place, marked dormant, left out of the active routing table |
| **Archived / reference** | Finished; kept only for reference | Marked clearly; never routed to for new work |

Two rules of thumb:

- **Mark status in the workspace map** (in `CLAUDE.md`) so the state is visible at a glance, not something you have to remember.
- **Archive, don't delete.** A finished workspace is a record of how that work was done. Keeping it costs nothing as long as it's clearly marked and kept out of active routing.

**In practice:** when a workspace stops being used, change its status rather than leaving it to look active or deleting it outright. Dormant and archived workspaces should not appear in the active routing table, so they never add to what the agent loads for live work.

---

## How Many Workspaces, Revisited

The FAQ suggests aiming for 4–12 workspace folders and treats anything past 12 as over-segmentation. That holds for a new workspace. It stops holding for one that's been in active use for a while, where a larger number of genuinely distinct folders is normal and healthy.

The number was always a proxy for the real test, which is stated elsewhere in the design principles:

> Two task types can share a folder if they share the same process **and** the same config files. If they differ in process **or** in which config files they need, they get separate folders.

That test is what actually decides whether a folder earns its place. The count is just a signal.

So treat 12 not as a ceiling but as a checkpoint. Passing it doesn't mean you've over-segmented. It means it's worth a look to confirm two things:

1. Each folder still passes the distinct-process-or-distinct-config test.
2. The growth is real work, not lifecycle clutter (see above), where finished or dormant workspaces are inflating the count without adding active surface.

If both check out, a large workspace is working as intended.

**In practice:** don't prune a folder just to stay under a number. Prune it only if it fails the distinctness test or has gone dormant. A workspace that's grown because the work has grown is not a problem to fix.

---

## Where This Shows Up: The Workspace Map

Both patterns live in one place the agent always reads: the workspace map in `CLAUDE.md`. The memory layer gets a line of its own alongside `_config/`, and each workspace folder carries its status inline.

```
team-workspace/
├── CLAUDE.md                  ← Layer 0 (identity, rules, this map)
├── CONTEXT.md                 ← Layer 1 (routing table)
│
├── _config/                   ← Layer 3 (stable reference)
│   ├── voice.md
│   ├── terminology.md
│   └── audiences.md
│
├── _session-log/              ← memory layer (cross-session state)
│
├── release-notes/             ← active
├── enablement-decks/          ← active
├── event-prep/                ← active
├── reports/                   ← dormant (seasonal; quiet until quarter-end)
└── product-launch-q1/         ← archived (completed; reference only)
```

Reading top to bottom, the map now answers three questions at a glance: where cross-session memory lives, which workspaces are in active use, and which are kept only for reference. None of that requires opening another file.

---

## Attribution

These patterns extend the Interpretable Context Methodology (ICM), based on the Model Workspace Protocol (MWP) described in:

> Van Clief, J. & McDermott, D. (2026). "Interpretable Context Methodology: Folder Structure as Agent Architecture." Eduba, University of Edinburgh.
