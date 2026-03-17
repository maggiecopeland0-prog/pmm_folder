# enablement-decks/CONTEXT.md
*Layer 2 - Stage contract.*

---

## What This Workspace Does

Produces sales enablement materials: training decks, FAQ docs, and quick-reference cards for internal teams.

---

## Inputs

### Always load from _config/
- `voice.md`
- `terminology.md`
- `audiences.md`

### Per run
- Feature description or PRD
- Target audience (Sales, CS, SC, or mixed)
- Format: deck, FAQ, or quick-reference card

---

## Process

1. Identify the audience. If mixed, label each section.
2. Extract key messages: what it does, why it matters, common questions.
3. Draft in the specified format.
4. Quality check: audience labels present, no jargon in [Sales]/[CS] sections, feature names match terminology.md.

---

## Output

Write to `enablement-decks/output/`.

| Type | File name |
|------|----------|
| Deck | `deck-[topic]-[date].md` |
| FAQ | `faq-[topic]-[date].md` |
| Quick-reference | `qrc-[topic]-[date].md` |
