# code-research

独立发布的 Code Research skill，用于在 Codex / Claude Code 中对当前项目做深度源码研究，并产出中文分析文档。

这个仓库本身就是 skill 根目录，不包含 `.codex-plugin/`、`.claude-plugin/` 或 marketplace 配置。

## 内容

- `SKILL.md`：skill 入口文件。
- `templates/`：研究报告模板。
- `agents/openai.yaml`：Codex UI 元数据。
- `evals/evals.json`：触发行为测试用例。

## 使用

将本仓库作为一个 skill 安装或放置到 Codex / Claude Code 的 skills 目录后，在对话中使用 `code-research` 或 `$code-research` 触发。

默认输出目录为目标项目内的 `docs/code-research/`。
