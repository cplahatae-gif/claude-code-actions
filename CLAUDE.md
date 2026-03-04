# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A **workshop template** for running Claude Code as a serverless scheduler via GitHub Actions. No build system, no application code — it's a collection of GitHub Actions workflow YAML files, Claude Code agents/skills definitions, and documentation. Users fork this repo, add their `CLAUDE_CODE_OAUTH_TOKEN` or `ANTHROPIC_API_KEY` as a repo secret, and run workflows from the Actions tab.

## Repository Layout

```
.github/workflows/          # Active GitHub Actions workflows
  step1-hello-claude.yml    # Workshop steps (progressive difficulty)
  step2-scheduled.yml
  step3-with-mcp.yml
  step4-full-pipeline.yml
  daily-research-digest.yml # Production automations
  repo-health-dashboard.yml
  newsletter-draft.yml
  learning-content.yml
  meeting-actions.yml
  genai-class-weekly.yml

templates/                  # Starter templates users copy from
  workflow-minimal.yml      # Simplest: manual dispatch only
  workflow-scheduled.yml    # Adds cron + git commit/push
  workflow-with-mcp.yml     # Adds MCP servers (Chrome, fetch)
  workflow-full.yml         # Full reference: all triggers + MCP + Skills
  agent-template.md         # .claude/agents/ boilerplate
  skill-template/           # .claude/skills/ boilerplate with assets/references/scripts dirs
  mcp-configs/              # Reusable MCP JSON configs (basic, with-chrome, with-filesystem)

examples/                   # Self-contained use-case examples (each has its own .claude/ and .github/)
  01-daily-news-digest/
  02-repo-health-checker/
  03-learning-content-generator/

docs/                       # Workshop documentation (00-05 + troubleshooting + cost guide)
output/                     # Generated content landing zone (gitkeep only)
.claude/agents/             # Repo-level agents (workshop-helper)
```

## Key Patterns

### Two Authentication Methods
Workflows use either `claude_code_oauth_token` (Claude Max subscription) or `anthropic_api_key` (API billing). The step1-4 workshop flows use OAuth; the full template uses API key. Never mix both in the same workflow step.

### Two Ways to Run Claude Code in Actions
1. **`anthropics/claude-code-action@v1`** — GitHub Action that handles setup automatically. Used in step1-4 and most production workflows. Key inputs: `prompt`, `prompt_file`, `claude_args`, `allowed_tools`, `model`, `max_turns`.
2. **Direct CLI** (`npm install -g @anthropic-ai/claude-code && claude -p`) — Used in example/01 (news-digest). More control but requires manual Node.js and MCP setup.

### MCP Server Configuration
MCP configs are written to `/tmp/mcp-config.json` at runtime and passed via `claude_args: "--mcp-config /tmp/mcp-config.json"`. Three common servers:
- `sequential-thinking` — Extended reasoning
- `fetch` — HTTP content retrieval
- `chrome-devtools` — Headless browser automation (requires Chrome setup step)

### Permission Approaches
- `--dangerously-skip-permissions` — Used in simple workshop steps (OAuth workflows)
- `allowed_tools: "Bash,Read,Write,Edit,Glob,Grep,mcp__*"` — Explicit allowlist (preferred for production)

### Git Commit Pattern in Workflows
Workflows that persist output follow this pattern: configure git identity → run Claude → `git add output/` → commit → push. The git config step must come before the Claude Code step if Claude is instructed to commit within its prompt.

## Editing Workflows

When modifying workflow YAML files:
- `permissions` block must match what Claude needs: `contents: write` for git push, `issues: write` for issue comments, `pull-requests: write` for PR comments, `id-token: write` for OAuth.
- Workshop step workflows (step1-4) trigger on `workflow_dispatch` and optionally `issue_comment`/`schedule`. The `if` condition filters `@claude` mentions.
- Cron times are UTC. KST = UTC + 9 (e.g., `"0 22 * * *"` UTC = KST 07:00 next day).
- `direct_prompt` and `direct_prompt_file` are **deprecated** in `claude-code-action@v1`. Use `prompt` and `prompt_file` instead.

## Agents and Skills

Agents go in `.claude/agents/<name>.md` with YAML frontmatter (`name`, `description`, `tools`, `model`). Skills go in `.claude/skills/<name>/SKILL.md` with supporting `assets/`, `references/`, `scripts/` subdirectories. See `templates/agent-template.md` and `templates/skill-template/SKILL.md` for the canonical structures.

## Language Convention

Documentation and prompts are bilingual Korean/English. Workflow comments and code are in English. Generated content (output/) is primarily Korean with English technical terms preserved.
