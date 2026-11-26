<h1 align="center">初始化科研工作区</h1>

<p align="center">按模型组织科研代码，用你熟悉的语言记录项目决策。</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-97CA00?style=flat" alt="MIT 许可证" /></a>
  <a href="#工作区结构"><img src="https://img.shields.io/badge/Research-Initializer-FE7D37?style=flat" alt="科研项目初始化" /></a>
  <a href="initialize-research-workspace/SKILL.md"><img src="https://img.shields.io/badge/AI%20agent-skill-007EC6?style=flat" alt="AI Agent 技能" /></a>
  <a href="https://sailrain.github.io/"><img src="https://img.shields.io/badge/A%20SailRain-work-00897B?style=flat" alt="SailRain 作品" /></a>
</p>

<p align="center"><a href="README.md">English</a> · <strong>简体中文</strong></p>

<p align="center">
  <a href="#1-初始化或整理项目">1. 初始化或整理项目</a> ·
  <a href="#2-按研究需要调整工作流">2. 按研究需要调整工作流</a> ·
  <a href="#3-卸载-skill-后继续与-agent-协作">3. 卸载 skill 后继续与 Agent 协作</a>
</p>

---

## 1. 初始化或整理项目

1. 确认已安装 Git，然后下载并解压[源码 ZIP](https://github.com/SailRain/initialize-research-workspace-skill/archive/refs/heads/main.zip)。
2. 把解压后内层的 `initialize-research-workspace/` 文件夹复制到 `~/.agents/skills/`。确认 `SKILL.md` 位于 `~/.agents/skills/initialize-research-workspace/SKILL.md`，且同一 skill 目录下有 `assets/templates/`。
3. 在 Codex 中打开科研项目目录，根据项目情况选用下面的提示词。如果 Codex 打开的是其他目录，请补上项目的完整路径。想指定项目文档的语言，可以加一句「请用简体中文写项目文档」。未指定时，skill 默认采用你在对话中使用的语言。

**从空目录开始**

```text
请用 $initialize-research-workspace 初始化这个科研目录，完成后展示实际目录树。
```

独立的空目录默认直接初始化。如果想先看方案，可以加一句「先展示预计目录树，等我确认后再改动」。

**整理已有项目或 Git 工作区**

```text
请用 $initialize-research-workspace 先只读盘点这个项目。
说明哪些程序可能仍在使用，以及现有材料能确认哪些科研进展。
用实际文件名展示预计目录树，标明哪些条目拟新建、移动、复制或原位保留。
等我确认当前程序、科研进展和具体整理操作后，再改动文件。
```

**检查交付结果。** 对照[标准布局](#工作区结构)或你已确认的方案，检查实际目录树。打开 `AGENTS.md` 核对当前正式模型和仍待补充的项目设置，打开 `CONTEXT.md` 核对科研进展，并确认三份项目文档都使用了你选定的语言。

## 2. 按研究需要调整工作流

整理或初始化后，skill 会再做一次只读复查。根据它的建议，先确认下一个任务会用到的信息，例如正式模型的程序入口和共享输入数据的位置。如果你还没有设定日志偏好，skill 会问你想记什么、什么时候记、放在哪里。例如，确定论文用图时，可以把对应的数据和脚本记在 `figures/` 下的说明里。

```text
请先读 AGENTS.md 和 CONTEXT.md，只读复查这个工作区。
结合实际文件，按优先级列出最有用的调整建议，先核对当前正式模型的程序入口和共享输入数据。
请建议在什么时候、什么位置记录论文选用图件的数据和脚本来源。
如果建议整理文件，先展示受影响的目录分支，列出需要更新的依赖或引用。
等我确认后再执行，并把确认后的长期约定写进 AGENTS.md。
```

**检查约定是否落到项目里。** 长期工作约定写进 `AGENTS.md`，已确认的进展和下一步写进 `CONTEXT.md`。有具体内容需要留存时再建详细记录，并从相关项目文档链接过去。批准移动或复制文件后，核对受影响的路径是否仍然有效。

## 3. 卸载 skill 后继续与 Agent 协作

卸载 skill 后，在科研项目根目录开启新的 Agent 对话。先请 Agent 读 `AGENTS.md` 了解当前模型和工作约定，再读 `CONTEXT.md` 接续项目进展、证据和下一步。写论文、报告或演示文稿时，请它查阅 `TERMINOLOGY.md`，沿用已经确认的术语。

当 Agent 在聊天中依据科研记录作答时，会在相关陈述后标出具体条目。例如，你问「上次验证到了哪一步？」，可能会看到下面的回复。

> 上次运行通过了数值验证，当时仍待实验复核。（`context/model-validation.md`，小节「验证状态」）

每次交代任务时，说明你要的结果、任务范围和验收标准。把下面方括号里的内容换成你的实际信息。

```text
请先读 AGENTS.md 和 CONTEXT.md，按当前正式模型的运行约定，用[已有输入]复现[目标结果]。
把本轮工作限定在当前正式模型内，生成的文件放到这个模型的 output/ 下。
用[参考图或参考数值]做对照，按[验收标准]检查结果。
告诉我实际运行了什么、验证了什么、产物放在哪里。
如果有实质性进展，请提出要写入 CONTEXT.md 的具体条目和依据，等我确认后再更新。
```

**检查结果并做好交接。** 打开产物，按标准验收，确认还有哪些验证待完成。审核依据和拟写入 `CONTEXT.md` 的条目，确认它准确反映科研进展后再批准更新。长期工作约定有变化时，更新 `AGENTS.md`，让下一次对话能沿用新约定。

## 工作区结构

下方是新项目的标准布局。仿真软件子目录和 `context/` 按需建立。

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

### 文件放在哪里

| 文件或用途 | 存放位置 |
| --- | --- |
| 探索性的 MATLAB 或 Python 代码 | 先放在 `PROG_temp/`，经你确认后再纳入当前正式模型。`PROG_temp/` 没有独立 Git 仓库。 |
| 新采用的正式模型 | 放在下一个编号的独立仓库，例如 `PROG2/`。较早的模型版本作为只读档案。 |
| 原理图、网表或仿真软件专用脚本 | 按软件放入对应子目录，例如 `simulation/LTspice/`。工程文件和依赖放在一起。 |
| 程序生成的数据、图件或日志 | 放在生成它们的程序所属的 `output/`。以程序文件的位置确定输出路径。例如，从任何工作目录启动 `PROG2/` 下的程序，产物都写到 `PROG2/output/`。 |
| 会议记录、选用的图件和文献 | 项目级交付物放在根目录 `output/`，选用的图件副本放在 `figures/`，文献放在 `references/`。生成的原件留在程序的 `output/`。 |
| 详细科研记录 | 在相关工作附近新建或复用 Markdown 记录，跨主题内容可用 `context/`。从 `CONTEXT.md` 或其他相关项目文档链接过去。 |

整理已有项目时，先确认文件的来源和用途。对已确认的产物，方案中会写明对应模型的 `output/` 和需要修改的引用。获批后同步执行移动和引用更新。输入数据和来源不明的文件保留原位。计划迁移时，核查代码、仿真工程和论文的依赖路径，包括论文引用的文献库文件。

### 生成产物的 Git 忽略规则

用 Git 跟踪模型代码，把生成的产物保存在磁盘上。请在实际管理该模型的仓库根目录下的 `.gitignore` 中设置忽略规则。

| 仓库布局 | 忽略模型的 `output/` | 忽略必须留在 `output/` 外的产物 |
| --- | --- | --- |
| `PROG2/` 是独立仓库 | `/output/` | `/bifur.mat` |
| 项目共用一个仓库 | `/PROG2/output/` | `/PROG2/bifur.mat` |

用精确路径忽略产物，让同类型的输入文件仍可按项目原有规则被跟踪。如果 Git 已经跟踪某个产物，从索引中移除它须经你明确批准。磁盘上的文件和已有提交历史都会保留。

手动分享 skill 时，请一并提供两份 README、`LICENSE` 和完整的 `initialize-research-workspace/` 文件夹。
