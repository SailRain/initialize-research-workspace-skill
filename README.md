<h1 align="center">Initialize Research Workspace</h1>

<p align="center">Organize research code by model and keep a record of project decisions in your language.</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-97CA00?style=flat" alt="MIT license" /></a>
  <a href="#workspace-layout"><img src="https://img.shields.io/badge/Research-Initializer-FE7D37?style=flat" alt="Research Initializer" /></a>
  <a href="initialize-research-workspace/SKILL.md"><img src="https://img.shields.io/badge/AI%20agent-skill-007EC6?style=flat" alt="AI agent skill" /></a>
  <a href="https://sailrain.github.io/"><img src="https://img.shields.io/badge/A%20SailRain-work-00897B?style=flat" alt="A SailRain work" /></a>
</p>

---

## How it works

| Your starting point | What Codex does |
| --- | --- |
| **An empty research folder** | Creates a Git repository for the first model, a folder for experiments, and three project documents in your language. |
| **An existing project** | Reads the code and research notes, then asks you to confirm the active programs, research progress, and proposed changes before it edits any files. Running the skill again follows the same review process. |

## Quick start

1. Download and extract the [source ZIP](https://github.com/SailRain/initialize-research-workspace-skill/archive/refs/heads/main.zip). Git must be installed to create the model repositories.
2. Copy the inner `initialize-research-workspace/` folder into `~/.agents/skills/`. You should now have `~/.agents/skills/initialize-research-workspace/SKILL.md` with `assets/templates/` beside it.
3. Open your research folder in Codex and enter the following request in your usual language.

```text
Use $initialize-research-workspace to initialize this research project.
```

If Codex is open in another folder, include the project path in your request. You can also specify a language for the project documents. Otherwise, the skill uses the language of your messages.

## Workspace layout

```text
research-project/
├── PROG1/             First formal model, with its own Git repository
│   └── output/        Results produced by this model's programs
├── PROG_temp/         Exploratory programs and experiments
│   └── output/        Results produced by those experiments
├── output/            Project deliverables, such as meeting notes
├── AGENTS.md          Working agreements and the active model
├── CONTEXT.md         Research progress, decisions, and sources
└── TERMINOLOGY.md     Approved terms and their usage
```

When you adopt a new model, the skill can set up `PROG2/` with its own Git history and keep `PROG1/` as a read-only archive. A program in `PROG2/` writes to `PROG2/output/` even when it reads data from `PROG1/`.

To share the skill manually, distribute `README.md`, `LICENSE`, and the complete `initialize-research-workspace/` folder together.
