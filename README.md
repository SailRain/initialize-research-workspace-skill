<h1 align="center">Initialize Research Workspace</h1>

<p align="center">Organize research code by model and keep a record of project decisions in your language.</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-97CA00?style=flat" alt="MIT license" /></a>
  <a href="#workspace-layout"><img src="https://img.shields.io/badge/Research-Initializer-FE7D37?style=flat" alt="Research Initializer" /></a>
  <a href="initialize-research-workspace/SKILL.md"><img src="https://img.shields.io/badge/AI%20agent-skill-007EC6?style=flat" alt="AI agent skill" /></a>
  <a href="https://sailrain.github.io/"><img src="https://img.shields.io/badge/A%20SailRain-work-00897B?style=flat" alt="A SailRain work" /></a>
</p>

<p align="center"><strong>English</strong> · <a href="README.zh-CN.md">简体中文</a></p>

<p align="center">
  <a href="#1-initialize-or-organize">1. Initialize or organize</a> ·
  <a href="#2-tailor-the-workflow">2. Tailor the workflow</a> ·
  <a href="#3-work-with-your-agent-after-uninstalling">3. Work with your agent after uninstalling</a>
</p>

---

## 1. Initialize or organize

1. Make sure Git is installed, then download and extract the [source ZIP](https://github.com/SailRain/initialize-research-workspace-skill/archive/refs/heads/main.zip).
2. Copy the inner `initialize-research-workspace/` folder into `~/.agents/skills/`. Check that `~/.agents/skills/initialize-research-workspace/SKILL.md` exists with `assets/templates/` in the same skill folder.
3. Open your research folder in Codex and choose the prompt below that fits your project. If Codex is open in another folder, include your project's full path. To choose the language of the project documents, add “Write the project documents in English.” Otherwise, the skill uses the language of your messages.

**Starting with an empty folder**

```text
Use $initialize-research-workspace to initialize this research folder.
When you're done, show me the actual directory tree.
```

The skill initializes an empty standalone folder directly. To review the layout first, add “Show me the proposed directory tree and wait for my approval before making any changes.”

**Organizing an existing project or Git workspace**

```text
Use $initialize-research-workspace to review this project in read-only mode.
Identify likely active programs and summarize the progress the files support.
Use actual filenames in the proposed directory tree and label what you would
create, move, copy, or keep in place. Wait for me to confirm the active
programs, research progress, and specific changes before making any edits.
```

**Check the handoff.** Compare the actual layout with the [standard layout](#workspace-layout) or with your approved plan. Open `AGENTS.md` to check the active model and identify any settings that still need your input. Read `CONTEXT.md` to verify the research status, and check that all three project documents are in your chosen language.

## 2. Tailor the workflow

After setup, the skill reviews the project again in read-only mode. Start with its suggestions and confirm the details you need for your next task, such as the active model's entry point and the location of shared input data. If you haven't set logging preferences, the skill asks what you want to record, when, and where. For example, when you select a figure for a paper, you can record the source dataset and script in a note under `figures/`.

```text
Read AGENTS.md and CONTEXT.md, then review this workspace in read-only mode.
Using the actual files, rank the changes that would help most. Start with the
active model's entry point and shared input data. Suggest when and where to
record the source dataset and script for figures selected for the manuscript.
For any proposed reorganization, show the affected branches of the directory
tree and list the dependencies or references that need updating. Wait for
my approval, then apply the agreed changes and save the lasting rules in
AGENTS.md.
```

**Check what was saved.** Put lasting working agreements in `AGENTS.md` and confirmed progress and next steps in `CONTEXT.md`. Create detailed notes when there is something to record, and link to them from the relevant project document. After an approved move or copy, check that affected paths still resolve.

## 3. Work with your agent after uninstalling

After uninstalling the skill, open the project root in a new agent session. Ask the agent to read `AGENTS.md` for the current model and working rules, then `CONTEXT.md` for progress, evidence, and next steps. For a paper, report, or presentation, ask it to check `TERMINOLOGY.md` for approved wording.

When a chat reply draws on a research record, the agent cites the entry it used. For example, you might see the following answer about a past validation run.

> The previous run passed numerical validation. Experimental verification was still pending at the time. (`context/model-validation.md`, “Validation status”)

For each task, name the result you want, the scope of the work, and how you will judge the result. Replace the bracketed details in this example with your own.

```text
Read AGENTS.md and CONTEXT.md. Follow the current formal model's run
instructions to reproduce [result] using [saved input]. Keep this task within
the active model and write the generated files to that model's output/.
Compare the result with [reference figure or value] using [acceptance criterion].
Tell me what you ran, what you verified, and where you saved the files. If
there is substantive progress, propose a CONTEXT.md update with its evidence
and wait for my approval before writing it.
```

**Check the result.** Open the reported output and compare it with your acceptance criterion. Check which validations are still pending. Review the evidence and approve the proposed `CONTEXT.md` entry when it accurately captures the progress. When a lasting rule changes, update `AGENTS.md` so it carries into the next session.

## Workspace layout

The tree shows the standard layout for a new project. Simulator subfolders and `context/` are created as needed.

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

### Where files belong

| If you're working with… | Use |
| --- | --- |
| Exploratory MATLAB or Python code | `PROG_temp/` until you approve promotion into the active formal model. `PROG_temp/` has no independent Git repository. |
| A newly adopted formal model | The next independent numbered repository, such as `PROG2/`. Keep earlier model versions as read-only archives. |
| Schematics, netlists, or tool-specific scripts | A simulator folder such as `simulation/LTspice/`. Keep each simulator project with its dependencies. |
| Generated data, figures, or logs | The producing program's `output/`. Resolve the path relative to the program file so a script in `PROG2/` writes to `PROG2/output/` from any working directory. |
| Meeting notes, selected figures, or literature | Root `output/` for project deliverables, `figures/` for selected copies, and `references/` for literature. Keep generated originals in the program's `output/`. |
| Detailed research notes | Keep or reuse a Markdown note near the relevant work, or use `context/` for cross-topic work. Link to it from `CONTEXT.md` or another relevant project document. |

For existing projects, confirm the source and use of each file before moving it. For confirmed outputs, the proposal names the producing model's `output/` and any references that must change. Apply approved moves and reference updates together. Keep inputs and files of uncertain origin in place. Check code, simulator, and manuscript dependencies when planning moves, including paths to bibliography files.

### Git rules for generated output

Use Git to track model code and keep generated artifacts on disk. Add the ignore rules to `.gitignore` at the root of the repository that manages the model.

| Repository layout | Ignore the model's `output/` | Ignore a generated file that must stay outside `output/` |
| --- | --- | --- |
| Independent `PROG2/` repository | `/output/` | `/bifur.mat` |
| Shared project repository | `/PROG2/output/` | `/PROG2/bifur.mat` |

Use exact paths so input files of the same type remain eligible for tracking under the project's rules. If Git already tracks an output, the agent needs your explicit approval before removing it from the Git index. The file stays on disk, and the commit history is preserved.

To share the skill manually, distribute both README files, `LICENSE`, and the complete `initialize-research-workspace/` folder.
