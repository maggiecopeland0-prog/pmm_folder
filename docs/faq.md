# ICM Frequently Asked Questions

## Getting Started

**How many workspace folders should I have?**
Aim for 4-12. Fewer than 4 means the structure probably isn't adding value  -  you might be better off with a single detailed prompt. More than 12 means you might be over-segmenting. The test: if two workspaces share the same process AND the same config files, merge them.

**How long should each file be?**
CLAUDE.md: ~800 tokens (one screen of text). CONTEXT.md routing table: ~300 tokens. Workspace CONTEXT.md: 200-500 tokens. Config files: 500-2,000 tokens each. The total context at any stage should be 2,000-8,000 tokens. If you're exceeding that, you're loading too much.

**Do I need all five layers?**
You need Layers 0-2 (CLAUDE.md, CONTEXT.md, workspace CONTEXT.md) as the structural backbone. Layer 3 (config files) is where quality comes from  -  skip it and outputs will be generic. Layer 4 (working inputs) is just whatever you provide each run.

**Can I use this with models other than Claude?**
ICM is model-agnostic. The folder structure, file formats, and naming conventions don't depend on any model-specific capability. Point a different model at the same files and it works. Whether the results are equivalent depends on how different models handle the same context, but the protocol itself imposes no vendor lock-in.

---

## Structure and Organization

**What's the difference between _config/ and references/?**
`_config/` lives at the workspace root and holds shared reference material (voice, terminology, audiences). `references/` lives inside a workspace folder and holds stage-specific reference material that only that workspace needs. Both are Layer 3  -  the distinction is scope, not function.

**When should I use numbered stage folders (01_research/, 02_draft/)?**
Use numbered folders when your workflow is sequential  -  each stage reads the previous stage's output. Use named folders (release-notes/, event-prep/) when workspaces are independent task types that don't feed into each other.

**Where do scripts go?**
If you have helper scripts (Python, shell) for deterministic tasks like data formatting or file conversion, put them in a `scripts/` folder at the workspace root or inside the relevant stage folder. The CONTEXT.md should reference them with clear instructions on when and how to run them.

---

## Working With the Workspace

**How do I update the workspace over time?**
Edit the markdown files with any text editor. If outputs consistently have the same problem, trace it to the source: update the voice guide, add a correction to terminology.md, or refine the process in a workspace CONTEXT.md. Commit changes to Git for version history.

**What if Claude loads the wrong config files?**
Tighten the routing table in CONTEXT.md. Make sure each row specifies exactly which config files to load. If Claude is loading files not listed, the routing table may be ambiguous.

**What if outputs are too generic?**
Add more voice samples to voice.md. Real good/bad examples teach the model more than any rule. Also check that the workspace CONTEXT.md process section is specific enough  -  generic instructions produce generic outputs.

**Can multiple people use the same workspace?**
Yes. The workspace is a folder  -  share it via Git, cloud storage, or a zip file. Each person can run it independently. If someone improves a config file, commit it so everyone benefits.

---

## Handoff and Sharing

**How do I hand off a workspace to another team?**
Copy the folder. They open CLAUDE.md, read through the structure, and they're oriented. They can start running tasks immediately and edit the config files to fit their domain. No developer, no framework, no deployment step.

**Can I version-control my workspace?**
Yes  -  ICM workspaces are Git-compatible by default. Every change is diffable. You can commit stage outputs after each run to create a version history of the pipeline's behavior. Use the .gitignore pattern from this repo to exclude output/ folders and session logs if you prefer.

**What if I want to duplicate a workspace for a different domain?**
Copy the workspace folder, rename it, and update the CONTEXT.md files and config files for the new domain. Keep the structural pattern (Layer 0-4) the same. Most people find it faster to adapt an existing workspace than to build from scratch.
