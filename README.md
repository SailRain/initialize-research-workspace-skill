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
| **An empty research folder** | Creates the first model's Git repository, the workspace folders, and three project documents in your language. The handoff shows the actual directory tree. If you ask to see the plan first, the skill previews the layout and waits for your approval. |
| **An existing project** | Reviews the workspace and shows the proposed directory tree in chat. It asks you to confirm the active programs, research progress, and planned changes before writing or moving any files. |

The first proposal shows the main layout using the project's actual names. The tree marks which files or folders the skill would create, move, copy, or keep in place. Follow-up proposals show the affected branches and wait for your approval.

After setup or approved changes, the skill reviews the workspace again in read-only mode. It shares useful follow-up suggestions and asks about logging preferences if you have yet to set them. The project's `AGENTS.md` carries your confirmed working agreements into future tasks.

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
│   ├── .gitignore     Excludes the model's output directory
│   └── output/        Generated results, ignored by Git
├── PROG_temp/         Exploratory programs and experiments
│   └── output/        Results produced by those experiments
├── simulation/        Simulator projects and their required files
│   ├── LTspice/       Example tool folder, created when needed
│   ├── Multisim/      Example tool folder, created when needed
│   └── PSpice/        Example tool folder, created when needed
├── output/            Project deliverables, such as meeting notes
├── figures/           Selected project figures for manuscripts and reports
├── references/        Project literature and supporting references
├── AGENTS.md          Working agreements, active model, and record guidance
├── CONTEXT.md         Progress overview, decisions, and links to detailed records
├── context/           Optional home for project-wide or cross-topic records
└── TERMINOLOGY.md     Approved terms and their usage
```

When you adopt a new model, the skill can set up `PROG2/` with its own Git history and keep `PROG1/` as a read-only archive. A program in `PROG2/` writes to `PROG2/output/` even when it reads data from `PROG1/`.

Each new model repository has a `.gitignore` with `/output/` so Git can track the code while generated figures, files, and data stay local. For an existing project, the skill proposes an ignore rule in the Git repository that manages the model. If Git already tracks output files, the skill identifies them and asks for approval before removing them from the index. The files stay on disk, and their earlier commits remain in the repository.

Use `simulation/` for schematics, netlists, and tool-specific scripts. Create a subfolder for each simulator you use and keep each project with its dependencies. Manage general MATLAB or Python code in the appropriate `PROG*` directory. When reorganizing an existing simulation project, the skill checks its dependencies and proposes moves for your approval.

Keep the current status and next steps in `CONTEXT.md`. The generated `AGENTS.md` explains when to propose a progress update and records any logging preferences you confirm. As the need arises, keep a detailed Markdown record near the work it describes and link it from the relevant project document. For example, a cross-model decision can live in `context/`, and a figure provenance note can live in `figures/`. For an existing project, the skill proposes how to reuse or organize existing records for your approval.

Use `figures/` for selected project figures and `references/` for available project literature. When organizing existing files, the skill proposes destinations and checks manuscript and code references before asking for your approval. Generated originals stay in their program output folders, with selected copies in `figures/` when useful.

To share the skill manually, distribute `README.md`, `LICENSE`, and the complete `initialize-research-workspace/` folder together.
