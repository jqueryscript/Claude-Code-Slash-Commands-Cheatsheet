# Claude Code Commands Cheatsheet

> Slash commands, MCP commands, CLI commands, flags, environment variables, and workflows. Last audited: September 2, 2026.

[![Status](https://img.shields.io/badge/status-updated-brightgreen)](#)
[![Commands](https://img.shields.io/badge/commands-70%2B-blue)](#)
[![Updated](https://img.shields.io/badge/updated-September%202%202026-orange)](#)
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
| `/add-dir <path>` | Add another directory to the working scope; network paths are refused, so use a mapped drive letter on Windows | Public |
| `/config` | Open settings, including editor mode, keybinding flavor, spellcheck, output style, usage-limit continuation, cross-session message handling, dialog expiry, and ultracode keyword trigger settings; `/config key=value` sets a setting from the prompt | Public |
| `/doctor` | Run a full setup checkup, diagnose problems, and offer fixes; current builds also explain failures to load server-managed settings; `/checkup` is an alias | Public |
| `/effort [low\|medium\|high\|xhigh\|max\|auto]` | Set reasoning effort per model; press `s` in the picker to change only the current session | Public |
| `/fast [on\|off]` | Toggle fast mode for Opus 5 and Opus 4.8 | Public |
| `/help` | Show help and available commands | Public |
| `/hooks` | Manage hooks; `PreModelSwitch` can block, confirm, or annotate a model change, `PostModelSwitch` runs afterward, and resume-time `SessionStart` receives staleness and re-cache estimates | Public |
| `/init` | Generate `CLAUDE.md` | Public |
| `/keybindings` | Edit keybindings, including actions such as `selection:clear` | Public |
| `/login` | Sign in with a Claude account, an Anthropic Console account without creating an API key, or a supported API-key flow | Public |
| `/logout` | Sign out | Public |
| `/memory` | Open memory files | Public |
| `/model [model]` | Switch models; the picker saves the default for new sessions, `s` switches only the current session, `ANTHROPIC_DEFAULT_MODEL` sets the startup model, and `modelPicker` can curate the picker | Public |
| `/output-style [style]` | Change response style; `Concise` is a built-in style available from `/config` > Output style | Public |
| `/permissions` | Manage permission rules and recent denials; the Auto mode tab lets you view and edit classifier rules, and Manual remains the default mode | Public |
| `/sandbox` | Open sandbox controls; newer builds can block credential reads, remember approved network hosts for the session, and enforce wildcard read-deny rules on macOS | Public |
| `/team-onboarding` | Generate a teammate ramp-up guide from local Claude Code usage | Public |
| `/terminal-setup` | Configure terminal integration and fix terminal rendering issues | Public |
| `/theme` | Change or create themes, including custom JSON and plugin-shipped themes | Public |
| `/scroll-speed` | Tune mouse wheel scroll speed with live preview | Public |
| `/tui` | Switch terminal UI mode; `/tui fullscreen` enables fullscreen rendering | Public |
| `Vim mode` | Editor mode available through `/config`; `/vim` was removed | Setting, not current slash command |

### Manage Context and Sessions

| Command | Purpose | Status |
|---|---|---|
| `/branch [name]` | Branch the current conversation or workflow | Public |
| `/cd <path>` | Move the session to a new working directory and immediately load that directory's project settings, hooks, approved `.mcp.json` servers, skills, and agents | Public |
| `/clear` | Clear the current conversation context | Public |
| `/compact [focus]` | Compact context with optional focus instructions | Public |
| `/context` | Show context usage breakdown, skill token estimates, and plugin-sourced skill names | Public |
| `/copy [N]` | Copy the latest or selected response | Public |
| `/export [filename]` | Export the conversation | Public |
| `/fork` | Copy the conversation into a new background session and its own worktree | Public |
| `/goal` | Set a completion condition and keep Claude working across turns; an idle goal gets at most three background check-ins, and your next message allows three more | Public |
| `/rename [name]` | Rename the current session | Public |
| `/resume [session]` | Resume a previous session, including background sessions; active goals are restored, and the picker loads older sessions as you scroll | Public |
| `/rewind` | Rewind to an earlier checkpoint, including checkpoints before `/clear`; `/undo` appears as an alias | Public |
| `/session` | Open session management UI | Leak-based |
| `/share` | Share the conversation; alias of `/feedback` | Public alias |
| `/status` | Show session status, mode, GitHub connection for Claude Code on the web, and managed-setting sources skipped by precedence | Public |
| `/summary` | Generate a session summary | Leak-based |
| `/exit` | Exit Claude Code | Public |

### Review, Debug, and Change Code

| Command | Purpose | Status |
|---|---|---|
| `/advisor` | Architecture or design advice workflow | Leak-based |
| `/batch` | Apply one change across many files or worktrees | Public / workflow command |
| `/brief` | Brief output mode | Leak-based |
| `/btw <question>` | Ask a side question with minimal context; browse history with `Shift+Left`/`Shift+Right` or `[`/`]`, and press `c` to copy raw Markdown | Public |
| `/bughunter` | Bug-finding workflow | Leak-based |
| `/bug [report]` | Report a bug with optional session context; alias of `/feedback` | Public alias |
| `/code-review [level] [PR#]` | Review the current diff or a PR in a background subagent; use `ultra` for a deep cloud review and `--comment` to post GitHub PR or GitLab MR findings | Public |
| `/debug [desc]` | Run a debugging workflow | Public |
| `/diff` | Open the diff viewer; detail view supports keyboard scrolling | Public |
| `/feedback [report]` | Send feedback, report a bug, or share the conversation; Claude can draft a report for your review unless `feedbackDrafts` is disabled | Public |
| `/files` | List files in current context | Leak-based |
| `/focus` | Toggle Focus view | Public |
| `/insights` | Show usage/session insights | Public |
| `/loop [interval]` | Run a recurring workflow; self-paced dynamic mode and the no-prompt autonomous default work across Anthropic, Bedrock, Vertex AI, and Foundry; `/proactive` appears as an alias | Public / workflow command |
| `/passes` | Run a multi-pass workflow | Leak-based |
| `/plan [desc]` | Enter plan mode | Public |
| `/powerup` | Open interactive lessons | Public |
| `/pr-comments [PR]` | Fetch PR review comments | Public |
| `/pr_comments` | Internal underscore form of `/pr-comments` | Internal |
| `/rate-limit-options` | Open rate-limit options | Leak-based |
| `/release-notes` | View release notes | Public |
| `/review` | Alias of `/code-review`; reviews the current diff or a PR | Public alias |
| `/security-review` | Run a security-focused review | Public |
| `/simplify` | Run a cleanup-only review and apply simplification, reuse, efficiency, and structure fixes | Public |
| `/tasks` | List and manage background tasks, including the model and effort used by each subagent; `/bashes` is an alias | Public |
| `/ultraplan` | Old detailed planning workflow | Removed in `v2.1.222` |
| `/ultrareview [PR#]` | Run the established deep cloud review workflow; `/code-review ultra` is the current form | Public / workflow command |
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
| `/agents` | Open the in-session subagent manager and custom-agent library | Public |
| `/bridge` | Manage IDE or bridge sessions | Leak-based |
| `/bridge-kick` | Force-restart a bridge connection | Leak-based |
| `/claude-api` | Load Claude API or SDK guidance; `upgrade` migrates Python projects from `anthropic` 0.x to 1.x, and `cost-optimize` profiles API spend and works through measured cost reductions | Built-in skill command |
| `/dataviz` | Load chart and dashboard design guidance | Built-in skill command |
| `/less-permission-prompts` | Scan transcripts for safe read-only Bash and MCP allowlist candidates | Built-in skill command |
| `/mcp` | Manage MCP servers, authentication, dynamic MCP commands, and connection-time headers generated by `headersHelper` | Public |
| `/mcp__[server]__[prompt] [args]` | Run a dynamic MCP prompt command | Generated by connected MCP servers |
| `/plugin` | Manage plugins, including HTTPS zip archive sources with optional SHA-256 pinning and marketplace `headersHelper` authentication | Public |
| `/plugin list` | List installed plugins; supports `--enabled` and `--disabled` filters | Public |
| `/reload-plugins` | Reload plugins; also works from Remote Control clients | Public |
| `/reload-skills` | Re-scan skill directories without restarting Claude Code | Public |
| `/skills` | List available skills | Public |
| `/subtask <task>` | Start a forked subagent that inherits the full conversation and prompt cache | Public |

Skills and slash commands can set `disallowed-tools` in frontmatter to remove tools while that workflow is active.

On Windows, macOS, and Linux, `ListAgents` can discover other Claude Code sessions and `SendMessage` can contact them across machines. `ListAgents` and `/list-agents` also include live teammates. Type `@` in the prompt to mention a live session by name. `/config` controls whether inbound messages are accepted, held, or refused. Sessions running with bypassed permissions hold inbound messages for approval by default. The optional `notify_when_idle` request asks a recipient session to send one notice when it next goes idle; it is a one-shot option with no polling.

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
| `/cost` | Open cost data plus the current session's prompt-cache hit ratio, misses, re-cached tokens, and warm or cold state | Public alias / shortcut |
| `/stats` | Shortcut to the stats tab inside `/usage` | Public alias / shortcut |
| `/usage` | Show limits, quota usage, costs, category breakdowns, and per-loop data; Claude apps gateways with spend limits also show a Spend limit bar | Public |
| `/usage-credits` | View usage credits or request a higher limit when the organization supports it; `/extra-usage` remains an alias | Public |
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
| `/agents` | Open the in-session subagent manager and custom-agent library | Public |
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
| `/bug [report]` | Report a bug; alias of `/feedback` | Public alias |
| `/bughunter` | Bug-finding workflow | Leak-based |
| `/cd <path>` | Move the session and load the new directory's project configuration | Public |
| `/checkup` | Alias of `/doctor` | Public alias |
| `/chrome` | Open Chrome integration | Public |
| `/claude-api` | Load Claude API or SDK guidance; includes `upgrade` and `cost-optimize` workflows | Built-in skill |
| `/clear` | Clear conversation context | Public |
| `/code-review [level] [PR#]` | Review the current diff or a PR; `ultra` runs a deep cloud review | Public |
| `/color [color]` | Change session accent color | Public |
| `/commit` | Generate a commit message and commit changes | Community |
| `/commit-push-pr` | Commit, push, and create a PR | Leak-based / community |
| `/compact [focus]` | Compact context with optional focus instructions | Public |
| `/config` | Open settings, including keybinding flavor, spellcheck, output style, and usage-limit continuation; supports `/config key=value` | Public |
| `/context` | Show context usage breakdown | Public |
| `/copy [N]` | Copy latest or selected response | Public |
| `/cost` | Open cost information inside `/usage` | Public alias / shortcut |
| `/ctx_viz` | Debug context visualization | Internal / leak-based |
| `/dataviz` | Load chart and dashboard design guidance | Built-in skill |
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
| `/feedback [report]` | Send feedback or review a Claude-drafted report | Public |
| `/files` | List files in context | Leak-based |
| `/fix-pipeline` | Repair failing CI pipelines | Community |
| `/focus` | Toggle Focus view | Public |
| `/fork` | Copy the conversation into a new background session and worktree | Public |
| `/goal` | Set a completion condition; idle goals get up to three background check-ins until the next message | Public |
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
| `/login` | Sign in, including keyless Anthropic Console account authentication | Public |
| `/logout` | Sign out | Public |
| `/loop [interval]` | Run a recurring or self-paced autonomous workflow | Public / workflow |
| `/mcp` | Manage MCP servers, authentication, and dynamic headers | Public |
| `/mcp__[server]__[prompt] [args]` | Dynamic MCP prompt command | MCP-generated |
| `/memory` | Open memory files | Public |
| `/merge-to-main` | Merge to main | Community |
| `/mobile` | Mobile integration or handoff | Leak-based |
| `/mock-limits` | Mock rate limits | Internal / leak-based |
| `/model [model]` | Switch active model; `ANTHROPIC_DEFAULT_MODEL` sets the startup model and `modelPicker` can curate the picker | Public |
| `/oauth-refresh` | Refresh OAuth tokens | Leak-based |
| `/onboarding` | First-run onboarding | Leak-based |
| `/output-style [style]` | Change response style, including the built-in `Concise` style | Public |
| `/passes` | Multi-pass workflow | Leak-based |
| `/perf-issue` | Report performance issue | Internal / leak-based |
| `/permissions` | Manage permission rules, recent denials, and Auto mode classifier rules | Public |
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
| `/review` | Alias of `/code-review` for the current diff or a PR | Public alias |
| `/rewind` | Rewind to an earlier checkpoint, including before `/clear` | Public |
| `/sandbox` | Open sandbox controls and credential/network protections | Public |
| `/sandbox-toggle` | Internal sandbox toggle | Internal |
| `/schedule` | Manage scheduled tasks | Public |
| `/scroll-speed` | Tune mouse wheel scroll speed | Public |
| `/security-review` | Run security-focused review | Public |
| `/session` | Session management UI | Leak-based |
| `/share` | Share the conversation; alias of `/feedback` | Public alias |
| `/simplify` | Run cleanup-only review and apply fixes | Public |
| `/skills` | List skills | Public |
| `/stats` | Open stats tab inside `/usage` | Public alias / shortcut |
| `/status` | Show session, web GitHub connection, and managed-setting source status | Public |
| `/statusline` | Customize status line | Leak-based |
| `/stickers` | Easter egg or promo command | Public but non-essential |
| `/summary` | Generate session summary | Leak-based |
| `/subtask <task>` | Start a forked subagent with the current conversation context | Public |
| `/tag` | Legacy tag command | Removed |
| `/tasks` | List background tasks with each subagent's model and effort | Public |
| `/team-onboarding` | Generate teammate onboarding guide | Public |
| `/teleport` | Bridge or transfer sessions | Public |
| `/terminal-setup` | Configure terminal integration | Public |
| `/terminalSetup` | Internal form of `/terminal-setup` | Internal |
| `/theme` | Change or create themes | Public |
| `/thinkback` | Replay or analyze thinking | Internal / leak-based |
| `/thinkback-play` | Animated thinking replay | Internal / leak-based |
| `/tui` | Switch terminal UI mode | Public |
| `/ultraplan` | Old detailed planning workflow | Removed |
| `/ultrareview [PR#]` | Comprehensive cloud code review | Public / workflow |
| `/upgrade` | Upgrade flow | Leak-based |
| `/usage` | Show limits, costs, usage breakdowns, and per-loop run and token data | Public |
| `/usage-credits` | View credits or request a higher supported organization limit | Public |
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

Use `/mcp` to connect servers and inspect the commands they expose. Reconnect picks up `.mcp.json` edits without restarting Claude Code. Newer builds also show startup notices when MCP servers need authentication. For HTTP, SSE, or WebSocket servers, `headersHelper` can generate short-lived request headers at connection time. Project-scoped helpers run only after workspace trust is accepted, and helpers from project, plugin, or agent configuration do not inherit credential environment variables.

---

## CLI Commands and Flags

### Core CLI Commands

| Command | Purpose |
|---|---|
| `claude` | Start interactive Claude Code |
| `claude agents` | Open agent view: running, blocked, and completed Claude Code sessions |
| `claude agents --json` | List active Claude Code sessions as JSON, including blocked and just-dispatched sessions, with `id` and `state` fields |
| `claude agents --json --all` | Include completed sessions in the JSON agent list |
| `claude attach <id>` | Attach this terminal to a background session |
| `claude logs <id>` | Print recent output from a background session |
| `claude stop <id>` | Stop a background session; `claude kill` is an alias |
| `claude respawn <id>` | Restart a running or stopped session and resume its saved conversation |
| `claude respawn --all` | Restart every running background session on the current Claude Code binary |
| `claude rm <id>` | Remove a session when its Claude-created worktree is safe to remove; keep its transcript available through `claude --resume` |
| `claude agents` then `! <command>` | Start a shell command as a background session you can attach to or detach from |
| `claude "prompt"` | Start with an initial prompt |
| `claude -p "prompt"` | Run a non-interactive single prompt |
| `claude --bg --exec '<command>'` | Run a shell command as a background Claude session |
| `claude -c` | Continue the last conversation |
| `claude -r "name"` | Resume a named session |
| `claude remote-control --continue` | Resume the most recent Remote Control server session for the current directory |
| `claude --teleport <session-id>` | Continue a cloud session in the matching local repository |
| `claude auto-mode reset [--yes]` | Restore the default auto-mode configuration |
| `claude self-hosted-runner` | Register a machine or container for Team and Enterprise web, mobile, and desktop sessions |
| `claude self-hosted-runner --client-label <label>` | Override the label registered by the runner; the default is the hostname |
| `claude self-hosted-runner --defer-shutdown-max-min <minutes>` | On SIGTERM, keep attached sessions serving, park remaining work after the timeout, then exit |
| `claude self-hosted-runner --proxy-authorization-command <command>` / `--proxy-authorization-file <path>` | Supply a fresh `Proxy-Authorization` header for each egress connection |
| `claude update` | Update Claude Code |
| `claude mcp list` | List MCP servers; disabled servers appear as `⊘ Disabled` without a health check |
| `claude mcp get <name>` | Show details for one MCP server; disabled servers appear as `⊘ Disabled` without a health check |
| `claude mcp login <name>` | Authenticate an MCP server from the CLI; supports `--no-browser` for SSH or headless use |
| `claude mcp logout <name>` | Sign out an MCP server from the CLI |
| `claude mcp serve` | Run Claude Code as an MCP server |
| `claude plugin init <name>` | Scaffold a new plugin in `.claude/skills` |
| `claude plugin install <name> [-y]` | Install a marketplace plugin; print a command-source helper first and use `-y`/`--yes` to skip its confirmation prompt |
| `claude plugin update <name> [-y]` | Update a plugin; use `-y`/`--yes` to skip the command-source confirmation prompt |
| `claude plugin details <name>` | Show plugin components and projected per-session token cost |
| `claude plugin tag` | Create release git tags for plugins with version validation |
| `claude plugin marketplace remove <name> --scope user\|project\|local` | Remove a marketplace from a selected configuration scope |

### Important Flags

| Flag | Purpose |
|---|---|
| `--add-dir` | Add an extra directory to scope; network paths are refused, so use a mapped drive letter on Windows |
| `--agent` | Select an agent |
| `--allowedTools` | Pre-approve tools |
| `--ax-screen-reader` | Use plain-text rendering for screen readers |
| `--bare` | Minimal headless mode |
| `--channels` | Enable channel/MCP push relay |
| `--chrome` | Enable Chrome integration mode |
| `--console` | Use Anthropic Console auth |
| `--dangerously-skip-permissions` | Skip permission prompts |
| `--effort` | Set reasoning effort for the current session without changing the saved per-model default |
| `--exclude-dynamic-system-prompt-sections` | Improve print-mode cross-user prompt caching |
| `--fallback-model` | Continue the session with a configured fallback when the primary model is unavailable |
| `--forward-subagent-text` | Include subagent text and thinking in stream-json output |
| `--json-schema` | Request structured output; recent builds avoid repeat `StructuredOutput` calls after a valid result |
| `--max-budget-usd` | Cap spend |
| `--max-turns` | Limit turns |
| `--mcp-config` | Use a specific MCP config for dispatched background sessions |
| `--model` | Set the model |
| `-n`, `--name` | Name the session |
| `--output-format` | Set machine-readable output |
| `--permission-mode` | Set permission behavior; `manual` is the default mode name |
| `--plugin-dir` | Use a plugin directory for dispatched background sessions |
| `--plugin-url <url>` | Fetch a plugin `.zip` archive from a URL for the current session |
| `-r` | Resume a session |
| `--remote` | Start a remote/web-backed session |
| `--remote-control-session-name-prefix` | Prefix Remote Control session names |
| `--restricted` | Start a shared-machine or evaluation session without command/code tools or WebFetch, confine file tools to working directories, load only managed settings and `--settings`, and refuse `bypassPermissions` |
| `--safe-mode` | Start Claude Code with customizations disabled for troubleshooting |
| `--settings` | Load settings for dispatched background sessions |
| `--tools` | Explicitly allow tools; `Grep` and `Glob` now map to the dedicated native search tools on builds that include embedded search |
| `--transport http\|stdio\|sse` | Select MCP transport |
| `--verbose` | Enable verbose output |
| `-w`, `--worktree` | Use an isolated git worktree; accepts a name, GitHub PR number or URL, or GitLab MR URL |

---

## Environment Variables

| Variable | What it does |
|---|---|
| `ANTHROPIC_DEFAULT_MODEL` | Sets the model used when new sessions start; a `/model` selection still overrides it and persists across restarts |
| `CLAUDE_CODE_CERT_STORE=bundled` | Uses bundled CAs only instead of the OS certificate store |
| `CLAUDE_CODE_DISABLE_BUNDLED_SKILLS` | Hides bundled skills, workflows, and built-in slash commands from the model |
| `CLAUDE_CODE_ENABLE_FEEDBACK_SURVEY_FOR_OTEL` | Re-enables the session quality survey for enterprises capturing responses through OpenTelemetry |
| `CLAUDE_CODE_DISABLE_BG_SHELL_PRESSURE_REAP=1` | Disables automatic memory-pressure cleanup for idle background shell commands |
| `CLAUDE_CODE_DISABLE_1M_CONTEXT=1` | Holds models with a native 1M window to 200K through auto-compaction |
| `CLAUDE_CODE_DISABLE_MOUSE_CLICKS=1` | Disables click, drag, and hover in fullscreen mode while keeping wheel scrolling |
| `CLAUDE_CODE_ENABLE_TODO_TOOLS=1` | Restores the legacy task-tracking tools on newer models that no longer expose them by default |
| `CLAUDE_CODE_FORK_SUBAGENT` | Sets fork mode: `1` enables it in print mode and the Agent SDK; `0` disables it everywhere |
| `CLAUDE_CODE_SUBAGENT_MODEL` | Sets the default subagent model; agent frontmatter and explicit per-spawn models take precedence |
| `CLAUDE_CODE_SUBAGENT_MODEL_FORCE=1` | Forces every subagent to use `CLAUDE_CODE_SUBAGENT_MODEL`, or the main model when it is unset |
| `CLAUDE_CODE_FORWARD_SUBAGENT_TEXT=1` | Includes subagent text and thinking in stream-json output |
| `CLAUDE_CODE_GOAL_CHECKIN_MINUTES` | Sets how long background work can keep an active `/goal` waiting; default is 30 minutes and `0` disables check-ins |
| `CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS` | Sets the concurrent subagent cap; the default is 20 |
| `CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH` | Sets nested subagent depth; the default is 3 |
| `CLAUDE_CODE_MAX_WEB_SEARCHES_PER_SESSION` | Sets the per-session WebSearch limit; the default is 200 |
| `CLAUDE_CODE_MCP_AUTO_BACKGROUND_MS` | Sets when long MCP calls move to the background, or disables automatic backgrounding |
| `CLAUDE_CODE_MCP_TOOL_IDLE_TIMEOUT` | Overrides the idle timeout for remote MCP tool calls that stop responding |
| `CLAUDE_CODE_TOOL_MEMORY_LIMIT` | Sets an opt-in Linux memory-cgroup limit for Bash tool commands |
| `CLAUDE_CODE_WEBFETCH_CACHE_TTL_MS` | Sets the WebFetch session URL cache lifetime in milliseconds; the default is 15 minutes |
| `CLAUDE_CODE_WORKFLOW_PREFIX_STAGGER_MS=0` | Disables the default stagger between same-prefix sibling agents in workflow fan-outs |
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
| `CLAUDE_CODE_PROJECT_DIR_NAME` | With `CLAUDE_CONFIG_DIR`, chooses the directory name used for project transcripts and auto memory |
| `CLAUDE_CODE_RESTRICTED=1` | Enables the same restricted mode as `--restricted` |
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

An idle goal can start up to three background check-ins. Your next message allows three more.

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
/code-review ultra
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
| `/statusline` | Leak-based | Customize status line |
| `/summary` | Leak-based | Generate a session summary |
| `/tag` | Removed | Legacy tag command |
| `/terminalSetup` | Internal | Internal form of `/terminal-setup` |
| `/thinkback` | Internal / leak-based | Replay or analyze thinking |
| `/thinkback-play` | Internal / leak-based | Animated thinking replay |
| `/ultraplan` | Removed | Old detailed planning workflow |
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
- `/agents` opens the in-session subagent manager. `claude agents` is the separate terminal view for background Claude Code sessions.
- `/fork` creates a separate background session and worktree. `/subtask` starts a forked subagent that inherits the current conversation; fork mode is on by default in interactive sessions as of `v2.1.232`.
- `/review` is now an alias of `/code-review`; `/code-review ultra` runs a deep cloud review.
- `/ultraplan` was removed in `v2.1.222`.
- `sandbox.network.strictAllowlist` denies non-allowlisted hosts for sandboxed commands without prompting.
- Plugins can use an HTTPS zip `archive` source with optional SHA-256 pinning.
- Plugin marketplaces accept bare GitLab repository URLs. `additionalMarketplaces` and `allowedMarketplaces` are aliases for `extraKnownMarketplaces` and `strictKnownMarketplaces`.
- `CLAUDE_CODE_RETRY_WATCHDOG` raises the default retry count for non-capacity transient errors to 300 and removes the old cap of 15 on `CLAUDE_CODE_MAX_RETRIES`.
- `ANTHROPIC_DEFAULT_MODEL` sets the model used by new sessions; a `/model` pick still overrides it and persists across restarts.
- Claude Fable 5.1 is available as `claude-fable-5-1`. In Claude apps gateway sessions, the `fable` and `best` aliases still resolve to Fable 5 until the gateway supports the newer default, so select Fable 5.1 explicitly.
- The built-in `Concise` output style was added in `v2.1.237`. Select it under Output style in `/config`; it takes effect after `/clear` or in a new session.
- The `spellcheck` setting was added in `v2.1.235`, and `keybindingFlavor: "readline"` was added in `v2.1.238`. The latter makes `Ctrl+W` delete back to the previous whitespace.
- `selection:clear` is available as a keybinding action. `CLAUDE_CODE_GOAL_CHECKIN_MINUTES` controls the first background check-in for `/goal`; later checks back off from 30 minutes to 1 hour and then every 2 hours. An idle goal gets at most three check-ins until your next message, and `0` disables check-ins.
- `modelPicker` can append to or replace the built-in `/model` list with an ordered, labeled model list. `promptCacheTtl` and `subagentPromptCacheTtl` set prompt-cache lifetimes for the main conversation and subagents. Agent frontmatter can set `experimental.cacheTtl` to `"5m"` or `"1h"` when no subagent TTL setting applies.
- `timeFormat` and `timeZone` control the turn-end clock and transcript timestamps. Supported choices include 12-hour, 24-hour, UTC, and custom `strftime` formats.
- `permissions.blockReadsOutsideWorkingDirectories` blocks file reads outside the working directories after the first-read prompt. Project and local settings cannot set `defaultMode` to `auto` or `bypassPermissions`; use user or managed settings, or pass `--permission-mode`.
- `/effort` now saves a separate default for each model. Press `s` in its picker for a session-only choice; the `--effort` CLI flag is also session-only.
- `CLAUDE_CODE_SUBAGENT_MODEL` is a default that agent frontmatter and explicit per-spawn choices can override. Set `CLAUDE_CODE_SUBAGENT_MODEL_FORCE=1` when every subagent must use that model, or the main model if no subagent model is set.
- Managed deployments can set `modelPricing` so `/cost`, the status line, and telemetry use contracted model rates and an organization discount multiplier. US-only inference workspaces include the 1.1x data-residency premium in cost estimates.
- `/mcp` and `/plugins` mark claude.ai connectors whose authentication is managed by the organization. Cloud-synced plugins appear as `name@synced` and can be enabled or disabled with that identifier.
- `headersHelper` can generate short-lived MCP or plugin-marketplace headers. Catalog helpers run during install or update only after the command is shown, and `-y`/`--yes` skips the confirmation prompt for command-source plugins.
- On macOS, wildcard read-deny rules such as `**/.env` take precedence inside allowed read regions and cannot be bypassed by renaming a matched file.
- In fullscreen mode, `Ctrl+L` and `Cmd+K` now repaint the screen only; the old double-press `/clear` shortcut was removed.

---

## Sources

- [Claude Code changelog through `v2.1.258`](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
- [Claude Code `v2.1.257` release notes](https://github.com/anthropics/claude-code/releases/tag/v2.1.257)
- [Claude Code `v2.1.251` release notes](https://github.com/anthropics/claude-code/releases/tag/v2.1.251)
- [Official Claude Code command and CLI references](https://code.claude.com/docs/en/commands)
- Local command reference notes and leak-based command lists

---

## Related Resources

- [awesome-claude-code](https://github.com/jqueryscript/awesome-claude-code): curated tools, workflows, integrations, and resources for Claude Code users
- [Anthropic Agent SDK Slash Commands Docs](https://platform.claude.com/docs/en/agent-sdk/slash-commands): official slash command documentation
- [Claude Code Commands Cheat Sheet (Full Article)](https://www.scriptbyai.com/claude-code-commands-cheat-sheet/): expanded version with explanations and workflows
- [Best Agent Skills](https://www.scriptbyai.com/best-agent-skills/): useful skills for Claude Code and other AI coding workflows
- [AI Coding Agents](https://www.scriptbyai.com/best-cli-ai-coding-agents/): comparison of Claude Code and other CLI coding agents

*Last audited: September 2, 2026*

