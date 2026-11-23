---
name: initialize-research-workspace
description: Initialize a new research workspace or organize an existing one, and establish reusable working agreements for future research. Set up model-specific Git repositories, program output locations, and project documents in the user's language, with a read-only review and owner confirmation for existing workspaces.
---

# Initialize a research workspace

Set up or organize the research folder and leave a reusable workflow that the owner and future agents can follow during daily research. Write enduring working agreements in the project's own `AGENTS.md`.

Work in the research folder the user designates. Resolve the templates relative to this skill and project paths relative to the research folder. If the requested target is ambiguous, establish its location before writing.

## Choose the language of the project documents

Honor an explicit request for the language of the generated documents. Otherwise, infer the user's language from their own conversational messages, including their latest clarification. Filenames, code, pasted papers, and these English templates are weak language signals. If the request is mixed or too short to tell and prior messages give no clear answer, ask which language to use. If an existing project has a conflicting document-language rule, resolve it with the owner during the review.

Write all new project-facing prose in that language, including headings, table labels, directory tree annotations, examples, instructions, and placeholders such as “To be confirmed.” Preserve literal filenames, paths, Git commands, code identifiers, and scientific symbols. Use the same language for the inventory, confirmation questions, and handoff unless the user requests a different response language. In an existing file, preserve its author's content and wording outside the approved edits. Translating existing passages requires agreement on that change.

## Inspect the folder and choose a route

Inspect the target's directory entries, including hidden entries. Check whether the target is a Git working tree, contains a repository, or lies within an enclosing Git workspace. A `.git` file can identify a linked worktree. For a working-tree check, use `git -C <target> rev-parse --show-toplevel`. If Git is unavailable or the target cannot be inspected reliably, report the missing information before treating it as empty.

**Empty standalone folder.** Take the direct route when the folder is empty or contains only a regular `.DS_Store` file, and it has no existing Git boundary. If the owner asks to see a plan first, show the proposed directory tree and wait for confirmation before making changes. Otherwise, carry out these steps once the target and language are clear. Preserve the metadata file and include a directory tree of the actual layout in the handoff.

1. Create `PROG1/output/`, `PROG_temp/output/`, and the root `output/`, `figures/`, `references/`, and `simulation/`. Add simulator subdirectories only for software the project uses.
2. Initialize Git inside `PROG1/` with `git -C <target>/PROG1 init`. Add an anchored `/output/` rule to `PROG1/.gitignore`. Leave commits, remote configuration, and publishing to the owner.
3. Write the three root documents from the templates below. Use `PROG1/` as the active formal directory. Use localized placeholders for unknown project facts. Include the recordkeeping guidance in `AGENTS.md` and the instructions in `CONTEXT.md` for linking progress entries to detailed records as they are created.

**Existing project or Git workspace.** Use this route for every other target, including an initialized project on a repeat visit. Keep the first pass read-only. Inspect existing instructions, research records and scattered notes, program entry points and dependencies, simulator projects, data and manuscript locations, project figures and literature, output conventions, and repository boundaries as needed. Follow relevant links in project and directory documents to locate existing records. Use listings and metadata for large datasets. For Git status, use `git --no-optional-locks -C <target> status --short` to avoid refreshing the index on disk. Keep the inventory and proposed changes in the conversation.

Present the following findings and ask the owner to confirm all three before the first write.

1. **Current programs.** Identify candidate active models and entry points, exploratory code, and historical versions. Cite the evidence and mark unresolved alternatives. Directory numbers and modification times alone cannot establish which model is active.
2. **Research progress.** Summarize what the available sources support, identify open questions, and distinguish implementation, verification, and inclusion in a manuscript. Ask the owner to confirm, correct, or mark the status as unknown.
3. **Reorganization plan.** Show the proposed directory tree and list the operations it represents. Identify records to reuse, consolidate, or move and the documents that would link to them. For each migration, name the source, destination, whether to move or copy, affected links or dependencies, and any Git implications. Flag same-name conflicts for the owner to resolve and preserve the existing files until a resolution is approved. For existing guidance, identify the sections to add or revise. Call out unresolved ownership of data or outputs.

