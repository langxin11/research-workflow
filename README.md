# 科研协作工作流

保存与 AI 约定好的科研工作方法，在新项目、新会话和不同设备上继续使用。适用于论文复现、自主研究、数据处理、仿真和结果分析。

代码和文档应容易读懂、运行和修改。具体项目的数据、代码、参数和进展保留在各自的项目中。

## 文件怎么用

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](skills/research-workflow/SKILL.md) | AI 协作约定，包含论文复现与自主研究的工作流程 |
| [机器人仿真与控制约定](skills/research-workflow/references/robotics-dynamics-control.md) | 机器人动力学仿真与控制的专项约定，按 `SKILL.md` 条件加载 |
| [项目说明模板](skills/research-workflow/assets/project-readme.md) | 新建或补充项目说明时参考，按需选用相关内容 |

## 安装与使用

将整个 `skills/research-workflow` 文件夹复制到用户目录下的 `.agents/skills/`，模板与参考文档会一起带过去。Windows 对应路径通常是 `C:\Users\你的用户名\.agents\skills\`。

Linux/macOS 也可以在仓库根目录执行以下命令，通过链接使用仓库中的技能：

```sh
mkdir -p "$HOME/.agents/skills"
ln -s "$PWD/skills/research-workflow" "$HOME/.agents/skills/research-workflow"
```

目标路径若已存在，先查看原有内容，避免重复安装。

新开 Codex 会话，在技能列表中查找 `research-workflow`。若未出现，重启后再检查。AI 可以根据任务自动选择技能，也可以像下面这样明确调用。

复现论文时：

```text
$research-workflow
先阅读这个项目的 README、论文和作者代码，接着复现论文中的轨迹跟踪实验。
请区分论文已给出的设置、需要补充的假设，以及我们自己的修改。
```

处理自己的实验时：

```text
$research-workflow
分析 data/ 中这组接触力实验，比较两种控制方法，并生成一张对比图。
沿用已有绘图风格，说明指标和误差带的含义。
```

只修改局部内容时：

```text
$research-workflow
调整这张图的字号和图例，保留当前数据处理方式。
```

## 跨设备复用

把本仓库复制到新设备，或设置自己的 Git 远端后克隆它，再按上面的方法安装。

- 通过链接安装：更新本机仓库即可更新技能；移动仓库后，需要重新建立链接。
- 通过复制安装：修改后需要更新安装目录中的副本。

本地技能文件不会随账号自动同步。本技能没有额外运行依赖，具体实验仍需准备自己的环境和数据。使用 `maniplot` 时，也要在对应设备准备该技能和绘图库。

若希望简洁表达等偏好适用于所有 Codex 任务，可将认可的几条偏好写入全局 `AGENTS.md`；科研流程继续由本技能维护。

## 怎样逐步改进

纠正 AI 后，稳定的通用习惯写入 `SKILL.md`，项目设置、参数和进展写入项目自己的说明。临时尝试和待定假设保留其状态。

先用一个小任务试用，例如复现论文中的一张图或分析一组数据。观察它是否减少重复沟通，结果是否容易理解、找到和修改。格式检查不能替代实际试用。

## 参考

- [Good enough practices in scientific computing](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510)：适合科研工作逐步采用的基本做法。
- [Cookiecutter Data Science](https://cookiecutter-data-science.drivendata.org/opinions/)：数据流、重复分析和按需简化项目结构。
- [Google 代码审查指南](https://google.github.io/eng-practices/review/reviewer/looking-for.html#complexity)：控制复杂度，避免为未知需求过度设计。
- [Agent Skills 编写建议](https://agentskills.io/skill-creation/best-practices)：明确适用范围，用简短步骤和具体示例传达方法。
- [Codex 技能说明](https://learn.chatgpt.com/docs/build-skills)：技能安装位置和调用方式。
