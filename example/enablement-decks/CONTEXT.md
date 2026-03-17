# enablement-decks/CONTEXT.md
*Layer 2  -  Stage contract. Read this after CLAUDE.md and CONTEXT.md.*

---

## What This Workspace Does

Produces sales enablement materials: training decks, FAQ documents, quick-reference cards, and onboarding guides. Content targets internal teams who need to understand, position, and support products.

---

## Inputs

### Always load from _config/
- `voice.md`  -  tone and formatting
- `terminology.md`  -  product name rules
- `audiences.md`  -  audience profiles and mixed-audience rules

### Layer 4  -  working inputs (provided per run)
- Feature description or PRD
- Target audience (Sales, CS, SC, or mixed)
- Format: slide deck, FAQ doc, or quick-reference card

---

## Process

### Step 1  -  Identify the audience
Determine who this is for. If mixed, plan the document structure so each audience gets labeled sections.

### Step 2  -  Extract key messages
From the source material, pull out:
- What the feature does (plain language)
- Why it matters to each audience
- Common questions the audience will have
- Competitive context (if relevant)

### Step 3  -  Structure the deliverable
- **Decks:** One idea per slide. Headlines are complete sentences that state the point. Bullets support, not repeat.
- **FAQ docs:** Group by audience. Lead with [All] questions. Use the exact words customers and reps would use.
- **Quick-reference cards:** Single page. Three sections max. Scannable in under 60 seconds.

### Step 4  -  Quality check
- Every section has an audience label
- No jargon in [Sales] or [CS] sections
- [SC] sections are precise enough to answer a technical question
- Feature names match terminology.md exactly

---

## Outputs

Write to `enablement-decks/output/`.

| Output type | File name format |
|-------------|-----------------|
| Training deck content | `deck-[topic]-[date].md` |
| FAQ document | `faq-[topic]-[date].md` |
| Quick-reference card | `qrc-[topic]-[date].md` |
