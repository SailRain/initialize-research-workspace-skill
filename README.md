# Initialize Research Workspace

This Codex skill sets up program repositories, output folders, and research records. It can initialize an empty folder directly. For an existing project, it first inspects the workspace and asks the owner to confirm the current programs, research progress, and proposed changes.

## Share and install

For manual distribution, share `README.md`, `LICENSE`, and the complete `initialize-research-workspace/` folder. After publication, you can also share the GitHub source archive. The recipient can copy the installable folder into their personal Codex skills directory, `~/.agents/skills/`. The resulting entry point should be `~/.agents/skills/initialize-research-workspace/SKILL.md`, with `assets/templates/` alongside it. A personal installation keeps a new research folder empty until initialization. Git must be available to create the formal model repositories.

## Use the skill

Open the target research folder in Codex and enter a request in your usual language. An English request could read as follows.

> Use $initialize-research-workspace to initialize this research project.

If Codex is open elsewhere, include the target folder's path. You can also request a particular document language. The skill uses your requested language or infers it from your messages when it writes `AGENTS.md`, `CONTEXT.md`, and `TERMINOLOGY.md`.

A new project starts with `PROG1/` for the formal model and `PROG_temp/` for experiments. Each program writes into its own directory's `output/`. The root `output/` holds project-level deliverables such as meeting notes. When you run the skill again, it reviews the existing setup and proposes any updates for your approval.
