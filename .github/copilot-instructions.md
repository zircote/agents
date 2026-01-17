# Copilot Instructions

You are working in the Agents plugin repository for Claude Code.

## Project Overview

This is a Claude Code plugin providing 115+ specialized Opus 4.5 agents organized by domain, 54 development skills, and powerful exploration and code review commands.

## Key Components

- **Agents**: 115+ specialized agents in `agents/` organized by domain
- **Skills**: 54 development skills in `skills/`
- **Commands**: Release and workflow commands in `commands/`

## Plugin Structure

```
.claude-plugin/plugin.json  # Plugin manifest
agents/                     # 115+ specialized agents
  01-core-development/
  02-language-specialists/
  03-infrastructure/
  04-quality-security/
  05-data-ai/
  06-developer-experience/
  07-specialized-domains/
  08-business-product/
  09-meta-orchestration/
  10-research-analysis/
  templates/
skills/                     # 54 development skills
commands/                   # Plugin commands
```

## Development Guidelines

1. Follow Claude Code plugin standards
2. Keep changes focused and reviewable
3. Update CHANGELOG.md for user-facing changes
4. Agents must follow Opus 4.5 frontmatter format

## Agent Format

```yaml
---
name: agent-name
description: >
  [Role] specialist for [domain]. Use PROACTIVELY when [trigger conditions].
model: inherit
tools: Read, Write, Bash, Glob, Grep
---

[Detailed instructions]
```

## Skill Format

Skills use SKILL.md files with YAML frontmatter containing `name`, `description`, and optional `triggerPhrases`.
