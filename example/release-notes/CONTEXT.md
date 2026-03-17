# release-notes/CONTEXT.md
*Layer 2 - Stage contract. Read this after CLAUDE.md and CONTEXT.md.*

---

## What This Workspace Does

Produces internal release notes and Slack announcements for product updates. Shared with Sales, CS, and SC audiences via Slack or internal docs.

---

## Inputs

### Always load from _config/
- `voice.md`
- `terminology.md`

### Per run
- Source material (PRD, product brief, or engineering notes)
- Target audience
- Format: Slack announcement or full release note

---

## Process

### Step 1 - Extract
Read the source material. Identify what changed, who it affects, and flag any terminology to correct before drafting.

### Step 2 - Draft
Lead with customer value, not product mechanics. Write in the specified format (see template below).

### Step 3 - Quality check
- No forbidden terms (check terminology.md)
- Tone matches the audience (check voice.md)
- Lead sentence states the customer benefit
- Under 5 sentences for Slack, under 300 words for full release note

---

## Output

Write to `release-notes/output/`.

| Type | File name | Length |
|------|----------|--------|
| Slack announcement | `slack-[feature]-[date].md` | 3-5 sentences |
| Full release note | `release-note-[feature]-[date].md` | Structured with headers |

---

## Template - Slack Announcement

```
*[Feature Name]* is now available in [location].

[What it does in plain language.]
[Why it matters - customer outcome.]
[How to access or use it.]
```
