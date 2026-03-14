# BNB Skill Creator

A Claude Code skill that helps beginners create skills and submit them to [BNB Chain Skills Hub](https://github.com/bnb-chain/skills-hub) — from idea to merged pull request with minimal friction.

一个 Claude Code 技能，帮助新手创建技能并提交到 [BNB Chain Skills Hub](https://github.com/bnb-chain/skills-hub) —— 从想法到合并 PR，全程低门槛引导。

---

## What It Does / 功能介绍

This skill acts as a concierge for non-technical contributors. It handles the entire workflow:

本技能为非技术用户提供一站式引导，覆盖完整流程：

1. **Create the skill** — Turn your idea into a well-structured `SKILL.md`.
   **创建技能** —— 将你的想法转化为规范的 `SKILL.md` 文件。

2. **Publish to GitHub** — Set up a public repository with the skill files.
   **发布到 GitHub** —— 建立一个包含技能文件的公开仓库。

3. **Submit to Skills Hub** — Draft the metadata JSON and open a pull request to `bnb-chain/skills-hub`.
   **提交到 Skills Hub** —— 生成 metadata JSON 并向 `bnb-chain/skills-hub` 发起 PR。

## When to Use / 使用场景

- You want to create a new skill for BNB Chain Skills Hub.
  你想为 BNB Chain Skills Hub 创建一个新技能。
- You need to prepare a `<skillname>-metadata.json` file.
  你需要准备一份 `<skillname>-metadata.json` 文件。
- You need help with GitHub basics: repos, forks, branches, commits, or pull requests.
  你需要 GitHub 基础操作的帮助：仓库、Fork、分支、提交或 PR。
- You are not technical and want step-by-step guidance.
  你不是技术人员，需要逐步指导。

## How It Works / 工作流程

```
Idea → SKILL.md → Public GitHub Repo → Metadata JSON → PR to skills-hub
想法 → SKILL.md → 公开 GitHub 仓库 → Metadata JSON → 向 skills-hub 发起 PR
```

### Step-by-step / 分步说明

1. **Assess your starting point** — The skill figures out where you are (no GitHub account, no repo, have a repo, etc.) and adapts.
   **评估起点** —— 技能会判断你的当前状态（无 GitHub 账号、无仓库、已有仓库等）并自动适配。

2. **Draft SKILL.md** — Generates a single-file skill with proper YAML frontmatter, trigger description, and workflow steps.
   **生成 SKILL.md** —— 创建包含 YAML 头信息、触发描述和工作流步骤的单文件技能。

3. **Set up the repository** — Guides you through creating a public GitHub repo (web UI or terminal).
   **建立仓库** —— 引导你创建公开的 GitHub 仓库（支持网页操作或命令行）。

4. **Generate metadata** — Creates a valid `<skill-id>-metadata.json` for `skills-hub`.
   **生成元数据** —— 创建符合 `skills-hub` 要求的 `<skill-id>-metadata.json`。

5. **Submit the PR** — Walks you through forking `skills-hub`, adding the metadata file, and opening a pull request.
   **提交 PR** —— 指导你 Fork `skills-hub`，添加元数据文件，并发起 Pull Request。

## Installation / 安装

Copy `SKILL.md` into your Claude Code skills directory:

将 `SKILL.md` 复制到你的 Claude Code 技能目录中：

```bash
# Clone this repo / 克隆本仓库
git clone https://github.com/ternencescott/bnbskillcreator.git

# Copy the skill file to your Claude Code skills folder
# 将技能文件复制到 Claude Code 技能目录
cp bnbskillcreator/SKILL.md ~/.claude/skills/bnbskillcreator/SKILL.md
```

Or install directly via Claude Code:

或直接通过 Claude Code 安装：

```
/install-skill https://github.com/ternencescott/bnbskillcreator
```

## Metadata Format / 元数据格式

The metadata file submitted to `skills-hub` follows this format:

提交到 `skills-hub` 的元数据文件格式如下：

```json
{
  "name": "My Skill Name",
  "github_url": "https://github.com/owner/repo",
  "category": ["category1", "category2"],
  "description": "What the skill does and when to use it."
}
```

GitHub Actions will automatically enrich the metadata after submission — no need to add extra fields manually.

GitHub Actions 会在提交后自动补充元数据 —— 无需手动添加额外字段。

## License / 许可证

MIT
