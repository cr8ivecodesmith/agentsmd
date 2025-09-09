Agent Guidelines
================

Role: AI coding assistant

Expertise: Fullstack software engineering

Mode:
You are working as a pair-programming partner of the human engineer.

Scope
=====

These guidelines apply to the entire directory tree of the root project directory.

Directory Map
=============

```
 <project>  # root project dir
├──  agentsmd
│   └──  guides  # coding style, architecture patterns, and workflows
│   └──  tasks  # project tasks with specs and attachments
│   └──  share  # shared resources and templates used across tasks
└── ...  # other project files and folders
```

Workflow
========

- Start with the relevant guide:
  - See `guides/workflow.md` for the end‑to‑end task flow and checkpoints.
  - See `guides/styleguides.md` and `guides/patterns_and_architecture.md` for code and docs style.
- For tasks:
  - Browse `tasks/{bug,feat,patch,misc}/` and open the task folder (e.g., `tasks/misc/0000-initalize_project`).
  - Read `spec.md` first. Follow any explicit constraints in that spec over general guidance.
  - Use the `attachments/` folder as the source of boilerplate or reference content; copy into the project as needed.
  - If the spec includes a History section, append concise entries describing changes you made.
- Keep changes minimal and focused on the task:
  - Avoid renaming files or large refactors unless the spec calls for it.
  - Update or add documentation alongside code changes where applicable.
  - Prefer small, verifiable edits over broad rewrites.

Conventions
===========

- Documentation style:
  - Top‑level headings use overline style with `===` on the next line (as in this file).
  - Favor semantic line breaks for readability and smaller diffs (see `guides/styleguides.md`).
  - Keep sections short; use lists and examples where they clarify intent.
- Code style:
  - Follow language‑specific sections in `guides/styleguides.md`.
  - Align with patterns from `guides/patterns_and_architecture.md` (composition first, small functions, idempotence).
- Task naming:
  - Folders typically use a zero‑padded index and kebab/underscore case (e.g., `0000-initalize_project`).
  - Keep names descriptive and stable once created.

Tools
=====

- ripgrep (preferred search)
  - Find files: `rg --files`
  - Search with line numbers: `rg -n "pattern"`
  - Limit or include globs: `rg -g '!dist/**' -n "pattern"`
  - Search headings in Markdown: `rg -n "^#|^===|^##" *.md`

Tips
====

- Read before you change: scan related guides and the task spec to avoid rework.
- Keep diffs tight: implement the smallest change that solves the task well.
- Prefer examples: when adding docs, include a short example over long prose.
- Cross‑reference: link to guides in this folder rather than duplicating content.

Do / Don’t
==========

- Do
  - Honor task‑specific instructions over general conventions.
  - Update docs alongside code changes when behavior or usage changes.
  - Use `ripgrep` for fast, precise searches.
- Don’t
  - Perform unrelated refactors or rename files without a clear task requirement.
  - Introduce new style patterns not covered by guides unless justified by the task.
  - Duplicate attachments content; import or reference it instead.
