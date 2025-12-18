# Changelog

All notable changes to the Pine Script Development Assistant will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [2.0.0] - 2025-12-18

### Changed
- **BREAKING**: Migrated from `.claude/agents/` to `.claude/skills/` system
- Skills now auto-activate based on user request context (no explicit Task tool calls needed)
- Updated `CLAUDE.md` to document the skills system
- Updated `user-prompt-submit.sh` hook to use skills terminology
- Hooks now provide informational feedback only (skills auto-invoke)

### Added
- New skills directory structure at `.claude/skills/`
- 7 skill configurations with `SKILL.md` files:
  - `pine-developer` - Writes production Pine Script v6 code
  - `pine-visualizer` - Breaks down trading ideas into components
  - `pine-debugger` - Adds debugging tools and troubleshooting
  - `pine-backtester` - Implements backtesting and performance metrics
  - `pine-optimizer` - Optimizes performance and user experience
  - `pine-publisher` - Prepares scripts for TradingView publication
  - `pine-manager` - Orchestrates complex multi-step projects
- Skills include detailed `description` fields for automatic discovery
- `status` command now lists available skills
- `help` command shows skills documentation
- This `CHANGELOG.md` file

### Removed
- **`.claude/agents/` directory** - Fully replaced by `.claude/skills/`
- Dependency on explicit Task tool invocation for agent selection
- References to "subagents" in documentation

### Migration Notes
- The `.claude/agents/` directory has been removed (fully replaced by skills)
- Skills use the same content as the previous agents, reformatted for SKILL.md
- No changes needed for end users - skills activate automatically

## [1.0.0] - 2025-12-01

### Added
- Initial release with 7 specialized Pine Script agents
- Agent-based architecture using `.claude/agents/` directory
- Claude Code hooks for deterministic agent routing
- Pine Script v6 documentation
- Template library for indicators, strategies, and utilities
- YouTube video analysis capability
- File protection system (lock/unlock commands)
- Interactive `start` command
- Example scripts

### Features
- pine-visualizer: Trading idea decomposition
- pine-developer: Pine Script v6 code generation
- pine-debugger: Debugging tools and troubleshooting
- pine-backtester: Performance metrics and testing
- pine-optimizer: Performance and UX optimization
- pine-manager: Multi-agent workflow orchestration
- pine-publisher: TradingView publication preparation

---

## Version History Summary

| Version | Date | Highlights |
|---------|------|------------|
| 2.0.0 | 2025-12-18 | Migrated to Claude Code Skills system |
| 1.0.0 | 2025-12-01 | Initial release with agent architecture |

## Upgrade Guide

### From 1.x to 2.0

**For End Users**: No action required. Skills activate automatically based on your requests.

**For Developers**:
1. Skills are now in `.claude/skills/skill-name/SKILL.md` format
2. The `description` field in SKILL.md frontmatter drives automatic discovery
3. `allowed-tools` is optional and restricts (rather than grants) tool access
4. Hooks provide informational feedback only - they don't control skill activation

**Key Differences**:

| Aspect | v1.x (Agents) | v2.0 (Skills) |
|--------|--------------|---------------|
| Location | `.claude/agents/name.md` | `.claude/skills/name/SKILL.md` |
| Invocation | Explicit Task tool | Auto-invoked by Claude |
| Discovery | Manual reference | Automatic at startup |
| Tool access | `tools:` grants | `allowed-tools:` restricts |
