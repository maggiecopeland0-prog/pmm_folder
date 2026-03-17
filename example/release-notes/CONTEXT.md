# release-notes/CONTEXT.md
*Layer 2  -  Stage contract. Read this after CLAUDE.md and CONTEXT.md.*

---

## What This Workspace Does

Produces internal release notes and Slack announcements for product updates. Outputs are written for internal audiences (Sales, CS, SC) and shared via Slack or internal documentation.

This workspace handles:
- Short Slack announcements (3-5 sentences)
- Longer internal release notes (structured format)
- Feature update posts for mixed internal audiences

---

## Inputs

### Always load from _config/
- `voice.md`  -  tone, formatting rules, what to avoid
- `terminology.md`  -  product name rules, required/forbidden terms

### Layer 4  -  working inputs (provided per run)
- Source material: PRD, product brief, engineering notes, or feature description
- Audience specification: who is this announcement for?
- Format specification: Slack announcement or full release note?

---

## Process

### Step 1  -  Extract
Read the source material. Identify:
- What changed (specific, factual)
- Who it affects
- Any terminology that needs correcting before drafting

### Step 2  -  Frame the value
Before writing, map the feature to this canvas:
```
You're trying to [customer use case]
by [current way]
but [limitation]
which leads to [problem]

Now, you can [capability]
with [feature name]
so that [benefit]
```
This ensures the announcement leads with customer value, not product mechanics.

### Step 3  -  Draft
Write in the format specified (Slack or full release note  -  see templates below).

### Step 4  -  Quality check
Before output, verify:
- No forbidden terms (check terminology.md)
- Tone matches the audience (check voice.md)
- Lead sentence is customer value, not product description
- Under word count limit for the format

---

## Outputs

Write completed drafts to `release-notes/output/`.

| Output type | File name format | Notes |
|-------------|-----------------|-------|
| Slack announcement | `slack-[feature-name]-[date].md` | 3-5 sentences, ready to paste |
| Full release note | `release-note-[feature-name]-[date].md` | Structured format with headers |

---

## Format Reference  -  Slack Announcement

```
*[Feature Name]* is now available in [specific location].

[One sentence: what it does in plain language.]
[One sentence: why it matters  -  customer outcome.]
[One sentence: how to access or use it.]
```

Rules: Bold the feature name. No filler. Under 5 sentences.

---

## Format Reference  -  Full Release Note

```
## [Feature Name]
**Status:** [Now available / Rolling out]
**Audience:** [All] or use labels

[Lead paragraph  -  2-3 sentences. What changed and why it matters.]

**What changed**
[Bullet list of specific changes.]

**Why it matters**
[Customer outcome framing.]

**How to use it**
[Steps or where to find it.]

**[SC] Technical notes** *(if applicable)*
[Details SCs need that Sales and CS don't.]
```
