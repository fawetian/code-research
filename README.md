# code-research

Code Research 是一个面向源码理解的研究工作流。它帮助你从产品目标、系统边界、架构取舍、核心机制、数据流、演进历史、阅读路径和质量风险几个角度，系统理解一个已有项目。

它不做浅层文件导览，而是把代码库还原成一组可讨论的设计判断：这个系统为什么存在，作者在 Day 0 会如何定义问题和 MVP，当前实现为什么长成这样，后来者应该按什么路径阅读源码。

默认产出中文研究文档，写入目标项目的 `docs/code-research/`。

## 适合场景

- 接手一个陌生项目，需要快速建立全局理解。
- 想从源码作者视角复盘产品需求和技术方案。
- 需要规划一条可执行的源码阅读路径。
- 希望识别核心模块、关键数据流和维护风险。

## 安装

### Codex

个人安装，所有项目可用：

```bash
mkdir -p ~/.agents/skills
git clone git@fawetian.github.com:fawetian/code-research.git ~/.agents/skills/code-research
```

项目安装，只在当前项目可用：

```bash
mkdir -p .agents/skills
git clone git@fawetian.github.com:fawetian/code-research.git .agents/skills/code-research
```

在 Codex 中使用 `code-research` 或 `$code-research` 触发。

### Claude Code

个人安装，所有项目可用：

```bash
mkdir -p ~/.claude/skills
git clone git@fawetian.github.com:fawetian/code-research.git ~/.claude/skills/code-research
```

项目安装，只在当前项目可用：

```bash
mkdir -p .claude/skills
git clone git@fawetian.github.com:fawetian/code-research.git .claude/skills/code-research
```

在 Claude Code 中使用 `/code-research` 触发，也可以让 Claude Code 根据请求自动选择。

## 更新

```bash
git -C ~/.agents/skills/code-research pull --ff-only
git -C ~/.claude/skills/code-research pull --ff-only
```

本仓库是 skill 根目录，不包含 `.codex-plugin/`、`.claude-plugin/` 或 marketplace 配置。
