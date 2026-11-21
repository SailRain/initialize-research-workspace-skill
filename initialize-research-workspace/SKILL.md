---
name: initialize-research-workspace
description: Initialize a new research project folder or help its owner organize an existing one. Use for setting up model-specific Git repositories, program output locations, and project documents in the user's language, with a read-only review and owner confirmation for existing workspaces.
---

# Initialize a research workspace

Work in the research folder the user designates. Resolve the templates relative to this skill and project paths relative to the research folder. If the requested target is ambiguous, establish its location before writing.

## Choose the language of the project documents

Honor an explicit request for the language of the generated documents. Otherwise, infer the user's language from their own conversational messages, including their latest clarification. Filenames, code, pasted papers, and these English templates are weak language signals. If the request is mixed or too short to tell and prior messages give no clear answer, ask which language to use. If an existing project has a conflicting document-language rule, resolve it with the owner during the review.

Write all new project-facing prose in that language, including headings, table labels, examples, instructions, and placeholders such as “To be confirmed.” Preserve literal filenames, paths, Git commands, code identifiers, and scientific symbols. Use the same language for the inventory, confirmation questions, and handoff unless the user requests a different response language. In an existing file, preserve its author's content and wording outside the approved edits. Translating existing passages requires agreement on that change.

## Inspect the folder and choose a route

Inspect the target's directory entries, including hidden entries. Check whether the target is a Git working tree, contains a repository, or lies within an enclosing Git workspace. A `.git` file can identify a linked worktree. For a working-tree check, use `git -C <target> rev-parse --show-toplevel`. If Git is unavailable or the target cannot be inspected reliably, report the missing information before treating it as empty.

**Empty standalone folder.** Take the direct route when the folder is empty or contains only a regular `.DS_Store` file, and it has no existing Git boundary. Preserve the metadata file and carry out these steps once the target and language are clear.

1. Create `PROG1/output/`, `PROG_temp/output/`, and the root `output/`, `figures/`, `references/`, and `simulation/`. Add simulator subdirectories only for software the project uses.
2. Initialize Git inside `PROG1/` with `git -C <target>/PROG1 init`. Leave commits, remote configuration, and publishing to the owner.
3. Write the three root documents from the templates below. Use `PROG1/` as the active formal directory. Use localized placeholders for unknown project facts. Include the recordkeeping guidance in `AGENTS.md` and the instructions in `CONTEXT.md` for linking progress entries to detailed records as they are created.

**Existing project or Git workspace.** Use this route for every other target, including an initialized project on a repeat visit. Keep the first pass read-only. Inspect existing instructions, research records and scattered notes, program entry points and dependencies, simulator projects, data and manuscript locations, project figures and literature, output conventions, and repository boundaries as needed. Follow relevant links in project and directory documents to locate existing records. Use listings and metadata for large datasets. For Git status, use `git --no-optional-locks -C <target> status --short` to avoid refreshing the index on disk. Keep the inventory and proposed changes in the conversation.

Present the following findings and ask the owner to confirm all three before the first write.

1. **Current programs.** Identify candidate active models and entry points, exploratory code, and historical versions. Cite the evidence and mark unresolved alternatives. Directory numbers and modification times alone cannot establish which model is active.
2. **Research progress.** Summarize what the available sources support, identify open questions, and distinguish implementation, verification, and inclusion in a manuscript. Ask the owner to confirm, correct, or mark the status as unknown.
3. **Reorganization plan.** List proposed creations and edits. Identify records to reuse, consolidate, or move and the documents that would link to them. For each migration, name the source, destination, whether to move or copy, affected links or dependencies, and any Git implications. Flag same-name conflicts for the owner to resolve and preserve the existing files until a resolution is approved. For existing guidance, identify the sections to add or revise. Call out unresolved ownership of data or outputs.

Treat a correction to the inventory as a correction of fact. Apply changes only when the active programs, research status, and actual operations are all confirmed. If the user confirms only part of this, carry that answer forward and ask for the outstanding decision. On the next turn, recheck affected paths before executing the agreed operations. Preserve existing histories, uncommitted work, and owner-authored guidance. If an enclosing repository already tracks a proposed model or exploratory folder, explain that relationship and settle its handling in the plan. A repeat visit that reveals no needed changes ends with a read-only summary.

