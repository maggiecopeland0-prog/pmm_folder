# ICM Design Principles

These principles come from the Model Workspace Protocol (MWP) by Van Clief & McDermott. They guide every decision when building and maintaining an ICM workspace.

---

## 1. One Stage, One Job

Each workspace folder handles a single type of work. A stage that researches does not also draft. A stage that drafts does not also format the final output. This follows McIlroy's Unix principle (make each program do one thing well) and Parnas's information-hiding criterion (decompose based on what each module hides from the rest).

In practice: if you find a workspace CONTEXT.md trying to cover too many different processes, split it into separate folders.

## 2. Plain Text as the Interface

Stages communicate through markdown and JSON files. No binary formats, no database connections, no proprietary serialization. Any tool that can read a text file can participate in the workflow. Any human who can open a text editor can inspect or modify any artifact.

In practice: your workspace should be fully functional with nothing more than a text editor and an AI agent. If it requires special software to read or edit, simplify.

## 3. Layered Context Loading

Agents load only the context they need for the current stage. Less irrelevant context means better model performance. Research by Liu et al. (2024) showed that LLMs perform significantly worse when relevant information is buried in the middle of long contexts. ICM prevents this by design  -  each stage only sees the files it needs.

In practice: never load all _config/ files at once. The routing table exists to prevent this. When in doubt, leave a file out of a workspace's load list  -  add it back if outputs suffer.

## 4. Every Output is an Edit Surface

The intermediate output of each stage is a file a human can open, read, edit, and save before the next stage runs. This implements Horvitz's mixed-initiative principle: the human works with visible, manipulable objects, and the system picks up whatever the human left there.

In practice: write outputs to the output/ folder as plain files. The human reviews them, edits if needed, and the next stage (or the human themselves) uses whatever is there.

## 5. Configure the Factory, Not the Product

A workspace is set up once with preferences, brand, style, and structural decisions. After that, each run produces a new deliverable using the same configuration. Layer 3 (reference material) is the factory. Layer 4 (working artifacts) is what the factory produces each time.

In practice: invest time in your _config/ files and workspace CONTEXT.md files during setup. Once they're solid, every subsequent run benefits. If you find yourself making the same edit to outputs repeatedly, fix the source (the config or process file) instead.

---

## The Edit-Source Principle

This deserves special emphasis. When an output has a recurring problem, there are two responses:

1. **Edit the output.** Fixes this run. The same problem will appear next time.
2. **Edit the source.** Fixes this run and every future run.

If you consistently tighten opening paragraphs, that's a signal the stage contract should say "keep the opening under three sentences." If the tone drifts formal, the voice guide needs a stronger example. Recurring output edits are debugging information  -  they point to fixable source-level problems.

---

## Observability as a Side Effect

Because every intermediate output is a plain file, an ICM workspace is observable by default. There is no logging layer to build, no dashboard to configure. You open the folder and read the files. This transparency is not a feature added on top  -  it's an inherent property of the architecture. The workspace cannot run without generating inspectable intermediate artifacts, because those artifacts are how the stages communicate.

---

## Attribution

These principles are described in detail in:

> Van Clief, J. & McDermott, D. (2026). "Interpretable Context Methodology: Folder Structure as Agent Architecture." Eduba, University of Edinburgh.
