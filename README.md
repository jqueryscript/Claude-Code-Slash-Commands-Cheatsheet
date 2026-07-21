# Claude Code Commands Cheatsheet

> Slash commands, MCP commands, CLI commands, flags, environment variables, and workflows. Last audited: July 21, 2026.

[![Status](https://img.shields.io/badge/status-updated-brightgreen)](#)
[![Commands](https://img.shields.io/badge/commands-70%2B-blue)](#)
[![Updated](https://img.shields.io/badge/updated-June%2026%202026-orange)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Table of Contents

- [Slash Commands by Task](#slash-commands-by-task)
  - [Start and Configure Claude Code](#start-and-configure-claude-code)
  - [Manage Context and Sessions](#manage-context-and-sessions)
  - [Review, Debug, and Change Code](#review-debug-and-change-code)
  - [Use GitHub, PR, and Release Workflows](#use-github-pr-and-release-workflows)
  - [Use MCP, Plugins, Skills, and Agents](#use-mcp-plugins-skills-and-agents)
  - [Work Remotely or Across Devices](#work-remotely-or-across-devices)
  - [Check Usage, Costs, Diagnostics, and UI State](#check-usage-costs-diagnostics-and-ui-state)
- [A-Z Slash Command Index](#a-z-slash-command-index)
- [MCP Commands](#mcp-commands)
- [CLI Commands and Flags](#cli-commands-and-flags)
- [Environment Variables](#environment-variables)
- [Real Workflows](#real-workflows)
- [Internal, Experimental, Removed, and Community Commands](#internal-experimental-removed-and-community-commands)
- [Notes](#notes)
- [Sources](#sources)
- [Related Resources](#related-resources)

## Slash Commands by Task

### Start and Configure Claude Code

| Command | Purpose | Status |
|---|---|---|
| `/add-dir <path>` | Add another directory to the working scope | Public |
| `/config` | Open settings, including editor mode and ultracode keyword trigger settings; `/config key=value` sets a setting from the prompt | Public |
| `/doctor` | Run environment diagnostics and show recent update status | Public |
| `/effort [low\|medium\|high\|xhigh\|max\|auto]` | Set reasoning effort; no-arg `/effort` opens an interactive slider and confirms when the level becomes the default for new sessions | Public |
| `/fast [on\|off]` | Toggle fast mode for supported Opus models | Public |
| `/help` | Show help and available commands | Public |
| `/hooks` | Manage hooks; `SessionStart` and `MessageDisplay` support newer workflows | Public |
| `/init` | Generate `CLAUDE.md` | Public |
| `/keybindings` | Edit keybindings | Public |
| `/login` | Sign in | Public |
| `/logout` | Sign out | Public |
| `/memory` | Open memory files | Public |
| `/model [model]` | Switch models; the picker saves the default for new sessions, and `s` switches only the current session | Public |
| `/output-style [style]` | Change response style | Public |
| `/permissions` | Manage permission rules and review recent auto-mode denial reasons | Public |
| `/sandbox` | Open sandbox controls; newer builds can block credential reads and remember approved network hosts for the session | Public |
| `/team-onboarding` | Generate a teammate ramp-up guide from local Claude Code usage | Public |
| `/terminal-setup` | Configure terminal integration and fix terminal rendering issues | Public |
| `/theme` | Change or create themes, including custom JSON and plugin-shipped themes | Public |
| `/scroll-speed` | Tune mouse wheel scroll speed with live preview | Public |
| `/tui` | Switch terminal UI mode; `/tui fullscreen` enables fullscreen rendering | Public |
| `Vim mode` | Editor mode available through `/config`; `/vim` was removed | Setting, not current slash command |

### Manage Context and Sessions

| Command | Purpose | Status |
|---|---|---|
| `/branch [name]` | Branch or fork the current conversation or workflow | Public; `/fork` appears as an alias in some references |
| `/cd <path>` | Move the current session to a new working directory without breaking the prompt cache | Public |
| `/clear` | Clear the current conversation context | Public |
| `/compact [focus]` | Compact context with optional focus instructions | Public |
| `/context` | Show context usage breakdown, skill token estimates, and plugin-sourced skill names | Public |
| `/copy [N]` | Copy the latest or selected response | Public |
| `/export [filename]` | Export the conversation | Public |
| `/goal` | Set a completion condition and keep Claude working across turns until it is met | Public |
| `/rename [name]` | Rename the current session | Public |
| `/resume [session]` | Resume a previous session, including background sessions | Public |
| `/rewind` | Rewind to an earlier checkpoint, including checkpoints before `/clear`; `/undo` appears as an alias | Public |
| `/session` | Open session management UI | Leak-based |
| `/share` | Share a session | Leak-based |
| `/status` | Show current session status | Public |
| `/summary` | Generate a session summary | Leak-based |
| `/exit` | Exit Claude Code | Public |

### Review, Debug, and Change Code

| Command | Purpose | Status |
|---|---|---|
| `/advisor` | Architecture or design advice workflow | Leak-based |
| `/batch` | Apply one change across many files or worktrees | Public / workflow command |
| `/brief` | Brief output mode | Leak-based |
| `/btw <question>` | Ask a side question with minimal context; use arrow navigation for earlier answers and press `c` to copy raw Markdown | Public |
| `/bughunter` | Bug-finding workflow | Leak-based |
| `/code-review [effort]` | Review for correctness issues; add `--fix` or `--comment` | Public |
| `/debug [desc]` | Run a debugging workflow | Public |
| `/diff` | Open the diff viewer; detail view supports keyboard scrolling | Public |
| `/feedback` | Send feedback | Public |
| `/files` | List files in current context | Leak-based |
| `/focus` | Toggle Focus view | Public |
| `/insights` | Show usage/session insights | Public |
| `/loop [interval]` | Run a recurring workflow; `/proactive` appears as an alias | Public / workflow command |
| `/passes` | Run a multi-pass workflow | Leak-based |
| `/plan [desc]` | Enter plan mode | Public |
| `/powerup` | Open interactive lessons | Public |
| `/pr-comments [PR]` | Fetch PR review comments | Public |
| `/pr_comments` | Internal underscore form of `/pr-comments` | Internal |
| `/rate-limit-options` | Open rate-limit options | Leak-based |
| `/release-notes` | View release notes | Public |
| `/review` | Review current code changes; PR review mode now uses the same engine as `/code-review medium` | Public |
| `/security-review` | Run a security-focused review | Public |
| `/simplify` | Run a cleanup-only review and apply simplification, reuse, efficiency, and structure fixes | Public |
| `/tasks` | Manage background tasks | Leak-based |
| `/ultraplan` | Run a detailed planning workflow | Leak-based |
| `/ultrareview [PR#]` | Run a comprehensive cloud code review with parallel multi-agent analysis and critique | Public / workflow command |
| `/workflows` | View dynamic workflow runs | Public |

### Use GitHub, PR, and Release Workflows

| Command | Purpose | Status |
|---|---|---|
| `/commit` | Generate a commit message and commit changes | Community |
| `/commit-push-pr` | Commit, push, and create a PR | Leak-based / community |
| `/fix-pipeline` | Repair failing CI pipelines | Community |
| `/install-github-app` | Set up GitHub app integration; GitHub Actions workflow setup is optional | Public |
| `/issue` | File a GitHub issue | Leak-based |
| `/lint` | Run linting commands | Community |
| `/merge-to-main` | Merge to main | Community |
| `/pr` | Create a pull request | Community |
| `/push` | Push the current branch | Community |
| `/vitest` | Run Vitest-based test workflows | Community |

### Use MCP, Plugins, Skills, and Agents

| Command | Purpose | Status |
|---|---|---|
| `/agents` | Manage subagents; `claude agents` opens the agent view | Public |
| `/bridge` | Manage IDE or bridge sessions | Leak-based |
| `/bridge-kick` | Force-restart a bridge connection | Leak-based |
| `/claude-api` | Load Claude API / SDK helper workflow | Built-in skill command |
| `/less-permission-prompts` | Scan transcripts for safe read-only Bash and MCP allowlist candidates | Built-in skill command |
| `/mcp` | Manage MCP servers, authentication, and dynamic MCP commands | Public |
| `/mcp__[server]__[prompt] [args]` | Run a dynamic MCP prompt command | Generated by connected MCP servers |
| `/plugin` | Manage plugins, inspect plugin components, and follow marketplace renames automatically | Public |
| `/plugin list` | List installed plugins; supports `--enabled` and `--disabled` filters | Public |
| `/reload-plugins` | Reload plugins; also works from Remote Control clients | Public |
| `/reload-skills` | Re-scan skill directories without restarting Claude Code | Public |
| `/skills` | List available skills | Public |

Skills and slash commands can set `disallowed-tools` in frontmatter to remove tools while that workflow is active.

### Work Remotely or Across Devices

| Command | Purpose | Status |
|---|---|---|
| `/chrome` | Open Chrome integration | Public, availability varies |
| `/desktop` | Hand off to the desktop app | Public |
| `/ide` | Open or manage IDE integration, including Devin Desktop where available | Public |
| `/mobile` | Mobile integration or handoff | Leak-based |
| `/oauth-refresh` | Refresh OAuth tokens | Leak-based |
| `/onboarding` | Start first-run onboarding | Leak-based |
| `/rc` | Start Remote Control | Public |
| `/remote-control` | Full Remote Control command | Public |
| `/remote-env` | Configure remote environments | Public |
| `/remote-setup` | Set up a remote session | Leak-based |
| `/schedule` | Manage cloud scheduled tasks | Public |
| `/teleport` | Transfer or bridge sessions | Public |
| `/voice` | Enable push-to-talk voice mode | Public |

### Check Usage, Costs, Diagnostics, and UI State

| Command | Purpose | Status |
|---|---|---|
| `/cost` | Shortcut to the cost tab inside `/usage` | Public alias / shortcut |
| `/stats` | Shortcut to the stats tab inside `/usage` | Public alias / shortcut |
| `/usage` | Show limits, quota usage, costs, and category breakdowns | Public |
| `/usage-credits` | Open usage credits information; `/extra-usage` remains an alias | Public |
| `/ant-trace` | Internal tracing | Internal / leak-based |
| `/autofix-pr` | Auto-fix PR issues | Internal / leak-based |
| `/backfill-sessions` | Backfill session data | Internal / leak-based |
| `/break-cache` | Invalidate caches | Internal / leak-based |
| `/ctx_viz` | Debug context visualization | Internal / leak-based |
| `/debug-tool-call` | Debug a tool call | Internal / leak-based |
| `/good-claude` | Easter egg command | Leak-based |
| `/heapdump` | Dump heap for memory analysis | Internal / leak-based |
| `/mock-limits` | Mock rate limits | Internal / leak-based |
| `/perf-issue` | Report a performance issue | Internal / leak-based |
| `/reset-limits` | Reset rate limits | Internal / leak-based |
| `/statusline` | Customize the status line | Leak-based |
| `/stickers` | Easter egg or promo command | Public but non-essential |
| `/thinkback` | Replay or analyze thinking | Internal / leak-based |
| `/thinkback-play` | Animated thinking replay | Internal / leak-based |
| `/upgrade` | Run upgrade flow | Leak-based |
| `/version` | Show Claude Code version | Leak-based |
| `/x402` | x402 payment-protocol integration | Internal / leak-based |
| `/buddy` | Temporary April 1st easter egg | Limited / non-essential |

---

## A-Z Slash Command Index

| Command | Short meaning | Type |
|---|---|---|
| `/add-dir <path>` | Add another directory to scope | Public |
| `/advisor` | Architecture or design advice | Leak-based |
| `/agents` | Manage subagents | Public |
| `/ant-trace` | Internal tracing | Internal |
| `/autofix-pr` | Auto-fix PR issues | Internal / leak-based |
| `/backfill-sessions` | Backfill session data | Internal / leak-based |
| `/batch` | Apply one change across many files | Public / workflow |
| `/branch [name]` | Branch or fork the conversation/workflow | Public |
| `/break-cache` | Invalidate caches | Internal / leak-based |
| `/bridge` | Manage IDE or bridge sessions | Leak-based |
| `/bridge-kick` | Force-restart a bridge connection | Leak-based |
| `/brief` | Brief output mode | Leak-based |
| `/btw <question>` | Ask a side question with minimal context | Public |
| `/buddy` | Temporary April 1st command | Limited / non-essential |
| `/bughunter` | Bug-finding workflow | Leak-based |
| `/cd <path>` | Move the session to a new working directory | Public |
| `/chrome` | Open Chrome integration | Public |
| `/claude-api` | Load Claude API / SDK helper workflow | Built-in skill |
| `/clear` | Clear conversation context | Public |
| `/code-review [effort]` | Review correctness issues; supports `--fix` and `--comment` | Public |
| `/color [color]` | Change session accent color | Public |
| `/commit` | Generate a commit message and commit changes | Community |
| `/commit-push-pr` | Commit, push, and create a PR | Leak-based / community |
| `/compact [focus]` | Compact context with optional focus instructions | Public |
| `/config` | Open settings; supports `/config key=value` | Public |
| `/context` | Show context usage breakdown | Public |
| `/copy [N]` | Copy latest or selected response | Public |
| `/cost` | Open cost information inside `/usage` | Public alias / shortcut |
| `/ctx_viz` | Debug context visualization | Internal / leak-based |
| `/debug [desc]` | Run a debugging workflow | Public |
| `/debug-tool-call` | Debug a tool call | Internal / leak-based |
| `/desktop` | Hand off to desktop app | Public |
| `/diff` | Open diff viewer | Public |
| `/doctor` | Run diagnostics | Public |
| `/effort [low\|medium\|high\|xhigh\|max\|auto]` | Set reasoning effort | Public |
| `/env` | Inspect environment settings | Leak-based |
| `/exit` | Exit Claude Code | Public |
| `/export [filename]` | Export conversation | Public |
| `/fast [on\|off]` | Toggle fast mode | Public |
| `/feedback` | Send feedback | Public |
| `/files` | List files in context | Leak-based |
| `/fix-pipeline` | Repair failing CI pipelines | Community |
| `/focus` | Toggle Focus view | Public |
| `/goal` | Set a completion condition | Public |
| `/good-claude` | Easter egg command | Leak-based |
| `/heapdump` | Dump heap for memory analysis | Internal / leak-based |
| `/help` | Show help and available commands | Public |
| `/hooks` | Manage hook scripts and events | Public |
| `/ide` | Open or manage IDE integration | Public |
| `/init` | Create `CLAUDE.md` | Public |
| `/init-verifiers` | Set up verifier hooks | Leak-based |
| `/install` | Install/update flow | Internal / leak-based |
| `/install-github-app` | Set up GitHub App integration | Public |
| `/insights` | Show usage or session insights | Public |
| `/issue` | File a GitHub issue | Leak-based |
| `/keybindings` | Edit keyboard shortcuts | Public |
| `/less-permission-prompts` | Propose safe read-only allowlist entries | Built-in skill |
| `/lint` | Run linting commands | Community |
| `/login` | Sign in | Public |
| `/logout` | Sign out | Public |
| `/loop [interval]` | Run a recurring workflow | Public / workflow |
| `/mcp` | Manage MCP servers | Public |
| `/mcp__[server]__[prompt] [args]` | Dynamic MCP prompt command | MCP-generated |
| `/memory` | Open memory files | Public |
| `/merge-to-main` | Merge to main | Community |
| `/mobile` | Mobile integration or handoff | Leak-based |
| `/mock-limits` | Mock rate limits | Internal / leak-based |
| `/model [model]` | Switch active model | Public |
| `/oauth-refresh` | Refresh OAuth tokens | Leak-based |
| `/onboarding` | First-run onboarding | Leak-based |
| `/output-style [style]` | Change response style | Public |
| `/passes` | Multi-pass workflow | Leak-based |
| `/perf-issue` | Report performance issue | Internal / leak-based |
| `/permissions` | Manage permission rules and recent denials | Public |
| `/plan [desc]` | Enter plan mode | Public |
| `/plugin` | Manage plugins | Public |
| `/plugin list` | List installed plugins | Public |
| `/powerup` | Open interactive lessons | Public |
| `/pr` | Create a pull request | Community |
| `/pr-comments [PR]` | Fetch PR review comments | Public |
| `/pr_comments` | Internal form of `/pr-comments` | Internal |
| `/privacy-settings` | Open privacy settings | Leak-based |
| `/push` | Push current branch | Community |
| `/rate-limit-options` | Open rate-limit options | Leak-based |
| `/rc` | Start Remote Control | Public |
| `/release-notes` | View release notes | Public |
| `/reload-plugins` | Reload plugins | Public |
| `/reload-skills` | Re-scan skill directories | Public |
| `/remote-control` | Start or manage Remote Control | Public |
| `/remote-env` | Configure remote environments | Public |
| `/remote-setup` | Set up remote session | Leak-based |
| `/rename [name]` | Rename current session | Public |
| `/reset-limits` | Reset rate limits | Internal / leak-based |
| `/resume [session]` | Resume previous session | Public |
| `/review` | Review current code changes; PR reviews use the `/code-review medium` engine | Public |
| `/rewind` | Rewind to an earlier checkpoint, including before `/clear` | Public |
| `/sandbox` | Open sandbox controls and credential/network protections | Public |
| `/sandbox-toggle` | Internal sandbox toggle | Internal |
| `/schedule` | Manage scheduled tasks | Public |
| `/scroll-speed` | Tune mouse wheel scroll speed | Public |
| `/security-review` | Run security-focused review | Public |
| `/session` | Session management UI | Leak-based |
| `/share` | Share a session | Leak-based |
| `/simplify` | Run cleanup-only review and apply fixes | Public |
| `/skills` | List skills | Public |
| `/stats` | Open stats tab inside `/usage` | Public alias / shortcut |
| `/status` | Show session status | Public |
| `/statusline` | Customize status line | Leak-based |
| `/stickers` | Easter egg or promo command | Public but non-essential |
| `/summary` | Generate session summary | Leak-based |
| `/tag` | Legacy tag command | Removed |
| `/tasks` | Manage background tasks | Leak-based |
| `/team-onboarding` | Generate teammate onboarding guide | Public |
| `/teleport` | Bridge or transfer sessions | Public |
| `/terminal-setup` | Configure terminal integration | Public |
| `/terminalSetup` | Internal form of `/terminal-setup` | Internal |
| `/theme` | Change or create themes | Public |
| `/thinkback` | Replay or analyze thinking | Internal / leak-based |
| `/thinkback-play` | Animated thinking replay | Internal / leak-based |
| `/tui` | Switch terminal UI mode | Public |
| `/ultraplan` | Detailed planning workflow | Leak-based |
| `/ultrareview [PR#]` | Comprehensive cloud code review | Public / workflow |
| `/upgrade` | Upgrade flow | Leak-based |
| `/usage` | Show plan limits, usage, and costs | Public |
| `/usage-credits` | Show usage credits | Public |
| `/version` | Show version | Leak-based |
| `/vim` | Old Vim-mode command | Removed |
| `/vitest` | Run Vitest workflows | Community |
| `/voice` | Enable push-to-talk voice mode | Public |
| `/workflows` | View dynamic workflow runs | Public |
| `/x402` | x402 integration | Internal / leak-based |

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

Use `/mcp` to connect servers and inspect the commands they expose. Reconnect picks up `.mcp.json` edits without restarting Claude Code. Newer builds also show startup notices when MCP servers need authentication.

---

## CLI Commands and Flags

### Core CLI Commands

| Command | Purpose |
|---|---|
| `claude` | Start interactive Claude Code |
| `claude agents` | Open agent view: running, blocked, and completed Claude Code sessions |
| `claude agents --json` | List active Claude Code sessions as JSON, including blocked and just-dispatched sessions, with `id` and `state` fields |
| `claude agents --json --all` | Include completed sessions in the JSON agent list |
| `claude agents` then `! <command>` | Start a shell command as a background session you can attach to or detach from |
| `claude "prompt"` | Start with an initial prompt |
| `claude -p "prompt"` | Run a non-interactive single prompt |
| `claude --bg --exec '<command>'` | Run a shell command as a background Claude session |
| `claude -c` | Continue the last conversation |
| `claude -r "name"` | Resume a named session |
| `claude update` | Update Claude Code |
| `claude mcp list` | List MCP servers |
| `claude mcp login <name>` | Authenticate an MCP server from the CLI; supports `--no-browser` for SSH or headless use |
| `claude mcp logout <name>` | Sign out an MCP server from the CLI |
| `claude mcp serve` | Run Claude Code as an MCP server |
| `claude plugin init <name>` | Scaffold a new plugin in `.claude/skills` |
| `claude plugin details <name>` | Show plugin components and projected per-session token cost |
| `claude plugin tag` | Create release git tags for plugins with version validation |
| `claude plugin marketplace remove <name> --scope user\|project\|local` | Remove a marketplace from a selected configuration scope |

### Important Flags

| Flag | Purpose |
|---|---|
| `--add-dir` | Add an extra directory to scope |
| `--agent` | Select an agent |
| `--allowedTools` | Pre-approve tools |
| `--bare` | Minimal headless mode |
| `--channels` | Enable channel/MCP push relay |
| `--chrome` | Enable Chrome integration mode |
| `--console` | Use Anthropic Console auth |
| `--dangerously-skip-permissions` | Skip permission prompts |
| `--effort` | Set reasoning effort |
| `--exclude-dynamic-system-prompt-sections` | Improve print-mode cross-user prompt caching |
| `--fallback-model` | Continue the session with a configured fallback when the primary model is unavailable |
| `--json-schema` | Request structured output; recent builds avoid repeat `StructuredOutput` calls after a valid result |
| `--max-budget-usd` | Cap spend |
| `--max-turns` | Limit turns |
| `--mcp-config` | Use a specific MCP config for dispatched background sessions |
| `--model` | Set the model |
| `-n`, `--name` | Name the session |
| `--output-format` | Set machine-readable output |
| `--permission-mode` | Set permission behavior |
| `--plugin-dir` | Use a plugin directory for dispatched background sessions |
| `--plugin-url <url>` | Fetch a plugin `.zip` archive from a URL for the current session |
| `-r` | Resume a session |
| `--remote` | Start a remote/web-backed session |
| `--remote-control-session-name-prefix` | Prefix Remote Control session names |
| `--safe-mode` | Start Claude Code with customizations disabled for troubleshooting |
| `--settings` | Load settings for dispatched background sessions |
| `--tools` | Explicitly allow tools; `Grep` and `Glob` now map to the dedicated native search tools on builds that include embedded search |
| `--transport http\|stdio\|sse` | Select MCP transport |
| `--verbose` | Enable verbose output |
| `-w`, `--worktree` | Use a git worktree |

---

## Environment Variables

| Variable | What it does |
|---|---|
| `CLAUDE_CODE_CERT_STORE=bundled` | Uses bundled CAs only instead of the OS certificate store |
| `CLAUDE_CODE_DISABLE_BUNDLED_SKILLS` | Hides bundled skills, workflows, and built-in slash commands from the model |
| `CLAUDE_CODE_ENABLE_AUTO_MODE=1` | Enables Auto mode on Bedrock, Vertex, and Foundry for supported Opus 4.7 and Opus 4.8 setups |
| `CLAUDE_CODE_ENABLE_FEEDBACK_SURVEY_FOR_OTEL` | Re-enables the session quality survey for enterprises capturing responses through OpenTelemetry |
| `CLAUDE_CODE_DISABLE_BG_SHELL_PRESSURE_REAP=1` | Disables automatic memory-pressure cleanup for idle background shell commands |
| `CLAUDE_CODE_MCP_TOOL_IDLE_TIMEOUT` | Overrides the idle timeout for remote MCP tool calls that stop responding |
| `CLAUDE_CLIENT_PRESENCE_FILE` | Points to a local marker file that suppresses mobile push notifications while you are at the machine |
| `CLAUDE_CODE_PERFORCE_MODE=1` | Makes Edit/Write/NotebookEdit fail on read-only Perforce files with a `p4 edit` hint |
| `CLAUDE_CODE_SAFE_MODE` | Starts Claude Code with customizations disabled for troubleshooting |
| `CLAUDE_CODE_SCRIPT_CAPS` | Limits per-session script invocations |
| `CLAUDE_CODE_USE_MANTLE=1` | Enables Amazon Bedrock powered by Mantle |
| `DISABLE_UPDATES` | Completely blocks all update paths, including manual `claude update`; stricter than `DISABLE_AUTOUPDATER` |
| `CLAUDE_CODE_SESSION_ID` | Session ID |
| `CLAUDE_CODE_USE_POWERSHELL_TOOL` | Opts into or out of the PowerShell tool rollout; on Linux and macOS, set it to `1` when `pwsh` is available |
| `CLAUDE_CODE_FORCE_SYNC_OUTPUT=1` | Forces synchronized output on terminals where auto-detection misses it, such as Emacs eat |
| `CLAUDE_CODE_DISABLE_ALTERNATE_SCREEN=1` | Opts out of the fullscreen alternate-screen renderer and keeps the conversation in the terminal's native scrollback |
| `CLAUDE_CODE_PACKAGE_MANAGER_AUTO_UPDATE` | Lets Homebrew or WinGet installations run package-manager upgrades in the background, then prompt for restart |
| `CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1` | Enables gateway `/v1/models` discovery for the `/model` picker |
| `OTEL_LOG_ASSISTANT_RESPONSES` | Controls assistant response text in `claude_code.assistant_response` OpenTelemetry logs; when unset, it follows `OTEL_LOG_USER_PROMPTS`; set `0` to keep prompts-only logging or `1` to log response content |
| `OTEL_LOG_TOOL_DETAILS=1` | Adds tool parameters such as Bash commands and MCP or skill names to tool decision telemetry events |
| `OTEL_RESOURCE_ATTRIBUTES` | Adds custom labels to OpenTelemetry metric datapoints, such as team or repository labels |

Remote Control, `/schedule`, Claude.ai MCP connectors, and notification preferences are disabled when `ANTHROPIC_API_KEY`, `apiKeyHelper`, or `ANTHROPIC_AUTH_TOKEN` is set.

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

## Internal, Experimental, Removed, and Community Commands

These commands are preserved for completeness. Do not treat this section as a guarantee that a command works in every public build.

| Command | Category | Typical role |
|---|---|---|
| `/advisor` | Leak-based | Architecture or design advice |
| `/ant-trace` | Internal | Internal tracing |
| `/autofix-pr` | Internal / leak-based | Auto-fix PR issues |
| `/backfill-sessions` | Internal / leak-based | Backfill session data |
| `/brief` | Leak-based | Brief output mode |
| `/bridge` | Leak-based | IDE or bridge session manager |
| `/bridge-kick` | Leak-based | Force-restart bridge connection |
| `/bughunter` | Leak-based | Bug-finding workflow |
| `/buddy` | Limited / non-essential | Temporary April 1st command |
| `/commit` | Community | Generate a commit message and commit changes |
| `/commit-push-pr` | Leak-based / community | Commit, push, and create a PR |
| `/ctx_viz` | Internal / leak-based | Debug context visualization |
| `/debug-tool-call` | Internal / leak-based | Debug a tool call |
| `/env` | Leak-based | Environment inspection |
| `/files` | Leak-based | List files in current context |
| `/fix-pipeline` | Community | Repair failing CI pipelines |
| `/good-claude` | Leak-based | Easter egg command |
| `/heapdump` | Internal / leak-based | Dump heap for memory analysis |
| `/init-verifiers` | Leak-based | Set up verifier hooks |
| `/install` | Internal / leak-based | Install or update flow |
| `/issue` | Leak-based | File a GitHub issue |
| `/lint` | Community | Run linting commands |
| `/merge-to-main` | Community | Merge-to-main workflow |
| `/mobile` | Leak-based | Mobile integration or handoff |
| `/mock-limits` | Internal / leak-based | Mock rate limits |
| `/oauth-refresh` | Leak-based | Refresh OAuth tokens |
| `/onboarding` | Leak-based | First-run onboarding |
| `/passes` | Leak-based | Multi-pass workflow |
| `/perf-issue` | Internal / leak-based | Report performance issue |
| `/pr` | Community | Create a pull request |
| `/pr_comments` | Internal | Internal form of `/pr-comments` |
| `/privacy-settings` | Leak-based | Privacy settings |
| `/push` | Community | Push current branch |
| `/rate-limit-options` | Leak-based | Rate-limit options |
| `/remote-setup` | Leak-based | Remote setup flow |
| `/reset-limits` | Internal / leak-based | Reset rate limits |
| `/sandbox-toggle` | Internal | Internal sandbox toggle |
| `/session` | Leak-based | Session management UI |
| `/share` | Leak-based | Share a session |
| `/statusline` | Leak-based | Customize status line |
| `/summary` | Leak-based | Generate a session summary |
| `/tag` | Removed | Legacy tag command |
| `/tasks` | Leak-based | Manage background tasks |
| `/terminalSetup` | Internal | Internal form of `/terminal-setup` |
| `/thinkback` | Internal / leak-based | Replay or analyze thinking |
| `/thinkback-play` | Internal / leak-based | Animated thinking replay |
| `/ultraplan` | Leak-based | Detailed planning workflow |
| `/upgrade` | Leak-based | Upgrade flow |
| `/version` | Leak-based | Show version |
| `/vim` | Removed | Old Vim-mode slash command |
| `/vitest` | Community | Run Vitest-based test workflows |
| `/x402` | Internal / leak-based | x402 integration |

---

## Notes

- `/vim` was removed in `v2.1.92`. Use `/config` for editor mode settings.
- `/tag` was removed in `v2.1.92`.
- As of `v2.1.118`, `/cost` and `/stats` are merged into `/usage`; both still work as shortcuts.
- `/simplify` now runs a cleanup-only review and applies simplification, reuse, efficiency, and structure fixes. Use `/code-review --fix` when you want bug-hunting fixes.
- `/extra-usage` was renamed `/usage-credits`; the old command remains an alias.
- The old `CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE` path is now a no-op.
- If you customized the old `modelPicker:setAsDefault` keybinding, rename it to `modelPicker:thisSessionOnly`; the `d` action was replaced by `s`.
- The dynamic workflow trigger keyword was renamed from `workflow` to `ultracode`; use `/workflows` to view larger background runs.
- Managed settings can now set `requiredMinimumVersion` and `requiredMaximumVersion` so Claude Code refuses to start outside an approved version range.
- `disableBundledSkills` and `CLAUDE_CODE_DISABLE_BUNDLED_SKILLS` can hide bundled skills, workflows, and built-in slash commands from the model.
- `!` bash commands now prompt Claude to respond to the command output automatically and offer live file path autocomplete. Set `respondToBashCommands` to `false` in settings to keep the older context-only behavior.
- `autoMode.classifyAllShell` routes all Bash and PowerShell commands through the auto-mode classifier instead of only arbitrary-code-execution patterns.
- `sandbox.credentials` can block sandboxed commands from reading credential files and secret environment variables.
- `CLAUDE_CODE_MAX_RETRIES` is capped at 15. Use `CLAUDE_CODE_RETRY_WATCHDOG` for unattended retry monitoring.

---

## Sources

- Claude Code changelogs through `v2.1.193`
- Local command reference notes and leak-based command lists

---

## Related Resources

- [awesome-claude-code](https://github.com/jqueryscript/awesome-claude-code): curated tools, workflows, integrations, and resources for Claude Code users
- [Anthropic Agent SDK Slash Commands Docs](https://platform.claude.com/docs/en/agent-sdk/slash-commands): official slash command documentation
- [Claude Code Commands Cheat Sheet (Full Article)](https://www.scriptbyai.com/claude-code-commands-cheat-sheet/): expanded version with explanations and workflows
- [Best Agent Skills](https://www.scriptbyai.com/best-agent-skills/): useful skills for Claude Code and other AI coding workflows
- [AI Coding Agents](https://www.scriptbyai.com/best-cli-ai-coding-agents/): comparison of Claude Code and other CLI coding agents

*Last audited: July 21, 2026*

