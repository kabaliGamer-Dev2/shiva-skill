# Shiva-Skill

A single-file global AI personalization prompt for AI coding agents (Claude Code, OpenCode, Codex, and similar). It defines how the assistant reasons, communicates, investigates, debugs, engineers, and verifies work in every conversation.

**Current version:** `S-Skill-v2.md` (v2.0, 2026-10-19)
**Previous version:** `S-Skill.md` (v1), kept for comparison and rollback.

## What v2 changes

- Merges the original personalization with the Strict AI Engineering & Product Intelligence Protocol.
- Resolves three conflicts: retry limits, workflow phases, and evidence labels.
- Removes duplicated sections; v1's §14 and §20 are folded into the new workflow and final gate.
- Adds: precedence order, capability honesty, tool and subagent discipline, plan-mode boundaries, prompt-injection handling, git safety, and resource awareness.
- Removes the external Superpowers dependency. The workflow, debugging method, and completion checks are now self-contained; no skill pack, MCP server, or repository is required.
- Fixes stale references: the deprecated `openai/skills` repository and the Codex skills documentation URL.
- Keeps ADHD communication mode on by default, with an explicit off switch ("normal mode" or "stop ADHD mode").

## v2 sections

| # | Section |
|---|---------|
| 1 | Scope and precedence |
| 2 | Mission and success criteria |
| 3 | Six non-negotiables |
| 4 | Communication contract (ADHD) |
| 5 | Reasoning method |
| 6 | Canonical workflow |
| 7 | Debugging, retries, and stop conditions |
| 8 | Evidence, status, and honesty |
| 9 | Reviews and research |
| 10 | Engineering, security, and failure modes |
| 11 | Tools, skills, memory, resources |
| 12 | Final quality gate |
| 13 | References |

## v1 sections

| # | Section |
|---|---------|
| 1 | Primary directive |
| 2 | Understand the real need |
| 3 | Permanent ADHD communication reference |
| 4 | Reasoning and deep analysis |
| 5 | Accuracy, research, and uncertainty |
| 6 | Depth, length, and information quality |
| 7 | Explanations and examples |
| 8 | Insight, creativity, and challenge |
| 9 | Software engineering workflow: Superpowers (v1 only; removed in v2) |
| 10 | Systematic debugging and root-cause analysis |
| 11 | Fallback engineering and failure-mode analysis |
| 12 | Codex and agent skills |
| 13 | Security, privacy, and safe changes |
| 14 | High-quality engineering and research rules |
| 15 | Personalization and practical constraints |
| 16 | Conversation memory and continuity |
| 17 | Response structure and format |
| 18 | Tone and feedback |
| 19 | Transparency and honesty |
| 20 | Final quality check |

## Usage

1. Copy `S-Skill-v2.md` into your agent's global instructions location, or paste it as a system prompt.
   - Claude Code: `~/.claude/CLAUDE.md`
   - OpenCode: `~/.config/opencode/AGENTS.md`
   - Codex: `~/.codex/AGENTS.md`
2. Start a new conversation. The rules apply automatically; no activation phrase is needed.
3. To disable ADHD formatting, say `normal mode` or `stop ADHD mode`.

Project-specific instructions (`AGENTS.md`, `CLAUDE.md`, `CONTRIBUTING.md`) take precedence over this file for work in that project. Platform and safety instructions take precedence over both.

## Version history

| Version | File | Date | Notes |
|---------|------|------|-------|
| 2.0 | `S-Skill-v2.md` | 2026-10-19 | Merge with Strict Engineering Protocol; deduplicated; references verified |
| 1.0 | `S-Skill.md` | 2026-10-19 | Initial global personalization prompt |

## License

No license specified yet.
