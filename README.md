# Claude Code Slash Commands Cheatsheet

> **The most complete, verified reference for every Claude Code slash command — built-in, MCP-generated, and custom — updated for 2026.**

[![Verified](https://img.shields.io/badge/status-verified-brightgreen)](https://github.com/your-handle/claude-code-cheatsheet)
[![Commands](https://img.shields.io/badge/commands-50%2B-blue)](https://github.com/your-handle/claude-code-cheatsheet)
[![Updated](https://img.shields.io/badge/updated-March%202026-orange)](https://github.com/your-handle/claude-code-cheatsheet)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Table of Contents

- [What Is Claude Code?](#what-is-claude-code)
- [How Slash Commands Work](#how-slash-commands-work)
- [Session & Conversation Management](#-session--conversation-management)
- [Context & Cost](#-context--cost)
- [Project & Memory](#-project--memory)
- [Code Review & Analysis](#-code-review--analysis)
- [Model & Mode Control](#-model--mode-control)
- [System, Tools & Permissions](#-system-tools--permissions)
- [IDE, Integrations & Remote](#-ide-integrations--remote)
- [Appearance & UI](#-appearance--ui)
- [Info & Diagnostics](#-info--diagnostics)
- [MCP Server Commands](#-mcp-server-commands)
- [Custom Commands](#-custom-commands)
- [Custom Command Frontmatter Reference](#-custom-command-frontmatter-reference)
- [Community / Unofficial Commands](#-community--unofficial-commands)
- [Tips & Workflows](#-tips--workflows)
- [Contributing](#contributing)

---

## What Is Claude Code?

Claude Code is Anthropic's AI coding assistant, available as a CLI tool (`npm install -g @anthropic-ai/claude-code`). It runs an interactive agentic loop directly in your terminal — reading files, executing code, writing tests, and managing git workflows autonomously.

Slash commands are typed shortcuts that control session behavior, switch modes, manage context, and invoke external tools without interrupting your workflow.

---

## How Slash Commands Work

Type any command at the Claude Code prompt:

```
/compact keep only API implementation decisions
/model opus
/plan
```

**Autocomplete:** Type `/` and start typing to filter commands. Autocomplete works anywhere in the input line, not only at the start.

**Three command types:**

| Type | Source | Example |
|---|---|---|
| Built-in | Ships with Claude Code | `/compact`, `/plan`, `/doctor` |
| MCP-generated | Connected MCP servers | `/mcp__github__list_prs` |
| Custom | Your `.claude/commands/` or `.claude/skills/` | `/run-tests unit` |

---

## 💬 Session & Conversation Management

| Command | Syntax | Description |
|---|---|---|
| `/clear` | `/clear` | Wipes all messages from the current context window. File edits and permissions remain intact. |
| `/compact` | `/compact [instructions]` | Summarizes the conversation to free context, with optional focus guidance (e.g., `/compact keep only API decisions`). |
| `/resume` | `/resume [session]` | Reopens a previous session by its ID or name. Displays an interactive picker if no argument is provided. |
| `/rename` | `/rename <n>` | Assigns a human-readable name to the current session for easy retrieval with `/resume`. |
| `/export` | `/export [filename]` | Exports the full conversation as Markdown to a file or the clipboard. |
| `/rewind` | `/rewind` | Rolls back the conversation and/or file changes to a prior checkpoint. As of 2026, supports selective rollback of conversation only, file edits only, or both. |
| `/exit` | `/exit` | Ends the Claude Code session and returns to the shell. Equivalent to `Ctrl+D`. |
| `/copy` | `/copy` | Opens an interactive selector for copying specific code blocks to the clipboard. SSH-friendly — added in v2.1.59. |

> **When to use `/clear` vs `/compact`:** Use `/compact` to preserve partial context when switching subtasks within the same project. Use `/clear` for a complete reset before a fully unrelated task.

---

## 📊 Context & Cost

| Command | Syntax | Description |
|---|---|---|
| `/context` | `/context` | Shows a breakdown of context window usage across messages, files, and tool outputs. Also flags any Skills excluded due to budget limits. |
| `/cost` | `/cost` | Reports input and output token consumption for the current session with an estimated API cost. |
| `/stats` | `/stats` | Displays historical usage aggregated over time — daily session counts and token consumption. |
| `/usage` | `/usage` | Shows plan-level quota consumption and current rate limit status for your Anthropic account. |

> **Token budget tip:** Claude Code auto-compacts when context exceeds ~95%. Run `/context` at 80% usage to decide whether to compact manually with a custom focus instruction.

---

## 📁 Project & Memory

| Command | Syntax | Description |
|---|---|---|
| `/init` | `/init` | Generates a `CLAUDE.md` file in the project root by analyzing existing files, capturing architecture, conventions, and preferred tools. |
| `/memory` | `/memory` | Opens an editor-like view for reading and modifying all persistent memory files (CLAUDE.md and related). |
| `/todos` | `/todos` | Displays the structured TODO list Claude maintains during multi-step agentic tasks — pending, in-progress, and completed items. |

> **Quick memory shortcut:** Prefix any message with `#` to append a note to memory without opening `/memory`. Example: `# always use pnpm, never npm`.

---

## 🔍 Code Review & Analysis

| Command | Syntax | Description |
|---|---|---|
| `/review` | `/review` | Requests a full code review of the current branch's diff, covering quality, security, performance, and test coverage. |
| `/security-review` | `/security-review` | Runs a security-focused pass over pending changes, checking for SQLi, XSS, exposed credentials, and insecure configurations. |
| `/pr-comments` | `/pr-comments [identifier]` | Fetches pull request review comments for the current branch's open PR (or a specified PR number), then lets Claude implement fixes. |

---

## 🤖 Model & Mode Control

| Command | Syntax | Description |
|---|---|---|
| `/model` | `/model [name]` | Shows the active model or switches it. Accepts shorthand (`sonnet`, `opus`, `haiku`) or full model strings. |
| `/plan` | `/plan` | Toggles **plan permission mode** — Claude proposes each action and waits for your approval before executing any tool call. *Not* a plan-document generator. |
| `/effort` | `/effort [level]` | Sets the reasoning effort level: `low`, `medium`, `high`, or `auto`. Added in 2026; default is `medium` for Max/Team subscribers on Opus 4.6. |
| `/fast` | `/fast` | Toggles Fast Mode, running Opus 4.6 at approximately 2.5× throughput without downgrading to a smaller model. Added in 2026. |
| `/output-style` | `/output-style [style]` | Sets the default response format for the session (e.g., `concise`, `detailed`), reducing repeated formatting instructions. |

> **Effort tip:** Append `ultrathink` to any prompt to force `high` effort for that single turn without changing the global `/effort` setting.

---

## ⚙️ System, Tools & Permissions

| Command | Syntax | Description |
|---|---|---|
| `/permissions` | `/permissions` | Views and adjusts per-tool permissions for bash, file editing, and MCP tools, controlling which actions require explicit approval. |
| `/hooks` | `/hooks` | Opens the hook configuration manager. Hooks fire on lifecycle events (`PreToolUse`, `PostToolUse`, `Stop`, `InstructionsLoaded`, `WorktreeCreate`, `WorktreeRemove`) and can call shell commands, HTTP endpoints, or MCP tools. |
| `/sandbox` | `/sandbox` | Enables sandboxed bash execution, isolating shell commands from the host filesystem and network. |
| `/config` | `/config` | Opens the interactive settings interface for API keys, defaults, and integrations. |
| `/add-dir` | `/add-dir [path ...]` | Adds one or more directories to Claude's working scope for the current session, granting access to files outside the project root. |
| `/terminal-setup` | `/terminal-setup` | Installs the `Shift+Enter` keybinding for multi-line prompt entry. May modify `.zshrc`/`.bashrc` with consent. |
| `/keybindings` | `/keybindings` | Opens `~/.claude/keybindings.json` for full keyboard shortcut customization. Added in 2026. |
| `/login` | `/login` | Authenticates or switches the Anthropic account (equivalent to `claude auth login`). |
| `/logout` | `/logout` | Signs out and clears stored credentials (equivalent to `claude auth logout`). |

---

## 🔗 IDE, Integrations & Remote

| Command | Syntax | Description |
|---|---|---|
| `/ide` | `/ide` | Displays connected IDE integrations (VS Code, JetBrains) and provides setup guidance for Claude Code plugins. |
| `/mcp` | `/mcp` | Opens the MCP server manager for viewing, connecting, and configuring external tool servers. Each connected server exposes its prompts as `/mcp__<server>__<prompt>` commands. |
| `/install-github-app` | `/install-github-app` | Launches the setup flow for the Claude GitHub App and GitHub Actions CI/CD integration. |
| `/pr-comments` | `/pr-comments [identifier]` | See Code Review section above. |
| `/teleport` | `/teleport` | Bridges a `claude.ai` web session to the local terminal, attaching CLI access to a remotely started session. |
| `/rc` | `/rc` | Starts a Remote Control session for supervising long-running agentic tasks from a mobile device. Added in 2026. Equivalent to `claude rc`. |
| `/remote-env` | `/remote-env` | Configures environment settings for remote containers or cloud development servers. |
| `/agents` | `/agents` | Lists and manages configured AI subagents for the session. |
| `/plugin` | `/plugin` | Opens the plugin marketplace manager for listing, installing, and configuring Claude Code plugins. |

---

## 🎨 Appearance & UI

| Command | Syntax | Description |
|---|---|---|
| `/theme` | `/theme` | Presents available terminal UI color themes and applies the selected one immediately. |
| `/vim` | `/vim` | Enables vim-style modal editing in the Claude Code input field (normal/insert/visual modes). |
| `/statusline` | `/statusline` | Configures which indicators appear in the persistent status bar at the bottom of the terminal UI. |

---

## ℹ️ Info & Diagnostics

| Command | Syntax | Description |
|---|---|---|
| `/help` | `/help` | Lists all available built-in and custom slash commands with descriptions, including MCP and `.claude/commands/` commands. |
| `/doctor` | `/doctor` | Runs active environment health checks: API key validity, network connectivity, Node.js version, and dependencies. Run after installation or upgrades. |
| `/status` | `/status` | Displays a summary of current configuration: active model, permission mode, connected MCP servers, and tool state. |
| `/release-notes` | `/release-notes` | Shows the recent Claude Code changelog, including new commands and behavior changes. |
| `/privacy-settings` | `/privacy-settings` | Opens privacy configuration — telemetry controls and data sharing preferences. |
| `/bug` | `/bug [description]` | Submits a bug report to Anthropic with collected session logs and context. |

---

## 🔌 MCP Server Commands

MCP (Model Context Protocol) servers expose their prompts as dynamically generated slash commands using the pattern:

```
/mcp__<server-name>__<prompt-name> [arguments]
```

**Examples:**

```bash
/mcp__github__list_prs
/mcp__github__create_pr "Add dark mode" main feature/dark-mode
/mcp__jira__create_issue "Bug: auth fails on mobile" high
/mcp__linear__get_sprint
```

Use `/mcp` to see all connected servers and their available commands. Commands update live as servers are connected or disconnected.

---

## 🛠 Custom Commands

Custom commands let you encode reusable workflows as Markdown files. Two locations:

| Scope | Legacy path | Recommended path |
|---|---|---|
| Project (shared via git) | `.claude/commands/<name>.md` | `.claude/skills/<name>/SKILL.md` |
| Personal (all projects) | `~/.claude/commands/<name>.md` | `~/.claude/skills/<name>/SKILL.md` |

> **Note:** The `.claude/skills/` format is the **current recommended approach** (supports multi-file skills and autonomous Claude invocation). The `.claude/commands/` legacy format continues to work.

### Minimal example

Create `.claude/commands/optimize.md`:

```
Analyze the following code for performance bottlenecks and suggest targeted improvements.
```

Invoke as `/optimize`.

### With arguments

`$ARGUMENTS` captures all trailing text as a single string. `$1`, `$2`, etc. capture positional arguments.

```
Fix issue #$1 with priority $2.
```

`/fix-issue 123 high` → `$1 = 123`, `$2 = high`

### Embedding live context

Prefix shell commands with `!` to execute before the model runs and inject output into the prompt:

```
## Current git status
!`git status`

## Staged changes
!`git diff --staged`

Create a commit message for the above changes.
```

Reference file contents with the `@` prefix:

```
Review @src/auth/login.ts against the requirements in @docs/auth-spec.md.
```

### Practical starter commands

The three examples below are ready to copy into your `.claude/commands/` directory.

#### `/smart-commit` — Sanity-checked git commit

Create `.claude/commands/smart-commit.md`:

```
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*)
argument-hint: [message]
description: Run pre-commit checks then commit with the provided message
model: haiku

Before committing, verify there are no TODO comments, console.log statements,
or commented-out code blocks in the changed files.

If clean, commit with: $ARGUMENTS
If issues found, list them and ask whether to proceed.
```

#### `/pr-review` — Comprehensive pull request review

Create `.claude/commands/pr-review.md`:

```
allowed-tools: Read, Grep, Glob, Bash(git diff:*)
description: Full code review of the current branch's changes

## Changed files
!`git diff --name-only HEAD~1`

## Diff
!`git diff HEAD~1`

Review the above for: code quality, security vulnerabilities,
performance implications, test coverage, and documentation completeness.
Provide specific, actionable feedback ordered by priority.
```

#### `/run-tests` — Framework-aware test runner

Create `.claude/commands/run-tests.md`:

```
allowed-tools: Bash, Read, Edit
argument-hint: [pattern]
description: Detect the test framework and run tests matching the given pattern

Run tests matching: $ARGUMENTS

1. Detect the test framework (Jest, Vitest, pytest, etc.)
2. Run tests with the provided pattern
3. If failures occur, analyze root cause and fix
4. Re-run to verify the fix
```

---

## 📋 Custom Command Frontmatter Reference

Add a YAML block at the top of any command file to control its behavior:

```yaml
allowed-tools: Read, Edit, Write, Bash(git:*)
argument-hint: [required-arg] [optional-arg]
description: Brief description shown in /help
model: claude-opus-4-6
context: inline | fork
agent: my-agent-name
disable-model-invocation: true | false
hooks:
  PreToolUse:
    - matcher: "Bash"
      hooks:
        - type: command
          command: "./scripts/validate.sh"
          once: true
```

| Field | Description |
|---|---|
| `allowed-tools` | Tools this command can use without extra permission prompts. Supports scoped bash: `Bash(git add:*)`. |
| `argument-hint` | Usage hint shown in `/help` output (e.g., `[issue-number] [priority]`). |
| `description` | Human-readable description visible in `/help` and autocomplete. |
| `model` | Model to run this command with. Use `haiku` for fast, lightweight tasks. |
| `context` | `inline` runs in the current conversation; `fork` spawns an isolated subagent with its own context window. |
| `agent` | Agent persona name when using `fork` context. |
| `disable-model-invocation` | Set to `true` to prevent Claude from calling this command autonomously via the Skills system. |
| `hooks` | Event handlers scoped to this command's execution lifecycle. |

**Variable substitution inside command files:**

| Variable | Behavior |
|---|---|
| `$ARGUMENTS` | All trailing text passed to the command as a single string |
| `$1`, `$2`, ... | Positional arguments (space-separated) |
| `` !`shell command` `` | Executes before the model runs and injects the output into the prompt |
| `@path/to/file` | Injects the file's contents into the prompt |

---

## ⚠️ Community / Unofficial Commands

These commands appear frequently in tutorials, blog posts, and community repos. They are **user-defined custom commands, not built-ins** — your installation will not have them unless your project's `.claude/commands/` directory defines them.

| Command | Typical implementation |
|---|---|
| `/commit` | Runs `git status` + `git diff`, generates a commit message, then commits |
| `/push` | Detects the current branch and runs `git push` |
| `/branch` | Creates a new git branch from a plain-text description |
| `/lint` | Runs ESLint, Prettier, or Ruff based on the detected project type |
| `/vitest` | Runs Vitest with an optional test pattern argument |
| `/pr` | Opens a GitHub pull request via the `gh` CLI |
| `/merge-to-main` | Merge + push workflow with pre-merge checks |
| `/fix-pipeline` | Fetches recent CI failure logs and attempts a fix |

Community command collections worth exploring:
- [wshobson/commands](https://github.com/wshobson/commands)
- [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)

---

## 💡 Tips & Workflows

**Starting a session effectively**

```
/init          # generate CLAUDE.md on first use in a repo
/doctor        # verify environment after installation
/status        # confirm model and permission mode
```

**Managing long sessions**

```
/context       # check what is consuming your context budget
/compact keep only the database schema decisions
/cost          # estimate spend before continuing heavy work
```

**Before opening a pull request**

```
/review
/security-review
/pr-comments   # pull in any existing review comments to address
```

**Switching between tasks**

```
/rename feature-x-refactor     # name the current session
/clear                         # start fresh for a different task
/resume feature-x-refactor     # come back to the original later
```

**Effort and speed control (2026)**

```
/effort low     # fast iteration, reduced cost
/fast           # Opus 4.6 at 2.5x speed
/effort high    # or append "ultrathink" to any single prompt
```

---

## Contributing

Corrections, additions, and version-specific updates are welcome.

1. Fork this repo
2. Edit the relevant section in `README.md`
3. Include the version number or source where possible
4. Open a pull request with a brief description

Please do not add unofficial community commands to the built-in tables — keep them in the Community section with a note about their nature.

---

## Sources

- [Slash Commands in the Agent SDK — Anthropic Docs](https://platform.claude.com/docs/en/agent-sdk/slash-commands)
- [SmartScope Claude Code Reference Guide 2026](https://smartscope.blog/en/generative-ai/claude/claude-code-reference-guide/)
- [prg.sh — Claude Code Slash Commands (Jan 2026)](https://prg.sh/notes/Claude-Code-Slash-Commands)
- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)

---

*Last audited: March 2026 · Verified against Claude Code v2.1.63+*
