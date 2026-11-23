<h1 align="center">初始化科研工作区</h1>

<p align="center">按模型组织科研代码，用你熟悉的语言记录项目决策。</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-97CA00?style=flat" alt="MIT 许可证" /></a>
  <a href="#工作区结构"><img src="https://img.shields.io/badge/Research-Initializer-FE7D37?style=flat" alt="科研项目初始化" /></a>
  <a href="initialize-research-workspace/SKILL.md"><img src="https://img.shields.io/badge/AI%20agent-skill-007EC6?style=flat" alt="AI Agent 技能" /></a>
  <a href="https://sailrain.github.io/"><img src="https://img.shields.io/badge/A%20SailRain-work-00897B?style=flat" alt="SailRain 作品" /></a>
</p>

<p align="center"><a href="README.md">English</a> · <strong>简体中文</strong></p>

---

## 工作方式

| 初始状态 | Codex 会怎么做 |
| --- | --- |
| **空的科研目录** | 为第一个模型建立独立的 Git 仓库，创建工作区目录，并用你的语言编写三份项目文档。初始化完成后展示实际目录树。如果你要求先看方案，skill 会预览目录结构，等你确认后再执行。 |
| **已有科研项目** | 检查工作区，在对话中展示整理后的预计目录树。写入或移动文件前，会请你确认当前使用的程序、科研进展和计划改动。 |

首次提交整理方案时，会用项目中的实际文件名展示主要目录结构，标明哪些条目拟新建、移动、复制或原位保留。后续整理方案只展示受影响的目录分支，经你确认后再执行。

初始化或获批改动完成后，skill 会再次只读检查工作区，提出进一步整理建议。如果你还没确定想记录哪些日志，也会在这时一并询问。你确认的工作约定会写入项目的 `AGENTS.md`，供后续任务使用。

## 快速开始

1. 下载并解压[源码 ZIP](https://github.com/SailRain/initialize-research-workspace-skill/archive/refs/heads/main.zip)。创建模型仓库需要安装 Git。
2. 将解压后内层的 `initialize-research-workspace/` 文件夹复制到 `~/.agents/skills/`。复制后，`SKILL.md` 应位于 `~/.agents/skills/initialize-research-workspace/SKILL.md`，同一 skill 目录下应有 `assets/templates/`。
3. 在 Codex 中打开科研项目目录，用你习惯的语言发出请求。

```text
请用 $initialize-research-workspace 初始化这个科研项目。
```

如果 Codex 当前打开的是其他目录，请在请求中注明科研项目的路径。你也可以指定项目文档的语言。skill 默认采用你在对话中使用的语言。

## 工作区结构

```text
research-project/
├── PROG1/             首个正式模型，拥有独立 Git 仓库
│   ├── .gitignore     忽略此模型的输出目录
│   └── output/        生成的产物，由 Git 忽略
├── PROG_temp/         探索性程序和实验
│   └── output/        探索性程序和实验的产物
├── simulation/        仿真工程及其依赖文件
│   ├── LTspice/       软件子目录示例，按需创建
│   ├── Multisim/      软件子目录示例，按需创建
│   └── PSpice/        软件子目录示例，按需创建
├── output/            会议记录等项目级交付物
├── figures/           论文或汇报选用的图件
├── references/        文献及其他参考资料
├── AGENTS.md          工作约定、当前模型和记录规则
├── CONTEXT.md         进展概览、决策和详细记录链接
├── context/           可选目录，用于项目级或跨主题记录
└── TERMINOLOGY.md     已确认的术语及其用法
```

采用新模型时，skill 可以建立有独立 Git 历史的 `PROG2/`，并把 `PROG1/` 保留为只读档案。`PROG2/` 下的新程序根据程序文件自身的位置确定输出路径，从其他工作目录启动时也会把结果写入 `PROG2/output/`。

整理已有项目时，skill 会只读核对疑似产物的来源和用途。确认是生成产物后，建议将其移入对应模型的 `output/`，并列出需要更新的引用。获批的移动和引用更新会一起执行。输入数据和来源不明的文件保留原位。

每个新建的模型仓库都会在 `.gitignore` 中加入 `/output/`，让 Git 跟踪代码，生成的图片、文件和数据则保存在本地。如果已确认的产物必须留在其他位置，skill 会在管理该文件的 Git 仓库中提出按精确路径忽略。例如，`PROG2/` 是独立仓库时用 `/bifur.mat`，项目共用一个仓库时用 `/PROG2/bifur.mat`。精确路径规则保留项目已有的 `.mat` 输入数据跟踪规则。若产物已被 Git 跟踪，从索引中移除它须经明确批准。磁盘上的文件和已有提交历史都会保留。

将原理图、网表和仿真软件专用脚本放入 `simulation/`。按实际使用的软件建立子目录，并将工程文件和依赖放在一起。通用 MATLAB 或 Python 代码放在相应的 `PROG*` 目录。整理已有仿真工程时，skill 会检查依赖，并把拟移动的文件列出来请你确认。

在 `CONTEXT.md` 中维护当前进度和下一步。生成的 `AGENTS.md` 说明何时主动提议更新进度，并记录你确认的日志偏好。需要详细记录时，在相关工作所在的目录附近建立 Markdown，并从合适的项目文档链接过去。例如，跨模型的决策可以放在 `context/`，图件来源记录可以放在 `figures/`。整理已有项目时，skill 会提出如何复用或整理现有记录，经你确认后再执行。

`figures/` 用于收纳选用的图件，`references/` 用于存放项目可用的文献。在整理已有文件时，skill 会提出存放位置，检查论文和代码有哪些引用，再请你确认。程序直接生成的原件保存在对应的输出目录，按需将选用的版本复制到 `figures/`。

手动分享 skill 时，请一并提供 `README.md`、`LICENSE` 和完整的 `initialize-research-workspace/` 文件夹。需要中文说明时，也可附上 `README.zh-CN.md`。
