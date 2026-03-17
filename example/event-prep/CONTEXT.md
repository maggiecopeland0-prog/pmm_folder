# event-prep/CONTEXT.md
*Layer 2 - Stage contract.*

---

## What This Workspace Does

Produces event preparation materials: presenter briefs, talking points, and Q&A prep for internal presenters.

---

## Inputs

### Always load from _config/
- `voice.md`
- `audiences.md`

### Per run
- Event details (name, date, audience, format, time limit)
- Session topic or abstract
- Presenter name (if available)

---

## Process

1. Identify who is presenting, to whom, for how long, and in what format.
2. Build a brief: session goal (one sentence), key messages (3 max), talk track (opening > context > key points > close), and landmines to avoid.
3. Write talking points in speakable language and anticipated Q&A.
4. Quality check: points sound natural read aloud, time estimate fits the slot, no unfamiliar jargon.

---

## Output

Write to `event-prep/output/`.

| Type | File name |
|------|----------|
| Brief | `brief-[event]-[date].md` |
| Talking points | `talking-points-[event]-[date].md` |
| Q&A prep | `qa-[event]-[date].md` |
