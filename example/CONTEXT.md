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

| Task | Workspace | Load from _config/ |
|------|-----------|-------------------|
| Write a Slack release note or product update | `release-notes/` | `voice.md`, `terminology.md` |
| Write a longer feature announcement | `release-notes/` | `voice.md`, `terminology.md` |
| Build or update a sales enablement deck | `enablement-decks/` | `voice.md`, `terminology.md`, `audiences.md` |
| Write a training guide or FAQ doc | `enablement-decks/` | `voice.md`, `terminology.md`, `audiences.md` |
| Write a presenter brief or talking points | `event-prep/` | `voice.md`, `audiences.md` |
| Prepare speaker notes for an event | `event-prep/` | `voice.md`, `audiences.md` |

---

## Reference File Index

| File | Contains | When to load |
|------|----------|-------------|
| `_config/voice.md` | Tone, formatting rules, what to avoid, good/bad samples | Any writing task |
| `_config/terminology.md` | Required terms, forbidden terms, product name rules | Any content touching products |
| `_config/audiences.md` | Audience profiles, what each group needs, how tone shifts | Multi-audience content or tailored messaging |

---

## Workspace Index

| Folder | What it produces |
|--------|-----------------|
| `release-notes/` | Slack announcements, internal release notes, product update posts |
| `enablement-decks/` | Sales training decks, FAQ documents, onboarding materials |
| `event-prep/` | Presenter briefs, talking points, speaker prep, event agendas |