Treat a correction to the inventory as a correction of fact. Apply changes only when the active programs, research status, and actual operations are all confirmed. If the user confirms only part of this, carry that answer forward and ask for the outstanding decision. On the next turn, recheck affected paths before executing the agreed operations. Preserve existing histories, uncommitted work, and owner-authored guidance. If an enclosing repository already tracks a proposed model or exploratory folder, explain that relationship and settle its handling in the plan. A repeat visit that reveals no needed changes ends with a read-only summary.

## Preview the proposed layout

Show the expected layout in a plain-text tree in the conversation before asking the owner to approve a plan. Use the actual project root and existing filenames, with the intended names for new entries. Show the main project branches on the first pass and focus on affected branches for follow-up plans. Annotate relevant entries with the planned action, such as `[Create]`, `[Move]`, `[Copy]`, or `[Keep in place]`. Show move and copy targets where they would land. If a placement is unresolved, ask about it alongside the tree before treating it as a proposed operation.

## Organize figures and references

For an existing project, include any missing root `figures/` and `references/` directories in the reorganization plan.

- Propose moving loose project figures to the root `figures/`. Keep original program-generated figures in the producing program's `output/`. When a figure is selected for a manuscript or presentation, copy it to `figures/` if the owner approves the copy.
- Propose organizing existing local research literature in the root `references/`. Keep bibliographies such as `.bib` files and other path-dependent assets at their current locations by default. If a move would affect a manuscript, program, or document, include the affected links and their updates in the proposal. Apply the approved move and link updates together.

## Organize simulator projects

Include a missing root `simulation/` in the reorganization plan for an existing workspace. Use one subdirectory per simulator in use, such as `simulation/LTspice/`, `simulation/Multisim/`, or `simulation/PSpice/`. Store simulator-specific projects, schematics, netlists, model libraries, and supporting scripts together with their local dependencies. Keep general research programs, including MATLAB and Python numerical simulations and their outputs, under the existing formal and exploratory program directories.

Identify the simulator from project metadata and companion files. Ask the owner about ambiguous assignments before proposing a move. Reuse existing destinations when they fit. Include each project and its dependencies in the approved migration plan, preserve their relative layout, and coordinate any required path updates.

## Write the workspace documents

Use the following three assets as content templates. Localize them while writing them into the research root. For an existing project, adapt the approved sections to its confirmed directories, sources, and research status. In particular, replace the fresh-project `PROG1/` default with the confirmed current directory.

- [AGENTS.md](assets/templates/AGENTS.md) defines the active model and entry point, program promotion, independent model repositories, output ownership, manuscript sources, verification, and cross-chat maintenance rules. Carry over the research-task closeout rule so future agents propose recording substantive progress in `CONTEXT.md` during ordinary research work.
- [CONTEXT.md](assets/templates/CONTEXT.md) summarizes confirmed progress, key decisions, verification status, next steps, and sources by topic. Seed existing research history with owner-confirmed information only.
- [TERMINOLOGY.md](assets/templates/TERMINOLOGY.md) records approved terms, wording, usage, and sources. An empty terminology table is appropriate until the owner confirms entries.

The active formal model gets its own numbered repository. Keep exploratory work in `PROG_temp/` until the owner confirms promotion. On an owner-confirmed model switch, create the next formal repository with its own `/output/` ignore rule and record the active model explicitly. Earlier numbered directories then serve as read-only archives.

## Route model outputs and configure Git

Write new model programs so their generated data, figures, and logs go to the producing model's `output/`. Resolve the model directory from the program's location so the destination works from other working directories. For example, `PROG2/bifurcation_diagram.m` should save its generated data to `PROG2/output/bifur.mat`. Apply the same principle to exploratory programs in `PROG_temp/`. Project-level deliverables prepared outside program runs go into the root `output/`.

