# 科研协作工作流

把已经与 AI 对齐的科研工作方式保存下来，在不同项目和设备上复用。适用于论文复现、自主研究、实验数据处理、仿真和结果分析。

优先让人容易读懂、运行和修改。具体项目的代码、数据、参数和研究进展保留在各自的项目里。

## 文件怎么用

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](skills/research-workflow/SKILL.md) | AI 使用的协作约定，包含论文复现和自主研究两种流程 |
| [项目说明模板](skills/research-workflow/assets/project-readme.md) | 需要新建或补充项目说明时，选用其中适合的内容 |

## 在 Codex 中使用

将整个 `skills/research-workflow` 文件夹放到用户目录下的 `.agents/skills/` 中。Linux/macOS 的用户目录通常是 `~`，Windows 通常是 `C:\Users\你的用户名`。只安装这一份技能文件夹，里面的模板会一起带过去。

在 Linux/macOS 上，如果希望修改仓库后立即使用新版，可以在本仓库根目录执行以下命令建立链接：

```sh
mkdir -p "$HOME/.agents/skills"
ln -s "$PWD/skills/research-workflow" "$HOME/.agents/skills/research-workflow"
```

链接目标若已存在，先查看它指向哪里，避免安装重复副本。

新开一个 Codex 会话，在技能列表中查找 `research-workflow`，或直接在消息中提到它。若没有出现，重启 Codex 后再检查。

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

也可以让 AI 根据任务自动选择这个技能。明确提到技能名称，便于在初次使用时确认它已被读取。

## 跨设备复用

把本仓库复制到另一台设备，或在设置自己的 Git 远端后克隆它，再按上面的方法安装技能。链接指向每台设备各自的仓库位置。

通过链接安装时，更新仓库即可更新技能；通过复制安装时，修改后需要更新安装目录中的副本。技能文件本身不会因登录同一账号自动同步。

这个技能以文字约定为主，没有额外运行依赖。具体实验仍需要准备项目自己的数据和运行环境。若使用 `maniplot`，在对应设备上准备该技能及其绘图库；缺少它时可先沿用项目已有的绘图方案。

技能在被调用时提供这些约定。如果希望简洁、可读的表达习惯适用于所有 Codex 任务，可把自己认可的几条偏好加入全局 `AGENTS.md`；科研流程继续由本技能维护。

## 怎样逐步改进

遇到需要再次纠正 AI 的地方，先判断它是通用习惯，还是当前项目的特殊要求。稳定的通用习惯写入 `SKILL.md`；项目假设、参数和进展更新到项目自己的说明里。一次尝试和待定建议应保留其状态。

第一次使用可以选择一个小任务：复现论文中的一张图，或分析自己的一组实验数据。看它是否减少了重复询问、能否找到结果对应的数据和脚本，以及交付内容是否容易理解和修改。技能格式检查不能替代这样的实际试用。

## 参考

- [Good enough practices in scientific computing](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510)：适合科研工作逐步采用的基本做法。
- [Cookiecutter Data Science](https://cookiecutter-data-science.drivendata.org/opinions/)：数据流、重复分析和按需简化项目结构。
- [Google 代码审查指南](https://google.github.io/eng-practices/review/reviewer/looking-for.html#complexity)：控制复杂度，避免为未知需求过度设计。
- [Agent Skills 编写建议](https://agentskills.io/skill-creation/best-practices)：明确适用范围，用简短步骤和具体示例传达方法。
- [Codex 技能说明](https://learn.chatgpt.com/docs/build-skills)：技能安装位置和调用方式。
