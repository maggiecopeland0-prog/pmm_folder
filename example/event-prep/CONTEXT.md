# event-prep/CONTEXT.md
*Layer 2  -  Stage contract. Read this after CLAUDE.md and CONTEXT.md.*

---

## What This Workspace Does

Produces event preparation materials: presenter briefs, talking points, speaker notes, and event agendas. Content supports internal presenters who need to deliver product-related sessions to external or internal audiences.

---

## Inputs

### Always load from _config/
- `voice.md`  -  tone and formatting
- `audiences.md`  -  who the presenter is speaking to

### Layer 4  -  working inputs (provided per run)
- Event details: name, date, audience, format (keynote, panel, demo, workshop)
- Session topic or abstract
- Presenter name and background (if available)
- Time limit

---

## Process

### Step 1  -  Understand the context
Identify: Who is presenting? To whom? How long? What format? What's the one thing the audience should remember?

### Step 2  -  Build the brief
Structure:
- **Session goal**  -  one sentence
- **Audience profile**  -  who's in the room, what they care about
- **Key messages**  -  3 max
- **Talk track**  -  the narrative arc (opening hook → context → key points → close)
- **Landmines**  -  topics to avoid or handle carefully

### Step 3  -  Write supporting materials
- **Talking points:** Numbered list, 1-2 sentences each, written in speakable language
- **Speaker notes:** Tied to slides if applicable, include transitions between sections
- **Q&A prep:** 5-8 anticipated questions with suggested answers

### Step 4  -  Quality check
- Talking points sound natural when read aloud (no written-language constructions)
- Time estimate fits the slot
- Key messages are consistent across all materials
- No jargon the audience wouldn't know

---

## Outputs

Write to `event-prep/output/`.

| Output type | File name format |
|-------------|-----------------|
| Presenter brief | `brief-[event]-[date].md` |
| Talking points | `talking-points-[event]-[date].md` |
| Q&A prep | `qa-[event]-[date].md` |