For loose files in an existing workspace, establish provenance and use during the read-only review. Check the generating program, run records, and consumers, or ask the owner to identify the file. For confirmed generated artifacts, show the proposed destination under the producing model's `output/` in the directory tree. Apply an approved move together with any approved updates to code or documents that read or reference the old path. Keep inputs and files of unknown origin in place.

Keep the anchored `/output/` rule in each independent numbered repository. In a shared root repository, scope the rule to the model, such as `/PROG2/output/`. When a confirmed generated artifact must stay elsewhere for a tool or dependency, add its exact path to the root `.gitignore` of the repository that manages it. For example, use `/bifur.mat` in the independent `PROG2/` repository or `/PROG2/bifur.mat` in the shared root repository. Use literal paths so unrelated files remain eligible for tracking. Avoid extension-wide rules such as `*.mat`, which can also match input data.

In existing projects, check the effective rules and tracked paths before proposing changes. Include the exact ignore entries in the reorganization plan and preserve existing rules. Identify tracked outputs and the Git impact of any move into an ignored path. Adding an ignore rule leaves existing tracked entries in the index. Obtain explicit approval before stopping tracking, and preserve the files on disk and their commit history.

## Organize research records

Create a detailed Markdown record when there is substantive material to preserve. Keep it near the work or asset it describes. Use the optional `context/` directory for project-wide or cross-topic matters and the relevant model, figure, or other project directory for local records. Choose the record type, filename, and fields to fit the research. Use the chosen project language for the record and its link text.

Reuse an adequate Markdown record and link to it directly. For CSV, YAML, and program logs, retain the original files and add a Markdown entry point when readers need an explanation or a way to find them. Describe their purpose and link to the original files. Carry over source references when consolidating notes.

Link project-wide progress entries in `CONTEXT.md` to their detailed records with relative paths. For directory-specific records, use the relevant README or another suitable project document. Add links to records that exist and check for existing notes and links on repeat visits. For an existing workspace, apply the approved record changes and the corresponding link updates together.

## Verify and hand off

Check the resulting structure against the approved changes. For each formal repository, compare the resolved path from `git -C <model> rev-parse --show-toplevel` with the model directory itself. Check that `PROG_temp/` has no independent repository and that the applicable output directories exist. Check that `figures/`, `references/`, and `simulation/` exist on fresh setups and where approved for existing projects. Verify that moved or copied assets are in their approved destinations, including simulator projects under the correct software folders. Check that dependent paths still resolve and original program outputs remain in place. Resolve new links from the containing document to verify that they reach the intended records and sources. Confirm the documents use the chosen language and reference the correct active model. Report the actual changes, output locations, and unresolved decisions. Identify any validation that could not be completed.

Use `git check-ignore --no-index` in the repository that manages the model to verify that its `output/` and any approved exact exceptions match the intended generated paths. Check that the added rules leave source inputs eligible for tracking. Use `git ls-files` to detect outputs that are still tracked. After a migration, check that consumers resolve the approved new paths.

### Review remaining opportunities

After creating the baseline layout or carrying out the approved reorganization, make a focused read-only pass over the resulting workspace. Look for remaining loose files and groups that could be easier to find or reuse. Check program inputs and outputs, project notes, and manuscript references when they can clarify how related files are used. Treat matching names as leads and respect decisions to keep files in place.

Include the most useful follow-up suggestions in the handoff. Name the actual files or groups, why the change would help, and any proposed destination, move or copy, and affected dependencies. When proposing further reorganization, show a tree of the affected branches and ask the owner to select or approve the operations before applying them. Ask focused questions when the active version, origin, or use is unclear. For a new project, offer a project-specific addition only when its known needs suggest one.

In the same handoff, ask what the owner wants to log if their preferences are unknown. Offer examples drawn from the project, such as significant code changes, formal runs, or provenance for selected figures, and let the owner defer the choice. Reuse established preferences and record confirmed choices in the project `AGENTS.md`, including when records are useful and where to keep them. Keep the workspace usable while preferences are pending and create detailed records when there is material to record.
