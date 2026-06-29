# code-research

Code Research 是一个面向源码理解的研究工作流。它帮助你从产品目标、系统边界、架构取舍、核心机制、数据流、演进历史、阅读路径和质量风险几个角度，系统理解一个已有项目。

它不做浅层文件导览，而是把代码库还原成一组可讨论的设计判断：这个系统为什么存在，作者在 Day 0 会如何定义问题和 MVP，当前实现为什么长成这样，后来者应该按什么路径阅读源码。

默认产出中文研究文档，写入目标项目的 `docs/code-research/`。

## 适合场景

- 接手一个陌生项目，需要快速建立全局理解。
- 准备参与贡献代码，需要知道从哪里读、哪里改、哪里风险高。
- 想从源码作者视角复盘产品需求、MVP 边界和技术方案。
- 需要规划一条可执行的源码阅读路径。
- 希望识别核心模块、关键数据流和维护风险。
- 想基于 commit history 理解系统为什么演进成现在这样。

不适合：单个函数解释、直接修 bug、写新功能技术方案、逐行 code review、安全漏洞扫描或性能 profiling。

## 安装

### Codex

推荐通过 Codex plugin marketplace 安装：

```bash
codex plugin marketplace add fawetian/code-research
codex plugin add code-research@code-research
```

如果你使用 SSH：

```bash
codex plugin marketplace add git@github.com:fawetian/code-research.git
codex plugin add code-research@code-research
```

也可以直接安装为个人 skill，所有项目可用：

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/fawetian/code-research.git ~/.agents/skills/code-research
```

或安装为项目 skill，只在当前项目可用：

```bash
mkdir -p .agents/skills
git clone https://github.com/fawetian/code-research.git .agents/skills/code-research
```

### Claude Code

推荐通过 Claude Code plugin marketplace 安装：

```text
/plugin marketplace add fawetian/code-research
/plugin install code-research@code-research
```

如果你使用 SSH：

```text
/plugin marketplace add git@github.com:fawetian/code-research.git
/plugin install code-research@code-research
```

也可以直接安装为个人 skill，所有项目可用：

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/fawetian/code-research.git ~/.claude/skills/code-research
```

或安装为项目 skill，只在当前项目可用：

```bash
mkdir -p .claude/skills
git clone https://github.com/fawetian/code-research.git .claude/skills/code-research
```

## 使用

在 Codex 中可以输入：

```text
$code-research 深入研究这个项目
```

在 Claude Code 中可以输入：

```text
/code-research 深入研究这个项目
```

也可以在请求里直接写 `code-research`，让 agent 根据 skill 描述自动选择。

## 使用示例

快速了解项目整体架构：

```text
code-research 给我一个大致的理解
```

深入理解某个特定功能：

```text
code-research 我想理解认证模块的实现
```

准备参与贡献代码：

```text
code-research 我想为这个项目贡献代码
```

规划源码阅读路径：

```text
code-research 分析这个项目的代码目录和结构，规划一条源码阅读路径
```

按背景补齐理解项目所需基础知识：

```text
code-research 我是后端工程师，前端基础比较薄弱，深入理解这个项目需要补哪些基础知识模块
```

分析系统为什么演进成现在这样：

```text
code-research 分析这个项目的演进路线和原因
```

从 0 重新思考系统设计：

```text
code-research 如果从第一性原理出发，怎么设计这套系统
```

站在源码作者 Day 0 视角理解产品和技术方案：

```text
code-research 站在源码作者 Day 0 视角，分析这套系统的需求、MVP 边界和技术方案
```

分析代码质量和可维护性风险：

```text
code-research 分析这个项目的代码质量，给我一份质量地图
```

## 研究产物

完整研究结果会保存在目标项目的 `docs/code-research/` 目录下：

| 文件 | 内容 |
| --- | --- |
| `RESEARCH_PLAN.md` | 研究计划、范围、执行状态和最终索引 |
| `01_architecture.md` | 架构概览、核心模块关系和 Mermaid 图 |
| `02_mechanism_[名称].md` | 核心机制拆解、关键调用链和设计原因 |
| `03_data_flow.md` | 数据流、状态流转、输入输出和持久化路径 |
| `04_dependencies.md` | 依赖关系、生态位置、外部系统和关键库作用 |
| `05_workflow.md` | 端到端业务流程和模块内部执行流程 |
| `06_learning_path.md` | 目录结构分析、源码阅读路径、入口文件、前置知识模块和可暂时跳过的目录 |
| `07_evolution_history.md` | 基于 commit history 的系统演进路线和原因 |
| `08_implementation_map.md` | 历史能力、当前模块和代码落点之间的映射 |
| `09_design_evolution.md` | 从第一性原理推演系统为什么逐步长成现在这样 |
| `10_day0_product_technical_design.md` | Day 0 产品需求、MVP 边界、初始技术方案和作者视角设计取舍 |
| `11_quality_map.md` | 基于源码证据的代码质量、维护风险、测试缺口和可简化点 |

如果你只研究某个专题，结果会写到 `docs/code-research/{topic}/`，避免覆盖已有全局研究。

## 重复调用

如果目标项目已经存在 `docs/code-research/`，Code Research 会先检测已有产物，再让你选择：

- 完整覆盖：删除旧文件，重新研究。
- 继续未完成：只补齐缺失专题。
- 归档后重来：把旧结果移动到 `_archived_日期/`，再重新开始。
- 研究新专题：在 `docs/code-research/{topic}/` 下做专项研究。

## 更新

Codex marketplace 安装更新：

```bash
codex plugin marketplace upgrade code-research
codex plugin remove code-research@code-research
codex plugin add code-research@code-research
```

Claude Code marketplace 安装更新：

```text
/plugin marketplace update code-research
/plugin update code-research
```

直接安装为个人 skill 时：

```bash
git -C ~/.agents/skills/code-research pull --ff-only
git -C ~/.claude/skills/code-research pull --ff-only
```

直接安装为项目 skill 时：

```bash
git -C .agents/skills/code-research pull --ff-only
git -C .claude/skills/code-research pull --ff-only
```

如果更新后没有立即出现，重启 Codex 或 Claude Code。

## 仓库结构

```text
code-research/
├── .agents/
│   └── plugins/
│       └── marketplace.json
├── .claude-plugin/
│   └── marketplace.json
├── SKILL.md
├── evals/
│   └── evals.json
├── plugins/
│   └── code-research/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── .codex-plugin/
│       │   └── plugin.json
│       └── skills/
│           └── code-research/
└── templates/
```

本仓库同时支持两种安装形态：根目录是直接安装用的 skill；`plugins/code-research/` 是 marketplace 安装用的最小插件包装，里面只分发这一个 skill。
