# Agents Plugin

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Plugin](https://img.shields.io/badge/Claude_Code-Plugin-blueviolet)](https://github.com/anthropics/claude-code)
[![CI](https://github.com/zircote/agents/actions/workflows/ci.yml/badge.svg)](https://github.com/zircote/agents/actions/workflows/ci.yml)
[![Version](https://img.shields.io/badge/version-0.6.0-green.svg)](https://github.com/zircote/agents/releases)

Comprehensive agent library featuring 115+ specialized Opus 4.5 agents organized by domain, 55 development skills, and powerful exploration and code review commands for enhanced Claude Code workflows.

## Installation

```bash
claude plugin install zircote/agents
```

## Verify Installation

After installing, verify the agents and commands are available:

```bash
# Test an agent (should return a helpful response)
claude "Using the python-pro agent, explain Python's GIL in one sentence"

# Verify agent count in Task tool
claude "List 3 available subagent types from the zircote plugin"
```

You should see agents like `python-pro`, `frontend-developer`, `code-reviewer` in the Task tool's available subagents.

## Contents

### Agents (115 total)

Specialized agents organized by domain in `agents/`:

| Category | Count | Directory | Examples |
|----------|-------|-----------|----------|
| Core Development | 11 | `01-core-development/` | frontend-developer, backend-developer, fullstack-developer, api-designer, mobile-developer, ui-designer |
| Language Specialists | 23 | `02-language-specialists/` | python-pro, typescript-pro, golang-pro, rust-engineer, java-architect, react-specialist, nextjs-developer, vue-expert |
| Infrastructure | 12 | `03-infrastructure/` | devops-engineer, sre-engineer, kubernetes-specialist, terraform-engineer, cloud-architect, database-administrator |
| Quality & Security | 12 | `04-quality-security/` | code-reviewer, security-auditor, penetration-tester, test-automator, performance-engineer, debugger, qa-expert |
| Data & AI | 12 | `05-data-ai/` | data-scientist, data-engineer, ml-engineer, llm-architect, postgres-pro, prompt-engineer, nlp-engineer |
| Developer Experience | 10 | `06-developer-experience/` | documentation-engineer, cli-developer, build-engineer, refactoring-specialist, mcp-developer, dx-optimizer |
| Specialized Domains | 11 | `07-specialized-domains/` | fintech-engineer, blockchain-developer, game-developer, iot-engineer, payment-integration |
| Business & Product | 10 | `08-business-product/` | product-manager, technical-writer, ux-researcher, scrum-master |
| Meta Orchestration | 8 | `09-meta-orchestration/` | multi-agent-coordinator, workflow-orchestrator, task-distributor |
| Research & Analysis | 6 | `10-research-analysis/` | research-analyst, competitive-analyst, market-researcher, trend-analyst |
| Templates | 1 | `templates/` | Agent creation templates |

### Skills (55 total)

Development skills in `skills/`:

| Category | Skills |
|----------|--------|
| **AI/Prompting** | anthropic-prompt-engineer, anthropic-architect, claude-code, prompt-engineer |
| **Frontend** | frontend-development, frontend-design, aesthetic, ui-styling, canvas-design, web-artifacts-builder, web-frameworks, artifacts-builder |
| **Backend** | backend-development, databases, devops |
| **Code Quality** | code-review, debugging (5 sub-skills), problem-solving (6 sub-skills) |
| **Tools & Utilities** | mcp-builder, changelog-generator, skill-creator, engineer-skill-creator, template-skill, skill-share, repomix, sequential-thinking |
| **Media** | ai-multimodal, image-enhancer, video-downloader, slack-gif-creator, chrome-devtools, svg-graphics |
| **Business** | brand-guidelines, competitive-ads-extractor, content-research-writer, internal-comms, lead-research-assistant, shopify |
| **Specialized** | better-auth, datadog-entity-generator, invoice-organizer, file-organizer, python-deprecation-fixer, python-project-skel, raffle-winner-picker, theme-factory, webapp-testing |

### Commands

Located in `commands/`:

| Command | Description |
|---------|-------------|
| `/zircote:release` | Prepare and execute a plugin release with version bump, validation, and optional PR creation |

## Agent Format

All agents follow Opus 4.5 best practices:

```yaml
---
name: agent-name
description: >
  [Role] specialist for [domain]. Use PROACTIVELY when [trigger conditions].
  [Key capabilities and integration points].
model: inherit
tools: Read, Write, Bash, Glob, Grep, [additional-tools]
---

[Detailed agent instructions including protocols, execution patterns, and output formats]
```

## Usage

### Via Task Tool (Subagent Delegation)

Agents are invoked via the Task tool with `subagent_type`:

```
Task(subagent_type="frontend-developer", prompt="Build a React component for user authentication")
Task(subagent_type="security-auditor", prompt="Review this codebase for vulnerabilities")
Task(subagent_type="python-pro", prompt="Refactor this module using best practices")
```

### Parallel Execution

Deploy multiple specialists simultaneously for independent tasks:

```
# Parallel: Full-stack feature with security review
Task(subagent_type="frontend-developer", prompt="Build the UI")
Task(subagent_type="backend-developer", prompt="Build the API")
Task(subagent_type="security-auditor", prompt="Review for vulnerabilities")

# Sequential: Research then implement
research = Task(subagent_type="research-analyst", prompt="Research best practices for X")
# Then use findings to guide implementation
Task(subagent_type="python-pro", prompt="Implement based on research: {research}")
```

### CLAUDE.md References

Reference agents in your project's CLAUDE.md for automatic routing:

```markdown
## Agent Preferences

- Use `frontend-developer` for React/TypeScript work
- Use `python-pro` for Python implementation
- Use `code-reviewer` before merging PRs
```

## Templates

Agent templates in `agents/templates/` provide starting points for creating new agents following Opus 4.5 conventions.

## File Structure

```
agents/
├── .claude-plugin/
│   └── plugin.json
├── agents/
│   ├── 01-core-development/
│   ├── 02-language-specialists/
│   ├── 03-infrastructure/
│   ├── 04-quality-security/
│   ├── 05-data-ai/
│   ├── 06-developer-experience/
│   ├── 07-specialized-domains/
│   ├── 08-business-product/
│   ├── 09-meta-orchestration/
│   ├── 10-research-analysis/
│   └── templates/
├── skills/
│   ├── aesthetic/
│   ├── ai-multimodal/
│   ├── anthropic-architect/
│   └── ... (55 total)
├── commands/
│   └── release.md
├── CHANGELOG.md
├── LICENSE
└── README.md
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Attribution

[VoltAgent/awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents)

## License

MIT
