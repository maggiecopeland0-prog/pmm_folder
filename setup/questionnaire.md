# ICM Workspace Setup Questionnaire

Use this questionnaire to gather the information you need before building a workspace. Work through it with Claude, or fill it in yourself and use the answers to populate the template files.

---

## Part 1: Identity (feeds CLAUDE.md)

1. **What is your role?**
   - Title:
   - Team / department:
   - Company:

2. **What does your work cover?** List the main categories of work you do (e.g., sales enablement, documentation, event prep, research, reporting).

3. **Who do you collaborate with most?** (e.g., Product teams, Sales, Engineering, executives)

4. **Who are your audiences?** List every group that consumes your outputs, and briefly describe what they need from you.

---

## Part 2: Task Mapping (feeds CONTEXT.md routing table)

5. **What types of deliverables do you produce regularly?** List everything  -  even small recurring tasks.
   Examples: release notes, FAQ docs, training decks, presenter briefs, reports, newsletters, battlecards, talk tracks...

6. **For each deliverable type, answer:**
   - What source material do you start from? (PRD, brief, data, previous output, nothing)
   - Who is the audience?
   - What format does it end up in? (Slack post, slide deck, Word doc, email, etc.)
   - How often do you produce it?

7. **Which of these deliverable types share a similar process?** Group them into clusters. Each cluster will become a workspace folder.

---

## Part 3: Voice and Style (feeds _config/voice.md)

8. **How would you describe your team's writing style in 3-4 words?** (e.g., "direct, plain, structured")

9. **What does good output look like from your team?** Paste 2-3 real examples of work you're proud of. These become your voice samples.

10. **What does bad output look like?** Paste 2-3 examples of the kind of writing you want to avoid (or that AI tends to produce without guidance).

11. **What formatting rules matter to your team?**
    - Header conventions?
    - Bullet vs. prose preferences?
    - Length limits?
    - Platform-specific formatting (Slack, slides, etc.)?

12. **What should always be avoided in your content?** (Filler phrases, passive voice, hedging, specific words, em dashes, etc.)

---

## Part 4: Terminology (feeds _config/terminology.md)

13. **What terms does your team always use?** List required words and what they replace.
    - "Always say _____, never _____"

14. **What product or service names must be used exactly?** List them with common misspellings or variations.

15. **What mistakes does AI keep making with your terminology?** These become your correction log.

---

## Part 5: Audiences (feeds _config/audiences.md)

16. **For each audience, describe:**
    - What they need from your content
    - What tone works for them
    - What format they prefer
    - What they care about most

17. **Do you produce documents that serve multiple audiences at once?** If so, how do you currently structure them? (Separate sections? Labels? Different versions?)

---

## Part 6: Process (feeds workspace CONTEXT.md files)

18. **For each workspace cluster (from question 7), describe the step-by-step process you follow to produce the deliverable.** Be specific  -  what do you do first, second, third?

19. **What quality checks do you run before publishing?** (Terminology review, tone check, audience appropriateness, format compliance, etc.)

20. **What are the most common mistakes in your outputs?** (These become explicit process steps or quality checks.)

---

## Part 7: Critical Rules (feeds CLAUDE.md)

21. **What rules apply to every single task, regardless of type?** These are your non-negotiables. Examples:
    - Terminology mandates ("always X, never Y")
    - Audience conventions ("always label sections by audience")
    - Formatting rules ("no em dashes," "no walls of text")
    - Product rules ("never describe X as proactive")

---

## Next Steps

Once you've completed this questionnaire:

1. Copy the `template/` folder and rename it for your team.
2. Fill in `CLAUDE.md` using Parts 1 and 7.
3. Fill in `CONTEXT.md` using Part 2.
4. Fill in `_config/voice.md` using Part 3.
5. Fill in `_config/terminology.md` using Part 4.
6. Fill in `_config/audiences.md` using Part 5.
7. Create workspace folders and fill in their `CONTEXT.md` files using Parts 2 and 6.
8. Run a real task through the workspace and iterate.
