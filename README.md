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
| **An empty research folder** | Creates a Git repository for the first model, folders for experiments, simulations, figures, and references, and three project documents in your language. |
| **An existing project** | Reviews the code, simulation projects, research notes, figures, and references, then asks you to confirm the active programs, research progress, and proposed changes before writing or moving any files. Running the skill again follows the same review process. |

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
├── simulation/        Simulator projects and their required files
│   ├── LTspice/       Example tool folder, created when needed
│   ├── Multisim/      Example tool folder, created when needed
│   └── PSpice/        Example tool folder, created when needed
├── output/            Project deliverables, such as meeting notes
├── figures/           Selected project figures for manuscripts and reports
├── references/        Project literature and supporting references
├── AGENTS.md          Working agreements and the active model
├── CONTEXT.md         Progress overview, decisions, and links to detailed notes
├── context/           Optional topic notes, created when needed and approved
│   └── algorithm-refinement.md
└── TERMINOLOGY.md     Approved terms and their usage
```

When you adopt a new model, the skill can set up `PROG2/` with its own Git history and keep `PROG1/` as a read-only archive. A program in `PROG2/` writes to `PROG2/output/` even when it reads data from `PROG1/`.

Use `simulation/` for schematics, netlists, and tool-specific scripts. Create a subfolder for each simulator you use and keep each project with its dependencies. Manage general MATLAB or Python code in the appropriate `PROG*` directory. When reorganizing an existing simulation project, the skill checks its dependencies and proposes moves for your approval.

Keep the current status and next steps in `CONTEXT.md`. For a substantial topic such as an algorithm refinement, link from the overview to its detailed note in `context/` after you approve the split.

Use `figures/` for selected project figures and `references/` for available project literature. When organizing existing files, the skill proposes destinations and checks manuscript and code references before asking for your approval. Generated originals stay in their program output folders, with selected copies in `figures/` when useful.

To share the skill manually, distribute `README.md`, `LICENSE`, and the complete `initialize-research-workspace/` folder together.
