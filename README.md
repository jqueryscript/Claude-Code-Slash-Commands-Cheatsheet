# Claude Code Slash Commands Cheatsheet

> A concise reference for current Claude Code commands: public slash commands, MCP command patterns, internal/leaked commands, community commands, and core CLI flags.

[![Status](https://img.shields.io/badge/status-updated-brightgreen)](#)
[![Commands](https://img.shields.io/badge/commands-70%2B-blue)](#)
[![Updated](https://img.shields.io/badge/updated-May%2030%202026-orange)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Table of Contents

- [What This Covers](#what-this-covers)
- [Public Slash Commands](#public-slash-commands)
  - [Session and Context](#session-and-context)
  - [Setup and Config](#setup-and-config)
  - [Coding and Review](#coding-and-review)
  - [Integrations and Remote](#integrations-and-remote)
- [MCP Commands](#mcp-commands)
- [Internal or Leak-Based Commands](#internal-or-leak-based-commands)
- [Community Commands](#community-commands)
- [CLI Commands and Flags](#cli-commands-and-flags)
- [Real Workflows](#real-workflows)
- [Notes](#notes)

---

## What This Covers

This README focuses on commands people are actually likely to search for or use.

- **Public commands**: visible in normal Claude Code builds
- **MCP commands**: generated from connected MCP servers
- **Internal/leaked commands**: found in source-based references, not guaranteed in public builds
- **Community commands**: custom team or repo commands, not built in
- **Built-in skill commands**: public commands such as `/claude-api`, `/less-permission-prompts`, and `/reload-skills`

Removed commands such as `/vim` and `/tag` are listed in notes instead of the main tables.

---

## Public Slash Commands

### Session and Context

| Command | Purpose |
|---|---|
| `/branch [name]` | Branch or fork the current conversation/workflow |
| `/clear` | Clear the current conversation context |
| `/compact [focus]` | Compact context with optional focus instructions |
| `/context` | Show context usage breakdown, model-aware skill token estimates, and plugin-sourced skill names |
| `/copy [N]` | Copy the latest or selected response |
| `/cost` | Shortcut to the cost tab inside `/usage` |
| `/diff` | Open the diff viewer; its detail view supports keyboard scrolling |
| `/export [filename]` | Export the conversation |
| `/rename [name]` | Rename the current session |
| `/resume [session]` | Resume a previous session, including background sessions |
| `/rewind` | Rewind to an earlier checkpoint |
| `/goal` | Set a completion condition and keep Claude working across turns until it is met |
| `/status` | Show current session status |
| `/exit` | Exit Claude Code |

### Setup and Config

| Command | Purpose |
|---|---|
| `/add-dir <path>` | Add another directory to the working scope |
| `/agents` | Manage subagents; use `claude agents` for the new agent view |
| `/color [color]` | Change session accent color; syncs to Remote Control when connected |
| `/config` | Open settings, including the workflow keyword trigger setting |
| `/doctor` | Run environment diagnostics; also warns about MCP servers defined in multiple config scopes with different endpoints |
| `/effort [low\|medium\|high\|xhigh\|max\|auto]` | Set reasoning effort; no-arg `/effort` opens an interactive slider. Opus 4.8 uses `xhigh` for hard tasks |
| `/fast [on\|off]` | Toggle fast mode for supported Opus models. The old `CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE` path is deprecated and scheduled for removal on June 1, 2026 |
| `/help` | Show help and available commands |
| `/less-permission-prompts` | Scan transcripts for common read-only Bash and MCP calls and propose an allowlist for `.claude/settings.json` |
| `/hooks` | Manage hooks; `SessionStart` can reload skills or set the session title, and `MessageDisplay` can transform displayed assistant text |
| `/init` | Generate `CLAUDE.md` |
| `/keybindings` | Edit keybindings |
| `/login` | Sign in |
| `/logout` | Sign out; no longer gets sent to a background session |
| `/mcp` | Manage MCP servers; Reconnect picks up `.mcp.json` edits without restart |
| `/memory` | Open memory files |
| `/model [model]` | Switch models. The picker saves the selection as the default for new sessions; press `s` to switch only the current session. Gateway discovery is opt-in via `CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1` |
| `/output-style [style]` | Change response style |
| `/permissions` | Manage permission rules |
| `/plugin` | Plugin details show component inventory, hook event names, MCP server names, LSP servers, and projected per-session token cost. Plugins in `.claude/skills` directories now load automatically |
| `/reload-plugins` | Reload plugins; also works from Remote Control clients |
| `/reload-skills` | Re-scan skill directories without restarting Claude Code |
| `/sandbox` | Open sandbox controls |
| `/skills` | List available skills |
| `/team-onboarding` | Generate a teammate ramp-up guide from local Claude Code usage |
| `/terminal-setup` | Configure terminal integration; can disable GPU acceleration in VS Code, Cursor, and Windsurf integrated terminals to prevent garbled text |
| `/theme` | Change or create themes; supports custom JSON themes and plugin-shipped themes |
| `/scroll-speed` | Tune mouse wheel scroll speed with live preview |
| `/tui` | Switches the terminal UI mode. Run `/tui fullscreen` to enable flicker-free fullscreen rendering without leaving the current conversation. |

Skills and slash commands can set `disallowed-tools` in frontmatter to remove tools while the workflow is active.

### Coding and Review

| Command | Purpose |
|---|---|
| `/batch` | Apply one change across many files |
| `/btw <question>` | Ask a side question with minimal context |
| `/claude-api` | Load Claude API / SDK helper workflow |
| `/debug [desc]` | Run a debugging workflow |
| `/feedback` | Send feedback |
| `/focus` | Toggle Focus view |
| `/insights` | Show usage/session insights |
| `/loop [interval]` | Run a recurring workflow |
| `/plan [desc]` | Enter plan mode |
| `/powerup` | Open interactive lessons |
| `/pr-comments [PR]` | Fetch PR review comments |
| `/release-notes` | View release notes |
| `/review` | Review current code changes |
| `/security-review` | Run a security-focused review |
| `/simplify` | Run a cleanup-only review and apply simplification, reuse, efficiency, and structure fixes |
| `/code-review [effort]` | Review for correctness issues; add `--fix` to apply findings to the working tree or `--comment` to post inline PR comments |
| `/stats` | Shortcut to the stats tab inside `/usage` |
| `/ultrareview [PR#]` | Run a comprehensive cloud code review with parallel multi-agent analysis and critique |
| `/usage` | Show limits usage by category, including skills, subagents, plugins, MCP servers, and large session files |
| `/usage-credits` | Open usage credits information; replaces `/extra-usage`, which remains an alias |
| `/workflows` | View dynamic workflow runs |

### Integrations and Remote

| Command | Purpose |
|---|---|
| `/chrome` | Open Chrome integration |
| `/desktop` | Hand off to the desktop app |
| `/ide` | Open or manage IDE integration |
| `/install-github-app` | Set up GitHub app integration |
| `/rc` | Start Remote Control |
| `/remote-control` | Full Remote Control command |
| `/remote-env` | Configure remote environments |
| `/schedule` | Manage scheduled tasks |
| `/teleport` | Bridge or transfer sessions |
| `/voice` | Enable push-to-talk voice mode |

---

## MCP Commands

MCP commands are generated dynamically from connected servers.

Pattern:

```text
/mcp__[server]__[prompt] [args]
```

Examples:

```text
/mcp__github__list_prs
/mcp__github__create_pr
/mcp__jira__create_issue
/mcp__linear__get_sprint
```

Use `/mcp` to connect servers and inspect the commands they expose.

`/mcp` Reconnect picks up `.mcp.json` edits without restarting Claude Code.

---

## Internal or Leak-Based Commands

These command names appear in source-based references. They are useful for research, but not guaranteed in standard public builds.

| Command | Likely role |
|---|---|
| `/advisor` | Architecture or design advice |
| `/ant-trace` | Internal tracing |
| `/autofix-pr` | Auto-fix PR issues |
| `/backfill-sessions` | Backfill session data |
| `/brief` | Brief output mode |
| `/bridge` | IDE/bridge session manager |
| `/bridge-kick` | Force-restart bridge connection |
| `/bughunter` | Bug-finding workflow |
| `/buddy` | Temporary easter egg |
| `/commit-push-pr` | Commit, push, and create PR |
| `/ctx_viz` | Debug context visualization |
| `/debug-tool-call` | Debug a tool call |
| `/env` | Environment inspection |
| `/files` | List files in current context |
| `/good-claude` | Easter egg command |
| `/heapdump` | Dump heap for memory analysis |
| `/init-verifiers` | Set up verifier hooks |
| `/install` | Install/update flow |
| `/issue` | File a GitHub issue |
| `/mobile` | Mobile integration/handoff |
| `/mock-limits` | Mock rate limits |
| `/oauth-refresh` | Refresh OAuth tokens |
| `/onboarding` | First-run onboarding |
| `/passes` | Multi-pass workflow |
| `/perf-issue` | Report performance issue |
| `/pr_comments` | Internal form of `/pr-comments` |
| `/privacy-settings` | Privacy settings |
| `/rate-limit-options` | Rate-limit options |
| `/remote-setup` | Remote setup flow |
| `/reset-limits` | Reset rate limits |
| `/sandbox-toggle` | Internal sandbox toggle |
| `/session` | Session management UI |
| `/share` | Share a session |
| `/statusline` | Customize status line |
| `/summary` | Generate a session summary |
| `/tasks` | Manage background tasks |
| `/terminalSetup` | Internal form of `/terminal-setup` |
| `/thinkback` | Replay/analyze thinking |
| `/thinkback-play` | Animated thinking replay |
| `/ultraplan` | Detailed planning workflow |
| `/ultrareview [PR#]` | Run a comprehensive cloud code review with parallel multi-agent analysis and critique |
| `/upgrade` | Upgrade flow |
| `/version` | Show version |
| `/x402` | x402 integration |

---

## Community Commands

These are common custom commands from blogs, repos, or team setups. They are **not built in** unless defined in `.claude/commands/`, skills, or plugins.

| Command | Typical use |
|---|---|
| `/commit` | Generate a commit message and commit changes |
| `/fix-pipeline` | Repair failing CI pipelines |
| `/lint` | Run linting commands |
| `/merge-to-main` | Merge-to-main workflow |
| `/pr` | Create a pull request |
| `/push` | Push the current branch |
| `/vitest` | Run Vitest-based test workflows |

---

## CLI Commands and Flags

### Core CLI Commands

| Command | Purpose |
|---|---|
| `claude` | Start interactive Claude Code |
| `claude agents` | Open agent view: running, blocked, and completed Claude Code sessions |
| `claude agents --json` | List live Claude Code sessions as JSON for scripts and status displays |
| `claude agents` then `! <command>` | Start a shell command as a background session you can attach to or detach from |
| `claude "prompt"` | Start with an initial prompt |
| `claude -p "prompt"` | Run a non-interactive single prompt |
| `claude --bg --exec '<command>'` | Run a shell command as a background Claude session |
| `claude -c` | Continue the last conversation |
| `claude -r "name"` | Resume a named session |
| `claude update` | Update Claude Code |
| `claude mcp list` | List MCP servers |
| `claude mcp serve` | Run Claude Code as an MCP server |
| `claude plugin init <name>` | Scaffold a new plugin in `.claude/skills` |
| `claude plugin details <name>` | Show plugin components and projected per-session token cost |
| `claude plugin tag` | Create release git tags for plugins with version validation |
| `claude plugin marketplace remove <name> --scope user\|project\|local` | Remove a marketplace from a selected configuration scope |

### Important Flags

| Flag | Purpose |
|---|---|
| `--add-dir` | Add an extra directory to scope |
| `--settings` | Loads settings for dispatched background sessions |
| `--mcp-config` | Uses a specific MCP config for dispatched background sessions |
| `--plugin-dir` | Uses a plugin directory for dispatched background sessions |
| `--agent` | Select an agent |
| `--allowedTools` | Pre-approve tools |
| `--bare` | Minimal headless mode |
| `--channels` | Enable channel/MCP push relay |
| `--chrome` | Enable Chrome integration mode |
| `--console` | Use Anthropic Console auth |
| `--dangerously-skip-permissions` | Skip permission prompts |
| `--effort` | Set reasoning effort |
| `--fallback-model` | Continue the session with a configured fallback when the primary model is unavailable |
| `--exclude-dynamic-system-prompt-sections` | Improve print-mode cross-user prompt caching |
| `--json-schema` | Request structured output |
| `--max-budget-usd` | Cap spend |
| `--max-turns` | Limit turns |
| `--model` | Set the model |
| `-n`, `--name` | Name the session |
| `--output-format` | Set machine-readable output |
| `--permission-mode` | Set permission behavior |
| `-r` | Resume a session |
| `--remote` | Start a remote/web-backed session |
| `--remote-control-session-name-prefix` | Prefix Remote Control session names |
| `--transport http\|stdio\|sse` | Select MCP transport |
| `--verbose` | Enable verbose output |
| `-w`, `--worktree` | Use a git worktree |
| `--plugin-url <url>` | Fetch a plugin `.zip` archive from a URL for the current session |

### Useful Environment Variables

| Variable | What it does |
| --- | --- |
| `CLAUDE_CODE_CERT_STORE=bundled` | Uses bundled CAs only instead of the OS certificate store. |
| `CLAUDE_CODE_ENABLE_AUTO_MODE=1` | Enables Auto mode on Bedrock, Vertex, and Foundry for supported Opus 4.7 and Opus 4.8 setups. |
| `CLAUDE_CODE_ENABLE_FEEDBACK_SURVEY_FOR_OTEL` | Re-enables the session quality survey for enterprises capturing responses through OpenTelemetry |
| `CLAUDE_CODE_PERFORCE_MODE=1` | Makes Edit/Write/NotebookEdit fail on read-only Perforce files with a p4 edit hint. |
| `CLAUDE_CODE_SCRIPT_CAPS` | Limits per-session script invocations. |
| `CLAUDE_CODE_USE_MANTLE=1` | Enables Amazon Bedrock powered by Mantle. |
| `DISABLE_UPDATES` | Completely blocks all update paths, including manual `claude update`. Stricter than `DISABLE_AUTOUPDATER`. |
| `CLAUDE_CODE_SESSION_ID` | Session ID. |
| `CLAUDE_CODE_USE_POWERSHELL_TOOL` | Opts into or out of the PowerShell tool rollout. On Linux and macOS, set it to `1` to enable the PowerShell tool when `pwsh` is available. |
| `CLAUDE_CODE_FORCE_SYNC_OUTPUT=1` | Forces synchronized output on terminals where auto-detection misses it, such as Emacs eat. |
| `CLAUDE_CODE_DISABLE_ALTERNATE_SCREEN=1` | Opts out of the fullscreen alternate-screen renderer and keep the conversation in the terminal's native scrollback |
| `CLAUDE_CODE_PACKAGE_MANAGER_AUTO_UPDATE` | Lets Homebrew or WinGet installations run package-manager upgrades in the background, then prompt for restart. |
| `CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1` | Enables gateway `/v1/models` discovery for the `/model` picker. This is now opt-in. |
| `OTEL_LOG_TOOL_DETAILS=1` | Adds tool parameters such as Bash commands and MCP or skill names to tool decision telemetry events. |

---

## Real Workflows

### Start a New Repository

```text
/init
/status
/model
```

### Onboard a New Teammate

```text
/team-onboarding
/init
/memory
```

### Understand an Unfamiliar Codebase

```text
/status
/context
/plan map the project structure and main entry points
```

### Work Toward a Clear Goal

```text
/goal fix the failing checkout test and stop after tests pass
/context
/review
```

### Review a Pull Request

```text
/review
/security-review
/pr-comments
/diff
```

### Prepare a Safe Refactor

```text
/review
/plan refactor the auth flow without changing behavior
/diff
```

### Manage a Long Session

```text
/context
/compact keep decisions only
/cost
```

### Run a Multi-File Refactor

```text
/review
/code-review --fix
/batch rename OldThing NewThing
```

### Fix a Bug in Stages

```text
/debug trace the failing checkout flow
/review
/diff
```

### Work With PR Feedback

```text
/pr-comments 123
/review
/diff
```

### Set Up MCP and Use It Immediately

```text
/mcp
/mcp__github__list_prs
/mcp__jira__create_issue
```

### Work Across Devices

```text
/remote-control
/remote-env
/teleport
```

### Switch to Focused Fullscreen Work

```text
/tui fullscreen
/focus
/context
```

### Check Usage and Limits

```text
/usage
/cost
/stats
```

### View Dynamic Workflows

```text
/workflows
/context
/usage
```

### Inspect Plugin Cost and Components

```text
claude plugin details plugin-name
/plugin
/context
```

### Run a Headless One-Off Task

```text
claude -p "review this diff and list risks"
```

### Run a Deep Cloud Review

```text
/review
/ultrareview
/pr-comments
```

### Reduce Repetitive Permission Prompts

```text
/less-permission-prompts
/permissions
/hooks
```

---

## Notes

- `/vim` was removed in `v2.1.92`. Use `/config` for editor mode settings.
- `/tag` was removed in `v2.1.92`.
- Internal/leaked commands are listed for completeness, not as guaranteed public commands.
- Community commands are custom workflows, not built-in Claude Code commands.
- As of `v2.1.118`, `/cost` and `/stats` are merged into `/usage`; both still work as shortcuts.
- `/simplify` now runs a cleanup-only review and applies simplification, reuse, efficiency, and structure fixes. Use `/code-review --fix` when you want bug-hunting fixes.
- `/extra-usage` was renamed `/usage-credits`; the old command remains an alias.
- `/vim` as a slash command was removed earlier, but Vim mode supports visual modes through editor settings and `/` in NORMAL mode opens reverse history search.
- Remote Control, `/schedule`, Claude.ai MCP connectors, and notification preferences are disabled when `ANTHROPIC_API_KEY`, `apiKeyHelper`, or `ANTHROPIC_AUTH_TOKEN` is set.

---

## Sources

- Claude Code changelogs through `v2.1.158`
- Local command reference notes and leak-based command lists

---

## Related Resources

- [awesome-claude-code](https://github.com/jqueryscript/awesome-claude-code) — curated tools, workflows, integrations, and resources for Claude Code users
- [Anthropic Agent SDK Slash Commands Docs](https://platform.claude.com/docs/en/agent-sdk/slash-commands) — official slash command documentation
- [Claude Code Commands Cheat Sheet (Full Article)](https://www.scriptbyai.com/claude-code-commands-cheat-sheet/) — expanded version with explanations and workflows
- [Best Agent Skills](https://www.scriptbyai.com/best-agent-skills/) — useful skills for Claude Code and other AI coding workflows
- [AI Coding Agents](https://www.scriptbyai.com/best-cli-ai-coding-agents/) — comparison of Claude Code and other CLI coding agents

*Last audited: May 30, 2026*