## Organize figures and references

For an existing project, include any missing root `figures/` and `references/` directories in the reorganization plan.

- Propose moving loose project figures to the root `figures/`. Keep original program-generated figures in the producing program's `output/`. When a figure is selected for a manuscript or presentation, copy it to `figures/` if the owner approves the copy.
- Propose organizing existing local research literature in the root `references/`. Keep bibliographies such as `.bib` files and other path-dependent assets at their current locations by default. If a move would affect a manuscript, program, or document, include the affected links and their updates in the proposal. Apply the approved move and link updates together.

## Organize simulator projects

Include a missing root `simulation/` in the reorganization plan for an existing workspace. Use one subdirectory per simulator in use, such as `simulation/LTspice/`, `simulation/Multisim/`, or `simulation/PSpice/`. Store simulator-specific projects, schematics, netlists, model libraries, and supporting scripts together with their local dependencies. Keep general research programs, including MATLAB and Python numerical simulations and their outputs, under the existing formal and exploratory program directories.

Identify the simulator from project metadata and companion files. Ask the owner about ambiguous assignments before proposing a move. Reuse existing destinations when they fit. Include each project and its dependencies in the approved migration plan, preserve their relative layout, and coordinate any required path updates.

## Write the workspace documents

Use the following three assets as content templates. Localize them while writing them into the research root. For an existing project, adapt the approved sections to its confirmed directories, sources, and research status. In particular, replace the fresh-project `PROG1/` default with the confirmed current directory.

- [AGENTS.md](assets/templates/AGENTS.md) defines the active model and entry point, program promotion, independent model repositories, output ownership, manuscript sources, verification, and cross-chat maintenance rules.
- [CONTEXT.md](assets/templates/CONTEXT.md) summarizes confirmed progress, key decisions, verification status, next steps, and sources by topic. Seed existing research history with owner-confirmed information only.
- [TERMINOLOGY.md](assets/templates/TERMINOLOGY.md) records approved terms, wording, usage, and sources. An empty terminology table is appropriate until the owner confirms entries.

The active formal model gets its own numbered repository. Keep exploratory work in `PROG_temp/` until the owner confirms promotion. On an owner-confirmed model switch, create the next formal repository and record the active model explicitly. Earlier numbered directories then serve as read-only archives. Every producing program writes to its own directory's `output/`, including an exploratory program or a program that reads inputs from an older model. Project-level deliverables prepared outside program runs go into the root `output/`.

## Organize research records

Create a detailed Markdown record when there is substantive material to preserve. Keep it near the work or asset it describes. Use the optional `context/` directory for project-wide or cross-topic matters and the relevant model, figure, or other project directory for local records. Choose the record type, filename, and fields to fit the research. Use the chosen project language for the record and its link text.

Reuse an adequate Markdown record and link to it directly. For CSV, YAML, and program logs, retain the original files and add a Markdown entry point when readers need an explanation or a way to find them. Describe their purpose and link to the original files. Carry over source references when consolidating notes.

Link project-wide progress entries in `CONTEXT.md` to their detailed records with relative paths. For directory-specific records, use the relevant README or another suitable project document. Add links to records that exist and check for existing notes and links on repeat visits. For an existing workspace, apply the approved record changes and the corresponding link updates together.

## Verify and hand off

Check the resulting structure against the approved changes. For each formal repository, compare the resolved path from `git -C <model> rev-parse --show-toplevel` with the model directory itself. Check that `PROG_temp/` has no independent repository and that the applicable output directories exist. Check that `figures/`, `references/`, and `simulation/` exist on fresh setups and where approved for existing projects. Verify that moved or copied assets are in their approved destinations, including simulator projects under the correct software folders. Check that dependent paths still resolve and original program outputs remain in place. Resolve new links from the containing document to verify that they reach the intended records and sources. Confirm the documents use the chosen language and reference the correct active model. Report the actual changes, output locations, and unresolved decisions. Identify any validation that could not be completed.
