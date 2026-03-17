# CONTEXT.md  -  Task Router
*Layer 1  -  Read this after CLAUDE.md. It tells you which workspace and reference files to load for any given task.*

---

## How to Use This File

1. Find the task type below that matches what's being asked.
2. Load only the listed reference files from `_config/`.
3. Navigate to the listed workspace folder and read its `CONTEXT.md`.
4. Do the work.

If a task doesn't match any category exactly, pick the closest one and note the gap.

---

## Task Routing Table

<!-- Fill in one row per task type. Each row maps a task to a workspace folder
     and specifies which config files to load. This is the core routing mechanism. -->

| Task | Workspace | Load from _config/ |
|------|-----------|-------------------|
| [TASK DESCRIPTION 1] | `[workspace-1]/` | `voice.md`, `terminology.md` |
| [TASK DESCRIPTION 2] | `[workspace-1]/` | `voice.md`, `terminology.md` |
| [TASK DESCRIPTION 3] | `[workspace-2]/` | `voice.md`, `terminology.md`, `audiences.md` |
| [TASK DESCRIPTION 4] | `[workspace-3]/` | `voice.md`, `audiences.md` |

---

## Reference File Index

<!-- Document each config file: what it contains and when to load it. -->

| File | Contains | When to load |
|------|----------|-------------|
| `_config/voice.md` | Tone, formatting rules, samples | Any writing task |
| `_config/terminology.md` | Required/forbidden terms, product names | Any content touching your domain |
| `_config/audiences.md` | Audience profiles, how tone shifts | Multi-audience content |

---

## Workspace Index

<!-- One row per workspace folder, describing what it produces. -->

| Folder | What it produces |
|--------|-----------------|
| `[workspace-1]/` | [DELIVERABLE TYPES] |
| `[workspace-2]/` | [DELIVERABLE TYPES] |
| `[workspace-3]/` | [DELIVERABLE TYPES] |
