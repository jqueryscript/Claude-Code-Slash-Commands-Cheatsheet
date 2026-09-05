# Claude Code Commands Cheat Sheet

A comprehensive GitHub reference for Claude Code slash commands, CLI commands, flags, keyboard shortcuts, MCP commands, skills, environment variables, removed command names, and common workflows.

[![PDF](https://img.shields.io/badge/PDF-Download-red)](./claude-code-commands-cheat-sheet.pdf) [![Web Reference](https://img.shields.io/badge/Web-ScriptByAI.com-blue)](https://www.scriptbyai.com/claude-code-commands-cheat-sheet/) [![Claude Code Releases](https://img.shields.io/badge/Claude%20Code-Releases-black)](https://github.com/anthropics/claude-code/releases)

This README is the full GitHub reference. The PDF provides a printable format, and the [web version](https://www.scriptbyai.com/claude-code-commands-cheat-sheet/) provides the same maintained reference in a browser-friendly layout.

> Type `/` on an empty prompt inside Claude Code to see the commands available in your installation. Availability can vary by platform, plan, provider, enabled features, plugins, MCP servers, and organization policy.

## Contents

- [Quick Reference](#quick-reference)
- [Slash Commands A-Z](#slash-commands-a-z)
- [Slash Commands by Task](#slash-commands-by-task)
  - [Start and Configure Claude Code](#start-and-configure-claude-code)
  - [Manage Context and Sessions](#manage-context-and-sessions)
  - [MCP, Plugins, Skills, and Agents](#mcp-plugins-skills-and-agents)
  - [Review, Debug, and Change Code](#review-debug-and-change-code)
  - [GitHub, PR, and Release Workflows](#github-pr-and-release-workflows)
  - [Remote and Cross-Device Commands](#remote-and-cross-device-commands)
  - [Usage, Diagnostics, and Account Commands](#usage-diagnostics-and-account-commands)
  - [Interface and Utility Commands](#interface-and-utility-commands)
- [MCP Slash Commands and Custom Commands](#mcp-slash-commands-and-custom-commands)
- [Claude Code CLI Commands](#claude-code-cli-commands)
- [Claude Code CLI Flags](#claude-code-cli-flags)
- [Claude Code Keyboard Shortcuts](#claude-code-keyboard-shortcuts)
- [Claude Code Environment Variables](#claude-code-environment-variables)
- [Older, Removed, and Replaced Command Names](#older-removed-and-replaced-command-names)
- [Common Workflows](#common-workflows)
- [Custom, Community, and Internal Command Names](#custom-community-and-internal-command-names)
- [FAQ](#faq)
- [Related Resources](#related-resources)

## Quick Reference

Claude Code has two command surfaces. Slash commands run inside an active Claude Code session. CLI commands and flags run from your shell.

### Common Claude Code Commands

| Command | What it does |
| --- | --- |
| **/help** | Show help and commands available in your installation. |
| **/init** | Create a starter CLAUDE.md for the current project. |
| **/model [model]** | Switch the active model. |
| **/plan [description]** | Enter Plan Mode for a task. |
| **/context [all]** | Inspect current context usage. |
| **/compact [instructions]** | Free context by summarizing the conversation. |
| **/clear [name]** | Start a fresh conversation. |
| **/resume [session]** | Return to an earlier conversation. |
| **/diff** | Review working-tree changes. |
| **/code-review [level] [target]** | Review a diff, branch, path, or pull request. |
| **/permissions** | Manage tool permission rules. |
| **/mcp [subcommand]** | Manage MCP servers and authentication. |
| **/skills** | Browse available skills. |
| **/tasks** | View background work in the current session. |
| **/doctor** | Diagnose setup and configuration issues. |

### Slash Commands vs. CLI Commands

Slash commands run inside an active Claude Code session. CLI commands and flags run in your shell before or while starting Claude Code.

| Where you run it | Examples |
| --- | --- |
| **Inside Claude Code** | **/compact**, **/model**, **/mcp**, **/doctor** |
| **In your terminal** | **claude -p "prompt"**, **claude -c**, **claude update**, **claude --model sonnet** |

## Slash Commands A-Z

The main A-Z table contains current built-in slash commands. If a command appears here, it is intended to be available in current Claude Code installations where the relevant feature, plan, provider, or policy permits it.

This A-Z index lists the current built-in commands, bundled skills, and bundled workflows. If a command appears here, it is part of the current Claude Code command reference, though account, platform, provider, or policy restrictions can hide individual commands in a particular installation.

| Command | What it does |
| --- | --- |
| **/add-dir <path>** | Add another working directory to the current session. |
| **/advisor [model|off]** | Turn the advisor tool on or off, optionally choosing its model. |
| **/agents** | Point you to Claude-managed subagent creation or the agent files in `.claude/agents/` and `~/.claude/agents/`. |
| **/artifacts** | List, attach, open, or copy links to available artifacts. |
| **/auto-mode-setup** | Draft auto-mode environment rules from the project and recent sessions. |
| **/autocompact [auto|<tokens>]** | Set the auto-compact window with **auto** or a token value such as **500k**; the choice is saved to settings. |
| **/autofix-pr [prompt]** | Start a Claude Code web session that watches the current branch’s PR and pushes fixes for CI failures or review comments; an optional prompt can narrow the work. |
| **/background [prompt]** | Detach the current session and keep it running as a background agent. Alias: /bg. |
| **/batch <instruction>** | Break a large codebase change into parallel worktree tasks. |
| **/branch [name]** | Branch the current conversation so you can try a different direction. |
| **/btw [question]** | Ask a side question about the current session without adding it to the main conversation history; run it with no question to revisit recent side questions. |
| **/bug [report]** | Report a bug or share selected session context. Alias: /share. |
| **/cd <path>** | Move the current session to another working directory without losing the conversation. |
| **/chrome** | Configure Claude in Chrome integration. |
| **/claude-api [subcommand]** | Load Claude API and Managed Agents guidance, including migration and audit workflows. |
| **/clear [name]** | Start a new conversation with empty conversational context while keeping project memory; an optional name labels the previous conversation for later resume. |
| **/code-review [level] [--fix] [--comment] [target]** | Review the current diff or a path, branch, or PR. Use **--fix** to apply findings, **--comment** for PR comments, or **ultra** for the cloud review flow. |
| **/color [color|default]** | Change the prompt bar color for the current session. |
| **/compact [instructions]** | Summarize the conversation to free context while keeping the current task. |
| **/config [key=value ...]** | Open the Settings interface, or pass supported **key=value** pairs to change settings directly. |
| **/context [all]** | Show context usage, capacity warnings, and optimization suggestions; pass **all** to expand the per-item breakdown. |
| **/copy [N]** | Copy the latest response or the Nth-latest response; when code blocks exist, the picker can copy an individual block or the full response. |
| **/cost** | Open the Usage view. Alias of /usage. |
| **/dataviz [request]** | Load bundled chart, graph, and dashboard design guidance. |
| **/debug [description]** | Enable session debug logging and investigate a runtime problem. |
| **/deep-research <question>** | Run a multi-source research workflow and synthesize a cited report. |
| **/design [brief]** | Create UI or graphic design artboards and publish them as an artifact where available. |
| **/design-login** | Authorize access used by design-system synchronization. |
| **/design-sync [hint]** | Sync a React design system for use with Claude Design. |
| **/desktop** | Continue the current session in the Claude Code Desktop app. Alias: /app. |
| **/diff** | Review working-tree changes, including edits made by Claude. |
| **/doctor** | Run a setup checkup for installation, settings, hooks, skills, plugins, MCP servers, and context overhead, with fixes offered where available. |
| **/effort [level|auto|status]** | Set or inspect reasoning effort with model-appropriate levels, **auto**, or **status**. |
| **/exit** | Exit Claude Code; in an attached background session, detach without stopping it. Alias: /quit. |
| **/export [filename]** | Export the current conversation as plain text. |
| **/fast [on|off]** | Turn fast mode on or off. |
| **/feedback [report]** | Send product feedback or review queued feedback drafts. |
| **/fewer-permission-prompts** | Find common read-only tool calls and propose permission allowlist entries. |
| **/focus** | Toggle the compact Focus view in fullscreen mode. |
| **/fork [prompt]** | Copy the current conversation into a separate background session while you keep working in the original session. |
| **/goal [condition|clear]** | Set a completion condition that keeps Claude working across turns until the condition is met, or clear the active goal. |
| **/heapdump** | Write heap diagnostics for investigating high memory use. |
| **/help** | Show help and the commands available in the current installation. |
| **/hooks** | View configured hook events and commands. |
| **/ide** | Manage IDE integrations and connection status. |
| **/import [codex|gemini] [--dry-run] [--yes]** | Import supported configuration from Codex or Gemini CLI. |
| **/init** | Create or initialize CLAUDE.md project guidance. |
| **/insights** | Generate an HTML report from recent local Claude Code usage. |
| **/install-github-app** | Set up the Claude GitHub App and optional GitHub Actions workflow. |
| **/install-slack-app** | Open the Slack app installation flow. |
| **/keybindings** | Open the custom keyboard-shortcuts configuration file. |
| **/list-agents** | List subagents, agent-team teammates, and other messageable Claude Code sessions. Alias: /peers. |
| **/login** | Sign in to an Anthropic account. |
| **/logout** | Sign out from the current Anthropic account. |
| **/loop [interval] [prompt]** | Repeat a prompt while the session stays open. Alias: /proactive. |
| **/mcp [subcommand]** | Open MCP management, authenticate servers, reconnect a server, or enable and disable individual servers or all servers. |
| **/memory** | Edit CLAUDE.md files and manage auto memory. |
| **/mobile** | Show a QR code for the Claude mobile app. Aliases: /ios, /android. |
| **/model [model]** | Switch the active model; the picker can save a default for new sessions or apply a model only to the current session. |
| **/passes** | Share a free week of Claude Code with friends when the account is eligible. |
| **/permissions** | Manage allow, ask, and deny rules, working directories, recent denials, and auto-mode classifier rules. |
| **/plan [description]** | Enter Plan Mode, optionally starting with a task description. |
| **/plugin [subcommand]** | Open plugin management or run plugin subcommands such as **list**, **install**, **enable**, and **disable**. |
| **/powerup** | Open interactive lessons for Claude Code features. |
| **/privacy-settings** | View and update privacy settings on eligible plans. |
| **/radio** | Open Claude FM lo-fi radio. |
| **/rate-limit-options** | Show options for continuing when a Claude.ai usage limit blocks a request. |
| **/recap** | Generate a one-line summary of the current session. |
| **/release-notes** | Open the interactive Claude Code changelog. |
| **/reload-plugins [--force]** | Reload active plugin components without restarting Claude Code; **--force** permits reloads that would change MCP tools and invalidate prompt cache. |
| **/reload-skills** | Re-scan skill and command directories during the current session and report which skills were added or removed. |
| **/remote-control** | Make the local session available from claude.ai or the Claude app through Remote Control. Alias: **/rc**. |
| **/remote-env** | Choose the default environment for cloud agents. |
| **/rename [name]** | Rename the current session. |
| **/resume [session]** | Resume a previous conversation by ID or name, or open the session picker. Alias: /continue. |
| **/review [level] [--fix] [--comment] [target]** | Alias of /code-review. |
| **/rewind** | Restore or summarize an earlier checkpoint. Aliases: /checkpoint, /undo. |
| **/run** | Build and run the project so Claude can observe a change working. |
| **/run-skill-generator** | Create project guidance that teaches /run and /verify how to launch the app. |
| **/sandbox** | Toggle sandbox mode on supported platforms. |
| **/schedule [description]** | Create, update, list, or run cloud routines. Alias: /routines. |
| **/scroll-speed** | Adjust mouse-wheel speed in fullscreen mode. |
| **/security-review** | Review the current branch against the origin default branch for security issues such as injection, authentication flaws, and data exposure. |
| **/setup-bedrock** | Open the Amazon Bedrock setup wizard. |
| **/setup-vertex** | Open the Google Cloud Agent Platform setup wizard. |
| **/simplify [target]** | Review changed code for reuse, simplicity, efficiency, and abstraction issues, then apply cleanup fixes; use code review when you want correctness bugs checked too. |
| **/skill-doctor** | Show each skill’s context cost and usage frequency to identify skills that consume context without being used. |
| **/skills** | List skills, filter by name, description, or source, sort by token count, and manage visibility where the skill can be toggled. |
| **/stats** | Open the Stats tab in /usage. |
| **/status** | Show version, model, account, connectivity, and session status. |
| **/statusline** | Configure the custom status line. |
| **/stickers** | Open the Claude Code sticker-ordering flow. |
| **/stop** | Stop the current attached background session while keeping its transcript and worktree. |
| **/subtask <task>** | Start a forked subagent that inherits the current conversation, works in the background, and reports its result back to this session. |
| **/tasks** | View and manage background work in the current session. Alias: /bashes. |
| **/team-onboarding** | Generate a team onboarding guide from recent Claude Code usage. |
| **/teleport** | Pull a Claude Code web session and its conversation into the local terminal. Alias: **/tp**. |
| **/terminal-setup** | Configure supported terminals for multiline input and related integration settings. |
| **/theme** | Choose or create a terminal color theme. |
| **/tui [default|fullscreen]** | Switch between the standard and fullscreen terminal renderers. |
| **/ultrareview [PR or branch]** | Run the deep cloud review flow. /code-review ultra is the preferred form. |
| **/upgrade** | Open the plan upgrade flow. |
| **/usage** | Show session cost, plan usage limits, and activity statistics; **/cost** and **/stats** open views within the same usage surface. |
| **/usage-credits** | Open or request usage-credit settings when a limit is reached. |
| **/verify** | Build and run the project to confirm a code change works in the actual app. |
| **/voice [hold|tap|off]** | Turn voice dictation on, choose hold/tap behavior, or turn it off. |
| **/web-setup** | Connect GitHub credentials for Claude Code on the web. |
| **/workflow-authoring** | Load the reference for creating or editing dynamic workflow scripts. |
| **/workflows** | Open the workflow progress view to watch and manage workflow runs. |

**Download the Claude Code Commands Cheat Sheet**

Save or print the PDF version for a compact offline reference. The web version below is the fuller reference and is updated as Claude Code changes.

[Download PDF](https://raw.githubusercontent.com/jqueryscript/Claude-Code-Slash-Commands-Cheatsheet/main/claude-code-commands-cheat-sheet.pdf)

## Slash Commands by Task

The A-Z index is best when you already know the command name. The task sections below group the same current commands by what you are trying to do.

### Start and Configure Claude Code

Use these commands for initial project setup, model and permission choices, terminal configuration, memory, providers, and session-wide settings.

| Command | What it does |
| --- | --- |
| **/add-dir <path>** | Add another working directory to the current session. |
| **/auto-mode-setup** | Draft auto-mode environment rules from the project and recent sessions. |
| **/autocompact [auto|<tokens>]** | Set the auto-compact window with **auto** or a token value such as **500k**; the choice is saved to settings. |
| **/cd <path>** | Move the current session to another working directory without losing the conversation. |
| **/color [color|default]** | Change the prompt bar color for the current session. |
| **/config [key=value ...]** | Open the Settings interface, or pass supported **key=value** pairs to change settings directly. |
| **/doctor** | Run a setup checkup for installation, settings, hooks, skills, plugins, MCP servers, and context overhead, with fixes offered where available. |
| **/effort [level|auto|status]** | Set or inspect reasoning effort with model-appropriate levels, **auto**, or **status**. |
| **/fast [on|off]** | Turn fast mode on or off. |
| **/help** | Show help and the commands available in the current installation. |
| **/hooks** | View configured hook events and commands. |
| **/ide** | Manage IDE integrations and connection status. |
| **/import [codex|gemini] [--dry-run] [--yes]** | Import supported configuration from Codex or Gemini CLI. |
| **/init** | Create or initialize CLAUDE.md project guidance. |
| **/keybindings** | Open the custom keyboard-shortcuts configuration file. |
| **/login** | Sign in to an Anthropic account. |
| **/logout** | Sign out from the current Anthropic account. |
| **/memory** | Edit CLAUDE.md files and manage auto memory. |
| **/model [model]** | Switch the active model; the picker can save a default for new sessions or apply a model only to the current session. |
| **/permissions** | Manage allow, ask, and deny rules, working directories, recent denials, and auto-mode classifier rules. |
| **/privacy-settings** | View and update privacy settings on eligible plans. |
| **/sandbox** | Toggle sandbox mode on supported platforms. |
| **/setup-bedrock** | Open the Amazon Bedrock setup wizard. |
| **/setup-vertex** | Open the Google Cloud Agent Platform setup wizard. |
| **/statusline** | Configure the custom status line. |
| **/terminal-setup** | Configure supported terminals for multiline input and related integration settings. |
| **/theme** | Choose or create a terminal color theme. |
| **/tui [default|fullscreen]** | Switch between the standard and fullscreen terminal renderers. |
| **/upgrade** | Open the plan upgrade flow. |

### Manage Context and Sessions

These commands manage context size, conversation state, checkpoints, background work, session naming, and session history.

| Command | What it does |
| --- | --- |
| **/background [prompt]** | Detach the current session and keep it running as a background agent. Alias: /bg. |
| **/branch [name]** | Branch the current conversation so you can try a different direction. |
| **/btw [question]** | Ask a side question about the current session without adding it to the main conversation history; run it with no question to revisit recent side questions. |
| **/clear [name]** | Start a new conversation with empty conversational context while keeping project memory; an optional name labels the previous conversation for later resume. |
| **/compact [instructions]** | Summarize the conversation to free context while keeping the current task. |
| **/context [all]** | Show context usage, capacity warnings, and optimization suggestions; pass **all** to expand the per-item breakdown. |
| **/copy [N]** | Copy the latest response or the Nth-latest response; when code blocks exist, the picker can copy an individual block or the full response. |
| **/cost** | Open the Usage view. Alias of /usage. |
| **/export [filename]** | Export the current conversation as plain text. |
| **/focus** | Toggle the compact Focus view in fullscreen mode. |
| **/fork [prompt]** | Copy the current conversation into a separate background session while you keep working in the original session. |
| **/goal [condition|clear]** | Set a completion condition that keeps Claude working across turns until the condition is met, or clear the active goal. |
| **/recap** | Generate a one-line summary of the current session. |
| **/rename [name]** | Rename the current session. |
| **/resume [session]** | Resume a previous conversation by ID or name, or open the session picker. Alias: /continue. |
| **/rewind** | Restore or summarize an earlier checkpoint. Aliases: /checkpoint, /undo. |
| **/stats** | Open the Stats tab in /usage. |
| **/status** | Show version, model, account, connectivity, and session status. |
| **/stop** | Stop the current attached background session while keeping its transcript and worktree. |
| **/subtask <task>** | Start a forked subagent that inherits the current conversation, works in the background, and reports its result back to this session. |
| **/tasks** | View and manage background work in the current session. Alias: /bashes. |
| **/usage** | Show session cost, plan usage limits, and activity statistics; **/cost** and **/stats** open views within the same usage surface. |

### MCP, Plugins, Skills, and Agents

Use these commands to extend Claude Code with MCP servers, plugins, skills, subagents, background work, and dynamic workflows.

| Command | What it does |
| --- | --- |
| **/agents** | Point you to Claude-managed subagent creation or the agent files in `.claude/agents/` and `~/.claude/agents/`. |
| **/batch <instruction>** | Break a large codebase change into parallel worktree tasks. |
| **/claude-api [subcommand]** | Load Claude API and Managed Agents guidance, including migration and audit workflows. |
| **/dataviz [request]** | Load bundled chart, graph, and dashboard design guidance. |
| **/deep-research <question>** | Run a multi-source research workflow and synthesize a cited report. |
| **/fewer-permission-prompts** | Find common read-only tool calls and propose permission allowlist entries. |
| **/list-agents** | List subagents, agent-team teammates, and other messageable Claude Code sessions. Alias: /peers. |
| **/loop [interval] [prompt]** | Repeat a prompt while the session stays open. Alias: /proactive. |
| **/mcp [subcommand]** | Open MCP management, authenticate servers, reconnect a server, or enable and disable individual servers or all servers. |
| **/plugin [subcommand]** | Open plugin management or run plugin subcommands such as **list**, **install**, **enable**, and **disable**. |
| **/reload-plugins [--force]** | Reload active plugin components without restarting Claude Code; **--force** permits reloads that would change MCP tools and invalidate prompt cache. |
| **/reload-skills** | Re-scan skill and command directories during the current session and report which skills were added or removed. |
| **/run-skill-generator** | Create project guidance that teaches /run and /verify how to launch the app. |
| **/skill-doctor** | Show each skill’s context cost and usage frequency to identify skills that consume context without being used. |
| **/skills** | List skills, filter by name, description, or source, sort by token count, and manage visibility where the skill can be toggled. |
| **/subtask <task>** | Start a forked subagent that inherits the current conversation, works in the background, and reports its result back to this session. |
| **/workflow-authoring** | Load the reference for creating or editing dynamic workflow scripts. |
| **/workflows** | Open the workflow progress view to watch and manage workflow runs. |

### Review, Debug, and Change Code

These commands help plan changes, inspect diffs, review code, debug failures, verify behavior, and run larger changes in parallel.

| Command | What it does |
| --- | --- |
| **/advisor [model|off]** | Turn the advisor tool on or off, optionally choosing its model. |
| **/autofix-pr [prompt]** | Start a Claude Code web session that watches the current branch’s PR and pushes fixes for CI failures or review comments; an optional prompt can narrow the work. |
| **/batch <instruction>** | Break a large codebase change into parallel worktree tasks. |
| **/code-review [level] [--fix] [--comment] [target]** | Review the current diff or a path, branch, or PR. Use **--fix** to apply findings, **--comment** for PR comments, or **ultra** for the cloud review flow. |
| **/debug [description]** | Enable session debug logging and investigate a runtime problem. |
| **/diff** | Review working-tree changes, including edits made by Claude. |
| **/plan [description]** | Enter Plan Mode, optionally starting with a task description. |
| **/review [level] [--fix] [--comment] [target]** | Alias of /code-review. |
| **/run** | Build and run the project so Claude can observe a change working. |
| **/security-review** | Review the current branch against the origin default branch for security issues such as injection, authentication flaws, and data exposure. |
| **/simplify [target]** | Review changed code for reuse, simplicity, efficiency, and abstraction issues, then apply cleanup fixes; use code review when you want correctness bugs checked too. |
| **/ultrareview [PR or branch]** | Run the deep cloud review flow. /code-review ultra is the preferred form. |
| **/verify** | Build and run the project to confirm a code change works in the actual app. |

### GitHub, PR, and Release Workflows

These commands handle pull-request review, GitHub integration, cloud autofix work, release notes, and web-session setup.

| Command | What it does |
| --- | --- |
| **/autofix-pr [prompt]** | Start a Claude Code web session that watches the current branch’s PR and pushes fixes for CI failures or review comments; an optional prompt can narrow the work. |
| **/code-review [level] [--fix] [--comment] [target]** | Review the current diff or a path, branch, or PR. Use **--fix** to apply findings, **--comment** for PR comments, or **ultra** for the cloud review flow. |
| **/install-github-app** | Set up the Claude GitHub App and optional GitHub Actions workflow. |
| **/release-notes** | Open the interactive Claude Code changelog. |
| **/review [level] [--fix] [--comment] [target]** | Alias of /code-review. |
| **/security-review** | Review the current branch against the origin default branch for security issues such as injection, authentication flaws, and data exposure. |
| **/ultrareview [PR or branch]** | Run the deep cloud review flow. /code-review ultra is the preferred form. |
| **/web-setup** | Connect GitHub credentials for Claude Code on the web. |

### Remote and Cross-Device Commands

Use these commands for desktop, browser, mobile, Remote Control, cloud environments, artifacts, voice, and web-session handoff.

| Command | What it does |
| --- | --- |
| **/artifacts** | List, attach, open, or copy links to available artifacts. |
| **/background [prompt]** | Detach the current session and keep it running as a background agent. Alias: /bg. |
| **/chrome** | Configure Claude in Chrome integration. |
| **/desktop** | Continue the current session in the Claude Code Desktop app. Alias: /app. |
| **/design [brief]** | Create UI or graphic design artboards and publish them as an artifact where available. |
| **/design-login** | Authorize access used by design-system synchronization. |
| **/design-sync [hint]** | Sync a React design system for use with Claude Design. |
| **/install-slack-app** | Open the Slack app installation flow. |
| **/mobile** | Show a QR code for the Claude mobile app. Aliases: /ios, /android. |
| **/remote-control** | Make the local session available from claude.ai or the Claude app through Remote Control. Alias: **/rc**. |
| **/remote-env** | Choose the default environment for cloud agents. |
| **/schedule [description]** | Create, update, list, or run cloud routines. Alias: /routines. |
| **/teleport** | Pull a Claude Code web session and its conversation into the local terminal. Alias: **/tp**. |
| **/voice [hold|tap|off]** | Turn voice dictation on, choose hold/tap behavior, or turn it off. |
| **/web-setup** | Connect GitHub credentials for Claude Code on the web. |

### Usage, Diagnostics, and Account Commands

Use these commands to inspect usage, diagnose problems, report issues, review activity, and manage plan or credit options.

| Command | What it does |
| --- | --- |
| **/bug [report]** | Report a bug or share selected session context. Alias: /share. |
| **/cost** | Open the Usage view. Alias of /usage. |
| **/debug [description]** | Enable session debug logging and investigate a runtime problem. |
| **/doctor** | Run a setup checkup for installation, settings, hooks, skills, plugins, MCP servers, and context overhead, with fixes offered where available. |
| **/feedback [report]** | Send product feedback or review queued feedback drafts. |
| **/heapdump** | Write heap diagnostics for investigating high memory use. |
| **/insights** | Generate an HTML report from recent local Claude Code usage. |
| **/passes** | Share a free week of Claude Code with friends when the account is eligible. |
| **/powerup** | Open interactive lessons for Claude Code features. |
| **/rate-limit-options** | Show options for continuing when a Claude.ai usage limit blocks a request. |
| **/recap** | Generate a one-line summary of the current session. |
| **/release-notes** | Open the interactive Claude Code changelog. |
| **/stats** | Open the Stats tab in /usage. |
| **/usage** | Show session cost, plan usage limits, and activity statistics; **/cost** and **/stats** open views within the same usage surface. |
| **/usage-credits** | Open or request usage-credit settings when a limit is reached. |

### Interface and Utility Commands

These commands control terminal presentation, navigation, and general session utilities.

| Command | What it does |
| --- | --- |
| **/color [color|default]** | Change the prompt bar color for the current session. |
| **/exit** | Exit Claude Code; in an attached background session, detach without stopping it. Alias: /quit. |
| **/focus** | Toggle the compact Focus view in fullscreen mode. |
| **/keybindings** | Open the custom keyboard-shortcuts configuration file. |
| **/radio** | Open Claude FM lo-fi radio. |
| **/scroll-speed** | Adjust mouse-wheel speed in fullscreen mode. |
| **/statusline** | Configure the custom status line. |
| **/stickers** | Open the Claude Code sticker-ordering flow. |
| **/terminal-setup** | Configure supported terminals for multiline input and related integration settings. |
| **/theme** | Choose or create a terminal color theme. |
| **/tui [default|fullscreen]** | Switch between the standard and fullscreen terminal renderers. |

## MCP Slash Commands and Custom Commands

The built-in `/mcp` command manages MCP server connections. MCP servers can also publish prompts that appear as slash commands after the server is connected.

### MCP Prompt Command Pattern

```
/mcp__[server]__[prompt] [args]
```

Examples:

```
/mcp__github__list_prs
/mcp__github__pr_review 456
/mcp__jira__create_issue "Bug in login flow" high
```

MCP prompt commands are discovered dynamically, so there is no fixed universal A-Z list for them. Their names depend on the connected servers and the prompts those servers expose.

### Skills, Plugins, and User Commands

Skills, plugins, and local project configuration can contribute additional slash commands. Type `/` to search the combined command menu in your current installation. Use `/skills` to inspect skills, `/plugin` for plugins, and `/reload-skills` or `/reload-plugins` after changing them during a session.

Project and personal commands can be stored as Markdown-based skills or command definitions under Claude Code configuration directories. These custom entries are intentionally excluded from the fixed A-Z table because each installation can have a different set.

## Claude Code CLI Commands

These terminal commands cover the current Claude Code CLI entry points and management subcommands. They run from your shell, not from the in-session slash-command menu.

| CLI command | What it does |
| --- | --- |
| **claude** | Start an interactive Claude Code session. |
| **claude "query"** | Start an interactive session with an initial prompt. |
| **claude -p "query"** | Run one non-interactive prompt and exit. |
| **cat file | claude -p "query"** | Pipe file content into a non-interactive prompt. |
| **claude -c** | Continue the most recent conversation for the current directory. |
| **claude -c -p "query"** | Continue the latest conversation non-interactively. |
| **claude -r "<session>" "query"** | Resume a named or identified session with an optional prompt. |
| **claude update** | Update Claude Code. |
| **claude gateway --config <file>** | Start the self-hosted Claude apps gateway with a gateway configuration. |
| **claude install [version]** | Install or reinstall the native binary, optionally choosing a release channel or version. |
| **claude auth login** | Sign in; auth-specific flags can select Console or SSO flows. |
| **claude auth logout** | Sign out from the Anthropic account. |
| **claude auth status** | Print authentication status. |
| **claude agents** | Open agent view or print background-session data with its flags. |
| **claude attach <id>** | Attach the terminal to a background session. |
| **claude auto-mode defaults** | Print built-in auto-mode classifier rules. |
| **claude auto-mode config** | Print the effective auto-mode configuration. |
| **claude auto-mode reset** | Remove the user-level auto-mode configuration and restore defaults. |
| **claude daemon status** | Show background-session supervisor status. |
| **claude daemon stop --any** | Stop the on-demand supervisor and, unless preserved, its hosted sessions. |
| **claude doctor** | Print read-only installation and settings diagnostics. |
| **claude import [codex|gemini]** | Start an import flow for supported coding-agent configuration. |
| **claude logs <id>** | Print recent output from a background session. |
| **claude mcp** | Open MCP configuration commands. |
| **claude mcp add [options] <name> ...** | Add an MCP server. |
| **claude mcp add-json <name> '<json>'** | Add an MCP server from JSON configuration. |
| **claude mcp add-from-claude-desktop** | Import MCP servers from Claude Desktop where supported. |
| **claude mcp get <name>** | Show one configured MCP server. |
| **claude mcp list** | List configured MCP servers. |
| **claude mcp login <name>** | Authenticate a configured MCP server from the terminal. |
| **claude mcp logout <name>** | Clear stored OAuth credentials for an MCP server. |
| **claude mcp remove <name>** | Remove an MCP server. |
| **claude mcp reset-project-choices** | Reset approvals for project-scoped MCP servers. |
| **claude mcp serve** | Run Claude Code itself as a stdio MCP server. |
| **claude plugin** | Manage Claude Code plugins. Alias: claude plugins. |
| **claude project purge [path]** | Delete local Claude Code state for one project or selected projects. |
| **claude remote-control** | Start a Remote Control server without a local interactive session. |
| **claude respawn <id>** | Restart a background session with its conversation intact. |
| **claude rm <id>** | Remove a background session from agent view while keeping its transcript. |
| **claude self-hosted-runner** | Start or manage a self-hosted environment runner. |
| **claude setup-token** | Generate a long-lived OAuth token for CI or scripts. |
| **claude stop <id>** | Stop a background session. Alias: claude kill. |
| **claude ultrareview [target]** | Run a deep cloud code review non-interactively. |

## Claude Code CLI Flags

These are the current top-level Claude Code flags. Some flags only apply to print mode, cloud dispatch, background sessions, or another specific CLI mode.

| Flag | What it does |
| --- | --- |
| **--add-dir** | Add one or more working directories to the session. |
| **--advisor <model>** | Choose an advisor model for the current session. |
| **--agent** | Start with a specific custom agent. |
| **--agents** | Define custom subagents from JSON at launch. |
| **--allow-dangerously-skip-permissions** | Make bypass-permissions mode available in the permission-mode cycle. |
| **--allowedTools, --allowed-tools** | Pre-approve matching tools or tool calls. |
| **--append-subagent-system-prompt** | Append text to subagent system prompts in non-interactive runs. |
| **--append-subagent-system-prompt-file** | Read appended subagent system-prompt text from a file. |
| **--append-system-prompt** | Append text to Claude Code's default system prompt. |
| **--append-system-prompt-file** | Append system-prompt text from a file. |
| **--autocompact <auto|tokens>** | Set the auto-compact window for this invocation. |
| **--ax-screen-reader** | Use screen-reader friendly terminal output. |
| **--bare** | Start with most project and user customizations skipped. |
| **--betas** | Send additional Anthropic beta headers for API-key sessions. |
| **--bg, --background** | Start the session as a background agent. |
| **--channels** | Enable selected MCP channel sources for the session. |
| **--chrome** | Enable Chrome integration. |
| **--cloud** | Create a cloud session or send a message to an existing web session. |
| **--continue, -c** | Continue the most recent eligible conversation. |
| **--dangerously-load-development-channels** | Load development channels that are not on the approved allowlist. |
| **--dangerously-skip-permissions** | Start with permission prompts bypassed. |
| **--debug** | Enable debug mode, optionally filtering debug categories. |
| **--debug-file <path>** | Write debug output to a specific file. |
| **--disable-slash-commands** | Disable commands and skills for the session. |
| **--disallowedTools, --disallowed-tools** | Deny matching tools or tool calls. |
| **--effort** | Choose the reasoning effort level for the session. |
| **--environment <environment-id>** | Dispatch a cloud session to a self-hosted environment. |
| **--exclude-dynamic-system-prompt-sections** | Move machine-specific system-prompt sections into the first user message. |
| **--exec** | Run a shell command as a PTY-backed background job with --bg. |
| **--fallback-model** | Set one or more fallback models. |
| **--fork-session** | Create a new session ID when resuming or continuing. |
| **--forward-subagent-text** | Include subagent text and thinking in stream-json output. |
| **--from-pr** | Open sessions associated with a pull request or merge request. |
| **--ide** | Connect to an available IDE at startup. |
| **--init** | Run Setup hooks with the init matcher before a print-mode session. |
| **--init-only** | Run setup and SessionStart hooks, then exit. |
| **--include-hook-events** | Include supported hook lifecycle events in stream-json output. |
| **--include-partial-messages** | Include partial streaming events in stream-json output. |
| **--input-format** | Choose text or stream-json input for print mode. |
| **--json-schema** | Require final structured output that matches a JSON Schema. |
| **--maintenance** | Run Setup hooks with the maintenance matcher before print mode. |
| **--max-budget-usd** | Cap API spend for a print-mode run. |
| **--max-turns** | Cap agentic turns in print mode. |
| **--mcp-config** | Load MCP configuration from JSON files or inline JSON. |
| **--model** | Choose the model for the current invocation. |
| **--name, -n** | Assign a display name to the session. |
| **--no-chrome** | Disable Chrome integration for the session. |
| **--no-session-persistence** | Do not save the print-mode session to disk. |
| **--output-format** | Choose text, json, or stream-json output in print mode. |
| **--permission-mode** | Choose the starting permission mode. |
| **--permission-prompt-tool** | Delegate print-mode permission prompts to an MCP tool. |
| **--permission-prompts** | Choose whether a host can answer print-mode permission prompts. |
| **--plugin-dir** | Load a plugin directory or zip archive for this session. |
| **--plugin-url** | Load a plugin zip archive from a URL for this session. |
| **--print, -p** | Run without the interactive terminal UI. |
| **--prompt-suggestions** | Emit predicted next-prompt messages in compatible stream-json runs. |
| **--ref <branch>** | Choose the source ref for a self-hosted environment dispatch. |
| **--remote** | Deprecated alias for --cloud that remains accepted. |
| **--remote-control, --rc** | Start an interactive session with Remote Control enabled. |
| **--remote-control-session-name-prefix <prefix>** | Prefix automatically generated Remote Control session names. |
| **--replay-user-messages** | Echo stream-json input messages back to stdout. |
| **--restricted** | Start with a reduced, evaluation-oriented tool and settings surface. |
| **--resume, -r** | Resume a specific session or open the resume picker. |
| **--safe-mode** | Start with customizations disabled for troubleshooting. |
| **--session-id** | Use a specific UUID as the session ID. |
| **--setting-sources** | Choose which user, project, and local setting sources load. |
| **--settings** | Load session overrides from a JSON file or inline JSON. |
| **--strict-mcp-config** | Ignore MCP configurations outside --mcp-config. |
| **--system-prompt** | Replace the default system prompt with supplied text. |
| **--system-prompt-file** | Replace the default system prompt with file contents. |
| **--teleport** | Resume a Claude Code web session locally. |
| **--teammate-mode** | Choose how agent-team teammates are displayed. |
| **--tmux** | Create a tmux or compatible pane layout for a worktree session. |
| **--tools** | Restrict which built-in tools Claude can use. |
| **--verbose** | Show verbose turn-by-turn output. |
| **--version, -v** | Print the Claude Code version. |
| **--worktree, -w** | Start Claude Code in an isolated Git worktree. |

### Removed and Replaced CLI Flags

| Old flag | Use now |
| --- | --- |
| **--enable-auto-mode** | Use **--permission-mode auto**. The older flag was removed. |

## Claude Code Keyboard Shortcuts

Keyboard behavior can vary by terminal and operating system. The tables below keep the shortcuts grouped by where they are used.

### General Keyboard Shortcuts

| Shortcut | Action |
| --- | --- |
| **Ctrl+C** | Interrupt a running operation; with no operation running, clear the prompt input. |
| **Ctrl+X Ctrl+K** | Stop all background subagents in the session after confirmation. |
| **Ctrl+D** | Exit Claude Code; when input contains text, delete the next character. |
| **Ctrl+G or Ctrl+X Ctrl+E** | Open the current prompt in the default text editor. |
| **Ctrl+L** | Redraw the terminal screen without losing the conversation. |
| **Ctrl+O** | Open or close the transcript viewer. |
| **Ctrl+R** | Search prompt history in reverse. |
| **Ctrl+V / Cmd+V / Alt+V** | Paste an image from the clipboard, depending on platform and terminal. |
| **Ctrl+B** | Move a running Bash command or agent to the background. |
| **Ctrl+T** | Show or hide Claude's task checklist. |
| **Ctrl+S** | Stash the current prompt, or restore the stashed prompt when the input is empty. |
| **Ctrl+Z** | Suspend Claude Code on Unix systems. |
| **Left / Right arrows** | Move between tabs in dialogs and menus. |
| **Tab** | Accept autocomplete, or open/close a comment field on supported permission prompts. |
| **Up / Down or Ctrl+P / Ctrl+N** | Move within multiline input, then browse prompt history at the first or last row. |
| **Esc** | Interrupt Claude or close the current dialog. |
| **Esc Esc** | Clear and save a draft, or open rewind controls when the input is empty. |
| **Shift+Tab** | Cycle permission modes; some Windows runtimes use Alt+M. |
| **Option+P / Alt+P** | Switch model without clearing the prompt. |
| **Option+T / Alt+T** | Toggle extended thinking where the active model permits it. |
| **Option+O / Alt+O** | Toggle fast mode. |

### Text Editing Shortcuts

| Shortcut | Action |
| --- | --- |
| **Ctrl+A** | Move to the start of the current logical line. |
| **Ctrl+E** | Move to the end of the current logical line. |
| **Ctrl+K** | Delete from the cursor to the end of the line. |
| **Ctrl+U** | Delete from the cursor to the start of the line. |
| **Ctrl+W** | Delete the previous word. |
| **Ctrl+Y** | Paste text deleted by line or word editing shortcuts. |
| **Alt+Y** | Cycle through earlier deleted text after Ctrl+Y. |
| **Alt+B** | Move back one word. |
| **Alt+F** | Move forward one word. |
| **Alt+D** | Delete the next word. |
| **Ctrl+\_ or Ctrl+Shift+-** | Undo the last edit to the prompt input. |

### Multiline Input

| Shortcut | Action |
| --- | --- |
| **\ + Enter** | Insert a newline in any terminal. |
| **Option+Enter** | Insert a newline on macOS terminals configured to send Option as Meta. |
| **Shift+Enter** | Insert a newline in terminals that expose this key combination. |
| **Ctrl+J** | Insert a newline without terminal-specific configuration. |
| **Paste directly** | Insert multiline code, logs, or text as pasted input. |

### Quick Input Commands

| Shortcut | Action |
| --- | --- |
| **/ at start** | Open the command and skill menu. |
| **! at start** | Run a shell command directly and add its output to the session. |
| **@** | Open file-path autocomplete and, where available, other live-session mentions. |
| **:** | Open emoji shortcode suggestions. |
| **? on empty input** | Show or hide the shortcut help panel. |

### Transcript Viewer Shortcuts

| Shortcut | Action |
| --- | --- |
| **?** | Toggle the transcript-viewer shortcut panel in fullscreen mode. |
| **{ / }** | Jump to the previous or next user prompt in fullscreen mode. |
| **Ctrl+E** | Toggle expanded transcript content in the classic renderer. |
| **[** | Write the conversation into native terminal scrollback in fullscreen mode. |
| **v** | Open the conversation in the configured external editor. |
| **q / Ctrl+C / Esc** | Exit transcript view. |

### Voice Input

| Shortcut | Action |
| --- | --- |
| **Hold or tap Space** | Record voice input when voice dictation is enabled; tap mode is available through /voice. |

## Claude Code Environment Variables

Claude Code reads environment variables for authentication, model selection, providers, request routing, terminal behavior, MCP, telemetry, automation, and feature controls. The tables below keep the documented variables in the reference rather than selecting only commonly used ones.

<details>
<summary><strong>Authentication, Models, and Providers</strong></summary>

| Variable | What it controls |
| --- | --- |
| **ANTHROPIC\_API\_KEY** | API key used for Anthropic API authentication. |
| **ANTHROPIC\_AUTH\_TOKEN** | Bearer token used for the Authorization header. |
| **ANTHROPIC\_AWS\_API\_KEY** | Workspace API key for Claude Platform on AWS. |
| **ANTHROPIC\_AWS\_BASE\_URL** | Overrides the Claude Platform on AWS endpoint. |
| **ANTHROPIC\_AWS\_WORKSPACE\_ID** | Sets the Claude Platform on AWS workspace ID. |
| **ANTHROPIC\_BASE\_URL** | Overrides the Anthropic API base URL for a proxy or gateway. |
| **ANTHROPIC\_BEDROCK\_BASE\_URL** | Overrides the Amazon Bedrock endpoint. |
| **ANTHROPIC\_BEDROCK\_MANTLE\_BASE\_URL** | Overrides the Bedrock Mantle endpoint. |
| **ANTHROPIC\_BEDROCK\_REGION\_PREFIX** | Chooses the preferred cross-region Bedrock inference prefix. |
| **ANTHROPIC\_BEDROCK\_SERVICE\_TIER** | Sets the Bedrock service tier. |
| **ANTHROPIC\_BETAS** | Adds Anthropic beta header values to API requests. |
| **ANTHROPIC\_CUSTOM\_HEADERS** | Adds custom HTTP headers to model requests. |
| **ANTHROPIC\_CUSTOM\_MODEL\_OPTION** | Adds a custom model ID to the model picker. |
| **ANTHROPIC\_CUSTOM\_MODEL\_OPTION\_DESCRIPTION** | Sets the model-picker description for the custom model entry. |
| **ANTHROPIC\_CUSTOM\_MODEL\_OPTION\_NAME** | Sets the model-picker display name for the custom model entry. |
| **ANTHROPIC\_CUSTOM\_MODEL\_OPTION\_SUPPORTED\_CAPABILITIES** | Declares capabilities supported by the custom model entry. |
| **ANTHROPIC\_DEFAULT\_FABLE\_MODEL** | Sets the model ID used by the Fable alias. |
| **ANTHROPIC\_DEFAULT\_FABLE\_MODEL\_DESCRIPTION** | Sets the model-picker description for the pinned Fable model. |
| **ANTHROPIC\_DEFAULT\_FABLE\_MODEL\_NAME** | Sets the model-picker display name for the pinned Fable model. |
| **ANTHROPIC\_DEFAULT\_FABLE\_MODEL\_SUPPORTED\_CAPABILITIES** | Declares capabilities supported by the pinned Fable model. |
| **ANTHROPIC\_DEFAULT\_HAIKU\_MODEL** | Sets the model ID used by the Haiku alias. |
| **ANTHROPIC\_DEFAULT\_HAIKU\_MODEL\_DESCRIPTION** | Sets the model-picker description for the pinned Haiku model. |
| **ANTHROPIC\_DEFAULT\_HAIKU\_MODEL\_NAME** | Sets the model-picker display name for the pinned Haiku model. |
| **ANTHROPIC\_DEFAULT\_HAIKU\_MODEL\_SUPPORTED\_CAPABILITIES** | Declares capabilities supported by the pinned Haiku model. |
| **ANTHROPIC\_DEFAULT\_MODEL** | Sets the model used for new sessions. |
| **ANTHROPIC\_DEFAULT\_OPUS\_MODEL** | Sets the model ID used by the Opus alias. |
| **ANTHROPIC\_DEFAULT\_OPUS\_MODEL\_DESCRIPTION** | Sets the model-picker description for the pinned Opus model. |
| **ANTHROPIC\_DEFAULT\_OPUS\_MODEL\_NAME** | Sets the model-picker display name for the pinned Opus model. |
| **ANTHROPIC\_DEFAULT\_OPUS\_MODEL\_SUPPORTED\_CAPABILITIES** | Declares capabilities supported by the pinned Opus model. |
| **ANTHROPIC\_DEFAULT\_SONNET\_MODEL** | Sets the model ID used by the Sonnet alias. |
| **ANTHROPIC\_DEFAULT\_SONNET\_MODEL\_DESCRIPTION** | Sets the model-picker description for the pinned Sonnet model. |
| **ANTHROPIC\_DEFAULT\_SONNET\_MODEL\_NAME** | Sets the model-picker display name for the pinned Sonnet model. |
| **ANTHROPIC\_DEFAULT\_SONNET\_MODEL\_SUPPORTED\_CAPABILITIES** | Declares capabilities supported by the pinned Sonnet model. |
| **ANTHROPIC\_FEDERATION\_RULE\_ID** | Configures Anthropic federation rule ID. |
| **ANTHROPIC\_FOUNDRY\_API\_KEY** | Configures Anthropic foundry API key. |
| **ANTHROPIC\_FOUNDRY\_AUTH\_TOKEN** | Configures Anthropic foundry auth token. |
| **ANTHROPIC\_FOUNDRY\_BASE\_URL** | Configures Anthropic foundry base url. |
| **ANTHROPIC\_FOUNDRY\_RESOURCE** | Configures Anthropic foundry resource. |
| **ANTHROPIC\_MODEL** | Sets the active model when no higher-priority model choice overrides it. |
| **ANTHROPIC\_ORGANIZATION\_ID** | Configures Anthropic organization ID. |
| **ANTHROPIC\_PROFILE** | Selects an Anthropic authentication profile. |
| **ANTHROPIC\_SMALL\_FAST\_MODEL\_AWS\_REGION** | Configures Anthropic small fast model AWS region. |
| **ANTHROPIC\_VERTEX\_BASE\_URL** | Overrides the Google Cloud Agent Platform endpoint. |
| **ANTHROPIC\_VERTEX\_PROJECT\_ID** | Sets the Google Cloud project for Agent Platform requests. |
| **ANTHROPIC\_WORKSPACE\_ID** | Configures Anthropic workspace ID. |
| **API\_FORCE\_IDLE\_TIMEOUT** | Overrides or disables the streaming body idle timeout. |
| **API\_TIMEOUT\_MS** | Sets the API request timeout in milliseconds. |
| **AWS\_BEARER\_TOKEN\_BEDROCK** | Sets an Amazon Bedrock bearer token. |
| **FALLBACK\_FOR\_ALL\_PRIMARY\_MODELS** | Applies fallback behavior across primary models. |
| **VERTEX\_REGION\_CLAUDE\_3\_5\_HAIKU** | Overrides the Google Cloud Agent Platform region for Claude 3 5 Haiku. |
| **VERTEX\_REGION\_CLAUDE\_3\_5\_SONNET** | Overrides the Google Cloud Agent Platform region for Claude 3 5 Sonnet. |
| **VERTEX\_REGION\_CLAUDE\_3\_7\_SONNET** | Overrides the Google Cloud Agent Platform region for Claude 3 7 Sonnet. |
| **VERTEX\_REGION\_CLAUDE\_4\_0\_OPUS** | Overrides the Google Cloud Agent Platform region for Claude 4 0 Opus. |
| **VERTEX\_REGION\_CLAUDE\_4\_0\_SONNET** | Overrides the Google Cloud Agent Platform region for Claude 4 0 Sonnet. |
| **VERTEX\_REGION\_CLAUDE\_4\_1\_OPUS** | Overrides the Google Cloud Agent Platform region for Claude 4 1 Opus. |
| **VERTEX\_REGION\_CLAUDE\_4\_5\_OPUS** | Overrides the Google Cloud Agent Platform region for Claude 4 5 Opus. |
| **VERTEX\_REGION\_CLAUDE\_4\_5\_SONNET** | Overrides the Google Cloud Agent Platform region for Claude 4 5 Sonnet. |
| **VERTEX\_REGION\_CLAUDE\_4\_6\_OPUS** | Overrides the Google Cloud Agent Platform region for Claude 4 6 Opus. |
| **VERTEX\_REGION\_CLAUDE\_4\_6\_SONNET** | Overrides the Google Cloud Agent Platform region for Claude 4 6 Sonnet. |
| **VERTEX\_REGION\_CLAUDE\_4\_7\_OPUS** | Overrides the Google Cloud Agent Platform region for Claude 4 7 Opus. |
| **VERTEX\_REGION\_CLAUDE\_4\_8\_OPUS** | Overrides the Google Cloud Agent Platform region for Claude 4 8 Opus. |
| **VERTEX\_REGION\_CLAUDE\_5\_OPUS** | Overrides the Google Cloud Agent Platform region for Claude 5 Opus. |
| **VERTEX\_REGION\_CLAUDE\_5\_SONNET** | Overrides the Google Cloud Agent Platform region for Claude 5 Sonnet. |
| **VERTEX\_REGION\_CLAUDE\_FABLE\_5** | Overrides the Google Cloud Agent Platform region for Claude Fable 5. |
| **VERTEX\_REGION\_CLAUDE\_FABLE\_5\_1** | Overrides the Google Cloud Agent Platform region for Claude Fable 5 1. |
| **VERTEX\_REGION\_CLAUDE\_HAIKU\_4\_5** | Overrides the Google Cloud Agent Platform region for Claude Haiku 4 5. |

</details>

<details>
<summary><strong>Claude Code Runtime and Behavior</strong></summary>

| Variable | What it controls |
| --- | --- |
| **CLAUDE\_AFK\_COUNTDOWN\_MS** | Configures afk countdown milliseconds. |
| **CLAUDE\_AFK\_TIMEOUT\_MS** | Configures afk timeout milliseconds. |
| **CLAUDE\_AGENT\_SDK\_DISABLE\_BUILTIN\_AGENTS** | Configures agent SDK disable builtin agents. |
| **CLAUDE\_AGENT\_SDK\_MCP\_NO\_PREFIX** | Configures agent SDK MCP no prefix. |
| **CLAUDE\_ASYNC\_AGENT\_STALL\_TIMEOUT\_MS** | Configures async agent stall timeout milliseconds. |
| **CLAUDE\_AUTOCOMPACT\_PCT\_OVERRIDE** | Sets an earlier auto-compaction trigger percentage. |
| **CLAUDE\_AUTO\_BACKGROUND\_TASKS** | Forces long-running agent tasks to move to the background automatically. |
| **CLAUDE\_AX\_PREPARK\_MS** | Configures ax prepark milliseconds. |
| **CLAUDE\_AX\_SCREEN\_READER** | Configures ax screen reader. |
| **CLAUDE\_AX\_STARTUP\_QUIET\_MS** | Configures ax startup quiet milliseconds. |
| **CLAUDE\_BASH\_MAINTAIN\_PROJECT\_WORKING\_DIR** | Configures bash maintain project working dir. |
| **CLAUDE\_BYTE\_STREAM\_IDLE\_TIMEOUT\_MS** | Configures byte stream idle timeout milliseconds. |
| **CLAUDE\_CLIENT\_PRESENCE\_FILE** | Points to a presence marker that suppresses mobile notifications while the computer is active. |
| **CLAUDE\_CODE\_ACCESSIBILITY** | Keeps the native terminal cursor visible for accessibility tools. |
| **CLAUDE\_CODE\_ADDITIONAL\_DIRECTORIES\_CLAUDE\_MD** | Loads CLAUDE.md and related memory files from directories added with --add-dir. |
| **CLAUDE\_CODE\_ALT\_SCREEN\_FULL\_REPAINT** | Forces full-frame repainting in fullscreen mode. |
| **CLAUDE\_CODE\_ALWAYS\_ENABLE\_EFFORT** | Sends the effort parameter for compatible custom or gateway model IDs. |
| **CLAUDE\_CODE\_API\_KEY\_HELPER\_TTL\_MS** | Sets how often apiKeyHelper credentials are refreshed. |
| **CLAUDE\_CODE\_ARTIFACT\_AUTO\_OPEN** | Configures code artifact auto open. |
| **CLAUDE\_CODE\_ARTIFACT\_COMMENTS** | Configures code artifact comments. |
| **CLAUDE\_CODE\_ARTIFACT\_COMMENTS\_AUTOREACT** | Configures code artifact comments autoreact. |
| **CLAUDE\_CODE\_ATTRIBUTION\_HEADER** | Configures code attribution header. |
| **CLAUDE\_CODE\_AUTO\_BACKGROUND\_WORKER\_CHECKIN\_SECONDS** | Configures code auto background worker checkin seconds. |
| **CLAUDE\_CODE\_AUTO\_COMPACT\_WINDOW** | Sets the auto-compact context window in tokens. |
| **CLAUDE\_CODE\_AUTO\_CONNECT\_IDE** | Overrides automatic IDE connection behavior. |
| **CLAUDE\_CODE\_AWS\_CHAIN\_RESOLVE\_TIMEOUT\_MS** | Configures code AWS chain resolve timeout milliseconds. |
| **CLAUDE\_CODE\_BRIDGE\_SESSION\_ID** | Exposes the active Remote Control session ID to subprocesses. |
| **CLAUDE\_CODE\_BS\_AS\_CTRL\_BACKSPACE** | Configures code bs as ctrl backspace. |
| **CLAUDE\_CODE\_CERT\_STORE** | Chooses CA certificate stores for TLS connections. |
| **CLAUDE\_CODE\_CHILD\_SESSION** | Marks subprocesses directly spawned by Claude Code tools or hooks. |
| **CLAUDE\_CODE\_CLIENT\_CERT** | Sets the client certificate file for mTLS. |
| **CLAUDE\_CODE\_CLIENT\_KEY** | Sets the client private key file for mTLS. |
| **CLAUDE\_CODE\_CLIENT\_KEY\_PASSPHRASE** | Sets the passphrase for an encrypted mTLS client key. |
| **CLAUDE\_CODE\_DEBUG\_LOGS\_DIR** | Overrides the debug log file path. |
| **CLAUDE\_CODE\_DEBUG\_LOG\_LEVEL** | Sets the minimum debug-log severity. |
| **CLAUDE\_CODE\_DISABLE\_1M\_CONTEXT** | Disables 1M-context model behavior and variants. |
| **CLAUDE\_CODE\_DISABLE\_ADAPTIVE\_THINKING** | Disables adaptive thinking. |
| **CLAUDE\_CODE\_DISABLE\_ADMIN\_ENV\_UNION** | Disables admin env union. |
| **CLAUDE\_CODE\_DISABLE\_ADVISOR\_TOOL** | Disables advisor tool. |
| **CLAUDE\_CODE\_DISABLE\_AGENT\_VIEW** | Disables agent view. |
| **CLAUDE\_CODE\_DISABLE\_ALTERNATE\_SCREEN** | Disables alternate screen. |
| **CLAUDE\_CODE\_DISABLE\_ARTIFACT** | Disables artifact. |
| **CLAUDE\_CODE\_DISABLE\_ATTACHMENTS** | Disables attachments. |
| **CLAUDE\_CODE\_DISABLE\_AUTO\_MEMORY** | Disables auto memory. |
| **CLAUDE\_CODE\_DISABLE\_BACKGROUND\_TASKS** | Disables background tasks. |
| **CLAUDE\_CODE\_DISABLE\_BEDROCK\_CONTENT\_TYPE\_DEFAULT** | Disables bedrock content type default. |
| **CLAUDE\_CODE\_DISABLE\_BEDROCK\_CONTENT\_TYPE\_GUARD** | Disables bedrock content type guard. |
| **CLAUDE\_CODE\_DISABLE\_BG\_EXIT\_HANDOFF** | Disables background exit handoff. |
| **CLAUDE\_CODE\_DISABLE\_BG\_SHELL\_PRESSURE\_REAP** | Disables background shell pressure reap. |
| **CLAUDE\_CODE\_DISABLE\_BUNDLED\_SKILLS** | Disables bundled skills. |
| **CLAUDE\_CODE\_DISABLE\_CFC\_PROMPT** | Disables CFC prompt. |
| **CLAUDE\_CODE\_DISABLE\_CLAUDE\_MDS** | Disables Claude mds. |
| **CLAUDE\_CODE\_DISABLE\_CRON** | Disables cron. |
| **CLAUDE\_CODE\_DISABLE\_EXPERIMENTAL\_BETAS** | Disables experimental betas. |
| **CLAUDE\_CODE\_DISABLE\_EXPLORE\_PLAN\_AGENTS** | Disables explore plan agents. |
| **CLAUDE\_CODE\_DISABLE\_FAST\_MODE** | Disables fast mode. |
| **CLAUDE\_CODE\_DISABLE\_FEEDBACK\_SURVEY** | Disables feedback survey. |
| **CLAUDE\_CODE\_DISABLE\_FILE\_CHECKPOINTING** | Disables file checkpointing. |
| **CLAUDE\_CODE\_DISABLE\_GIT\_INSTRUCTIONS** | Disables Git instructions. |
| **CLAUDE\_CODE\_DISABLE\_LEGACY\_MODEL\_REMAP** | Disables legacy model remap. |
| **CLAUDE\_CODE\_DISABLE\_MOUSE** | Disables mouse. |
| **CLAUDE\_CODE\_DISABLE\_MOUSE\_CLICKS** | Disables mouse clicks. |
| **CLAUDE\_CODE\_DISABLE\_MTLS\_RELOAD\_ON\_STALE\_CONNECTION** | Disables mTLS reload on stale connection. |
| **CLAUDE\_CODE\_DISABLE\_NONESSENTIAL\_TRAFFIC** | Disables nonessential traffic. |
| **CLAUDE\_CODE\_DISABLE\_NONSTREAMING\_FALLBACK** | Disables nonstreaming fallback. |
| **CLAUDE\_CODE\_DISABLE\_NOTIFICATION\_PRESENCE\_CHECK** | Disables notification presence check. |
| **CLAUDE\_CODE\_DISABLE\_OFFICIAL\_MARKETPLACE\_AUTOINSTALL** | Disables official marketplace autoinstall. |
| **CLAUDE\_CODE\_DISABLE\_PERMISSION\_PROMPT\_NOTIFY\_HOOKS** | Disables permission prompt notify hooks. |
| **CLAUDE\_CODE\_DISABLE\_POLICY\_SKILLS** | Disables policy skills. |
| **CLAUDE\_CODE\_DISABLE\_TERMINAL\_TITLE** | Disables terminal title. |
| **CLAUDE\_CODE\_DISABLE\_THINKING** | Disables thinking. |
| **CLAUDE\_CODE\_DISABLE\_UNKNOWN\_MODEL\_WINDOW\_ENFORCEMENT** | Disables unknown model window enforcement. |
| **CLAUDE\_CODE\_DISABLE\_VIRTUAL\_SCROLL** | Disables virtual scroll. |
| **CLAUDE\_CODE\_DISABLE\_WORKFLOWS** | Disables workflows. |
| **CLAUDE\_CODE\_EFFORT\_LEVEL** | Sets the effort level and takes precedence over command-line and in-session choices. |
| **CLAUDE\_CODE\_ENABLE\_APPEND\_SUBAGENT\_PROMPT** | Enables append subagent prompt. |
| **CLAUDE\_CODE\_ENABLE\_AWAY\_SUMMARY** | Enables away summary. |
| **CLAUDE\_CODE\_ENABLE\_BACKGROUND\_PLUGIN\_REFRESH** | Enables background plugin refresh. |
| **CLAUDE\_CODE\_ENABLE\_FEEDBACK\_SURVEY\_FOR\_OTEL** | Enables feedback survey for OpenTelemetry. |
| **CLAUDE\_CODE\_ENABLE\_FINE\_GRAINED\_TOOL\_STREAMING** | Enables fine grained tool streaming. |
| **CLAUDE\_CODE\_ENABLE\_GATEWAY\_MODEL\_DISCOVERY** | Enables gateway model discovery. |
| **CLAUDE\_CODE\_ENABLE\_PROMPT\_SUGGESTION** | Enables prompt suggestion. |
| **CLAUDE\_CODE\_ENABLE\_TASKS** | Enables tasks. |
| **CLAUDE\_CODE\_ENABLE\_TELEMETRY** | Enables telemetry. |
| **CLAUDE\_CODE\_ENABLE\_TODO\_TOOLS** | Enables todo tools. |
| **CLAUDE\_CODE\_EXIT\_AFTER\_STOP\_DELAY** | Configures code exit after stop delay. |
| **CLAUDE\_CODE\_EXPERIMENTAL\_AGENT\_TEAMS** | Configures code experimental agent teams. |
| **CLAUDE\_CODE\_EXTRA\_BODY** | Configures code extra body. |
| **CLAUDE\_CODE\_FILE\_READ\_MAX\_OUTPUT\_TOKENS** | Configures code file read max output tokens. |
| **CLAUDE\_CODE\_FORCE\_SESSION\_PERSISTENCE** | Forces session persistence behavior. |
| **CLAUDE\_CODE\_FORCE\_STRIKETHROUGH** | Forces strikethrough behavior. |
| **CLAUDE\_CODE\_FORWARD\_SUBAGENT\_TEXT** | Includes subagent text and thinking in compatible stream-json output. |
| **CLAUDE\_CODE\_GIT\_BASH\_PATH** | Sets the Git Bash executable path on Windows. |
| **CLAUDE\_CODE\_GLOB\_HIDDEN** | Controls whether the Glob tool includes hidden files. |
| **CLAUDE\_CODE\_GLOB\_NO\_IGNORE** | Controls whether the Glob tool ignores .gitignore rules. |
| **CLAUDE\_CODE\_GLOB\_TIMEOUT\_SECONDS** | Sets the Glob tool discovery timeout. |
| **CLAUDE\_CODE\_GOAL\_CHECKIN\_MINUTES** | Sets how often Claude checks on background work tied to an active goal. |
| **CLAUDE\_CODE\_HIDE\_CWD** | Configures code hide cwd. |
| **CLAUDE\_CODE\_IDE\_HOST\_OVERRIDE** | Configures code IDE host override. |
| **CLAUDE\_CODE\_IDE\_SKIP\_AUTO\_INSTALL** | Configures code IDE skip auto install. |
| **CLAUDE\_CODE\_IDE\_SKIP\_VALID\_CHECK** | Configures code IDE skip valid check. |
| **CLAUDE\_CODE\_MAX\_CONCURRENT\_SUBAGENTS** | Sets the maximum number of concurrently running subagents. |
| **CLAUDE\_CODE\_MAX\_CONTEXT\_TOKENS** | Overrides the assumed context-window size for the active model. |
| **CLAUDE\_CODE\_MAX\_OUTPUT\_TOKENS** | Sets the maximum output tokens for model requests. |
| **CLAUDE\_CODE\_MAX\_RETRIES** | Sets the API request retry count. |
| **CLAUDE\_CODE\_MAX\_SUBAGENT\_SPAWN\_DEPTH** | Sets how many nested subagent layers can be created. |
| **CLAUDE\_CODE\_MAX\_TOOL\_USE\_CONCURRENCY** | Sets the parallel tool and subagent execution limit. |
| **CLAUDE\_CODE\_MAX\_TURNS** | Sets a default turn cap when no CLI turn limit is supplied. |
| **CLAUDE\_CODE\_MAX\_WEB\_SEARCHES\_PER\_SESSION** | Caps WebSearch calls in one session. |
| **CLAUDE\_CODE\_MCP\_ALLOWLIST\_ENV** | Restricts stdio MCP servers to a safe baseline environment plus configured variables. |
| **CLAUDE\_CODE\_MCP\_AUTO\_BACKGROUND\_MS** | Sets when a long MCP tool call moves to the background. |
| **CLAUDE\_CODE\_MCP\_TOOL\_IDLE\_TIMEOUT** | Sets the idle timeout for MCP tool calls. |
| **CLAUDE\_CODE\_MESSAGING\_SOCKET** | Exposes the cross-session inbox socket path to hooks and shell commands. |
| **CLAUDE\_CODE\_MESSAGING\_TOKEN** | Exposes the per-session inbox authentication token to hooks and shell commands. |
| **CLAUDE\_CODE\_NATIVE\_CURSOR** | Configures code native cursor. |
| **CLAUDE\_CODE\_NEW\_INIT** | Configures code new init. |
| **CLAUDE\_CODE\_NO\_FLICKER** | Configures code no flicker. |
| **CLAUDE\_CODE\_OAUTH\_REFRESH\_TOKEN** | Configures code OAuth refresh token. |
| **CLAUDE\_CODE\_OAUTH\_SCOPES** | Configures code OAuth scopes. |
| **CLAUDE\_CODE\_OAUTH\_TOKEN** | Configures code OAuth token. |
| **CLAUDE\_CODE\_OTEL\_CONTENT\_MAX\_LENGTH** | Configures Claude Code OpenTelemetry content max length. |
| **CLAUDE\_CODE\_OTEL\_DIAG\_STDERR** | Configures Claude Code OpenTelemetry diag stderr. |
| **CLAUDE\_CODE\_OTEL\_FLUSH\_TIMEOUT\_MS** | Configures Claude Code OpenTelemetry flush timeout milliseconds. |
| **CLAUDE\_CODE\_OTEL\_HEADERS\_HELPER\_DEBOUNCE\_MS** | Configures Claude Code OpenTelemetry headers helper debounce milliseconds. |
| **CLAUDE\_CODE\_OTEL\_SHUTDOWN\_TIMEOUT\_MS** | Configures Claude Code OpenTelemetry shutdown timeout milliseconds. |
| **CLAUDE\_CODE\_PACKAGE\_MANAGER\_AUTO\_UPDATE** | Controls package-manager background upgrades for supported installations. |
| **CLAUDE\_CODE\_PERFORCE\_MODE** | Adds Perforce-aware handling for read-only files. |
| **CLAUDE\_CODE\_PLUGIN\_CACHE\_DIR** | Configures code plugin cache dir. |
| **CLAUDE\_CODE\_PLUGIN\_GIT\_TIMEOUT\_MS** | Configures code plugin Git timeout milliseconds. |
| **CLAUDE\_CODE\_PLUGIN\_KEEP\_MARKETPLACE\_ON\_FAILURE** | Configures code plugin keep marketplace on failure. |
| **CLAUDE\_CODE\_PLUGIN\_PREFER\_HTTPS** | Configures code plugin prefer HTTPS. |
| **CLAUDE\_CODE\_PROCESS\_WRAPPER** | Runs Claude Code child processes through a required corporate launcher. |
| **CLAUDE\_CODE\_PROJECT\_DIR\_NAME** | Overrides the project directory name used under a custom Claude config directory. |
| **CLAUDE\_CODE\_PROMPT\_CACHE\_TTL** | Sets the main conversation prompt-cache TTL. |
| **CLAUDE\_CODE\_PROPAGATE\_TRACEPARENT** | Configures code propagate traceparent. |
| **CLAUDE\_CODE\_PROVIDER\_MANAGED\_BY\_HOST** | Marks the provider as managed by a host platform. |
| **CLAUDE\_CODE\_REMOTE\_SESSION\_ID** | Exposes the cloud or remote session identifier. |
| **CLAUDE\_CODE\_RESUME\_PROMPT** | Configures code resume prompt. |
| **CLAUDE\_CODE\_RETRY\_WATCHDOG** | Uses extended retry behavior for unattended sessions. |
| **CLAUDE\_CODE\_SAFE\_MODE** | Starts Claude Code with customizations disabled for troubleshooting. |
| **CLAUDE\_CODE\_SCRIPT\_CAPS** | Sets limits for script invocations. |
| **CLAUDE\_CODE\_SCROLL\_SPEED** | Sets terminal scroll speed. |
| **CLAUDE\_CODE\_SEND\_FEEDBACK** | Configures code send feedback. |
| **CLAUDE\_CODE\_SESSIONEND\_HOOKS\_TIMEOUT\_MS** | Configures code sessionend hooks timeout milliseconds. |
| **CLAUDE\_CODE\_SESSION\_ID** | Exposes or sets the current session identifier where supported. |
| **CLAUDE\_CODE\_SIMPLE** | Enables the minimal environment used by bare mode. |
| **CLAUDE\_CODE\_SIMPLE\_SYSTEM\_PROMPT** | Uses the simplified system-prompt behavior for minimal runs. |
| **CLAUDE\_CODE\_SKIP\_ANTHROPIC\_AWS\_AUTH** | Skips anthropic AWS auth. |
| **CLAUDE\_CODE\_SKIP\_AWS\_CRED\_CACHE** | Skips AWS cred cache. |
| **CLAUDE\_CODE\_SKIP\_BEDROCK\_AUTH** | Skips bedrock auth. |
| **CLAUDE\_CODE\_SKIP\_FAST\_MODE\_NETWORK\_ERRORS** | Skips fast mode network errors. |
| **CLAUDE\_CODE\_SKIP\_FAST\_MODE\_ORG\_CHECK** | Skips fast mode org check. |
| **CLAUDE\_CODE\_SKIP\_FOUNDRY\_AUTH** | Skips foundry auth. |
| **CLAUDE\_CODE\_SKIP\_MANTLE\_AUTH** | Skips mantle auth. |
| **CLAUDE\_CODE\_SKIP\_PROMPT\_HISTORY** | Skips prompt history. |
| **CLAUDE\_CODE\_SKIP\_VERTEX\_AUTH** | Skips vertex auth. |
| **CLAUDE\_CODE\_STOP\_HOOK\_BLOCK\_CAP** | Caps repeated Stop or SubagentStop hook blocking. |
| **CLAUDE\_CODE\_SUBAGENT\_MODEL** | Sets the default model for subagents, teammates, and workflow agents. |
| **CLAUDE\_CODE\_SUBAGENT\_MODEL\_FORCE** | Forces the configured subagent model across agent types. |
| **CLAUDE\_CODE\_SUBAGENT\_PROMPT\_CACHE\_TTL** | Sets the prompt-cache TTL used by subagents. |
| **CLAUDE\_CODE\_SUBPROCESS\_ENV\_SCRUB** | Configures code subprocess env scrub. |
| **CLAUDE\_CODE\_SYNC\_PLUGIN\_INSTALL** | Configures plugin install. |
| **CLAUDE\_CODE\_SYNC\_PLUGIN\_INSTALL\_TIMEOUT\_MS** | Configures plugin install timeout milliseconds. |
| **CLAUDE\_CODE\_SYNC\_SKILLS** | Configures skills. |
| **CLAUDE\_CODE\_SYNC\_SKILLS\_INSTALL\_TIMEOUT\_MS** | Configures skills install timeout milliseconds. |
| **CLAUDE\_CODE\_SYNC\_SKILLS\_WAIT\_TIMEOUT\_MS** | Configures skills wait timeout milliseconds. |
| **CLAUDE\_CODE\_SYNTAX\_HIGHLIGHT** | Configures code syntax highlight. |
| **CLAUDE\_CODE\_TASK\_LIST\_ID** | Shares a task list across Claude Code sessions that use the same ID. |
| **CLAUDE\_CODE\_TEAM\_TEARDOWN\_PARK\_TIMEOUT\_MS** | Configures code team teardown park timeout milliseconds. |
| **CLAUDE\_CODE\_TMPDIR** | Overrides Claude Code's internal temporary directory. |
| **CLAUDE\_CODE\_TMUX\_TRUECOLOR** | Allows 24-bit truecolor output inside tmux. |
| **CLAUDE\_CODE\_TOOL\_MEMORY\_CGROUP\_EXCLUDE** | Chooses process types excluded from the Linux tool-memory cap. |
| **CLAUDE\_CODE\_TOOL\_MEMORY\_LIMIT** | Caps tool-process memory on Linux and WSL. |
| **CLAUDE\_CODE\_USER\_DIALOG\_TIMEOUT\_MS** | Sets a deadline for remote-client dialogs and held-message approvals. |
| **CLAUDE\_CODE\_USE\_ANTHROPIC\_AWS** | Uses Claude Platform on AWS. |
| **CLAUDE\_CODE\_USE\_BEDROCK** | Uses Amazon Bedrock. |
| **CLAUDE\_CODE\_USE\_FOUNDRY** | Uses Microsoft Foundry. |
| **CLAUDE\_CODE\_USE\_MANTLE** | Uses the Amazon Bedrock Mantle endpoint. |
| **CLAUDE\_CODE\_USE\_NATIVE\_FILE\_SEARCH** | Uses Node.js file APIs for configuration discovery rather than bundled ripgrep. |
| **CLAUDE\_CODE\_USE\_POWERSHELL\_TOOL** | Controls availability of the native PowerShell tool. |
| **CLAUDE\_CODE\_USE\_VERTEX** | Uses Google Cloud's Agent Platform. |
| **CLAUDE\_CODE\_WEBFETCH\_CACHE\_TTL\_MS** | Sets the WebFetch response-cache lifetime. |
| **CLAUDE\_CODE\_WORKFLOW\_PREFIX\_STAGGER\_MS** | Sets the maximum stagger for same-prefix workflow agents. |
| **CLAUDE\_CONFIG\_DIR** | Overrides the default ~/.claude configuration directory. |
| **CLAUDE\_DISABLE\_ADOPT** | Stops in-flight background work when a session moves to the background rather than carrying that work over. |
| **CLAUDE\_EFFORT** | Exposes the current effort level to Bash and hook subprocesses. |
| **CLAUDE\_ENABLE\_BYTE\_WATCHDOG** | Forces the byte-level streaming idle watchdog on or off. |
| **CLAUDE\_ENABLE\_BYTE\_WATCHDOG\_BEDROCK** | Enables the byte-level streaming watchdog for Bedrock event streams. |
| **CLAUDE\_ENABLE\_STREAM\_WATCHDOG** | Configures enable stream watchdog. |
| **CLAUDE\_ENV\_FILE** | Configures env file. |
| **CLAUDE\_PID** | Configures pid. |
| **CLAUDE\_REMOTE\_CONTROL\_SESSION\_NAME\_PREFIX** | Prefixes automatically generated Remote Control session names. |
| **CLAUDE\_STREAM\_FIRST\_BYTE\_TIMEOUT\_MS** | Sets the streaming first-byte timeout. |
| **CLAUDE\_STREAM\_IDLE\_TIMEOUT\_MS** | Sets the event-level streaming idle timeout. |
| **CLAUDE\_SUBAGENT\_BG\_SHELL\_MAX\_MS** | Sets the lifetime limit for background shell commands owned by subagents. |

</details>

<details>
<summary><strong>MCP, Networking, Telemetry, and Other Variables</strong></summary>

| Variable | What it controls |
| --- | --- |
| **BASH\_DEFAULT\_TIMEOUT\_MS** | Sets the default Bash command timeout. |
| **BASH\_MAX\_OUTPUT\_LENGTH** | Sets the maximum Bash output returned to Claude. |
| **BASH\_MAX\_TIMEOUT\_MS** | Sets the maximum Bash timeout Claude can request. |
| **BETA\_TRACING\_ENDPOINT** | Sets the OTLP endpoint used for detailed beta tracing. |
| **CCR\_FORCE\_BUNDLE** | Forces cloud dispatch to bundle and upload the local repository. |
| **CLAUDECODE** | Marks subprocesses launched from Claude Code or its IDE integrations. |
| **DEBUG** | Enables debug logging. |
| **DISABLE\_AUTOUPDATER** | Disables autoupdater. |
| **DISABLE\_AUTO\_COMPACT** | Disables auto compact. |
| **DISABLE\_COMPACT** | Disables compact. |
| **DISABLE\_COST\_WARNINGS** | Disables cost warnings. |
| **DISABLE\_DOCTOR\_COMMAND** | Disables doctor command. |
| **DISABLE\_ERROR\_REPORTING** | Disables error reporting. |
| **DISABLE\_EXTRA\_USAGE\_COMMAND** | Disables extra usage command. |
| **DISABLE\_FEEDBACK\_COMMAND** | Disables feedback command. |
| **DISABLE\_GROWTHBOOK** | Disables growthbook. |
| **DISABLE\_INSTALLATION\_CHECKS** | Disables installation checks. |
| **DISABLE\_INSTALL\_GITHUB\_APP\_COMMAND** | Disables install github app command. |
| **DISABLE\_INTERLEAVED\_THINKING** | Disables interleaved thinking. |
| **DISABLE\_LOGIN\_COMMAND** | Disables login command. |
| **DISABLE\_LOGOUT\_COMMAND** | Disables logout command. |
| **DISABLE\_PROMPT\_CACHING** | Disables prompt caching. |
| **DISABLE\_PROMPT\_CACHING\_FABLE** | Disables prompt caching fable. |
| **DISABLE\_PROMPT\_CACHING\_HAIKU** | Disables prompt caching haiku. |
| **DISABLE\_PROMPT\_CACHING\_OPUS** | Disables prompt caching opus. |
| **DISABLE\_PROMPT\_CACHING\_SONNET** | Disables prompt caching sonnet. |
| **DISABLE\_TELEMETRY** | Disables telemetry and feature-flag fetching. |
| **DISABLE\_UPDATES** | Blocks all update paths, including manual updates. |
| **DISABLE\_UPGRADE\_COMMAND** | Disables upgrade command. |
| **DO\_NOT\_TRACK** | Opts out of telemetry using the common DO\_NOT\_TRACK convention. |
| **ENABLE\_BETA\_TRACING\_DETAILED** | Enables detailed beta tracing when a tracing endpoint is configured. |
| **ENABLE\_CLAUDEAI\_MCP\_SERVERS** | Controls loading of MCP connectors configured in Claude.ai. |
| **ENABLE\_PROMPT\_CACHING\_1H** | Requests a one-hour prompt-cache TTL. |
| **ENABLE\_TOOL\_SEARCH** | Controls deferred MCP tool discovery and ToolSearch behavior. |
| **FORCE\_AUTOUPDATE\_PLUGINS** | Forces autoupdate plugins. |
| **FORCE\_HYPERLINK** | Forces hyperlink. |
| **FORCE\_PROMPT\_CACHING\_5M** | Forces prompt caching 5m. |
| **HTTPS\_PROXY** | Sets the HTTPS proxy. |
| **HTTP\_PROXY** | Sets the HTTP proxy. |
| **IS\_DEMO** | Configures is demo. |
| **MAX\_MCP\_OUTPUT\_TOKENS** | Sets the MCP output-token limit for tools without their own limit. |
| **MAX\_STRUCTURED\_OUTPUT\_RETRIES** | Sets retries for structured-output validation. |
| **MAX\_THINKING\_TOKENS** | Sets the fixed thinking-token budget where fixed thinking is used. |
| **MCP\_CLIENT\_SECRET** | Supplies an MCP OAuth client secret when requested by MCP configuration. |
| **MCP\_CONNECTION\_NONBLOCKING** | Configures MCP connection nonblocking. |
| **MCP\_CONNECT\_TIMEOUT\_MS** | Sets the MCP connection timeout. |
| **MCP\_DISCOVERY\_CACHE** | Configures MCP discovery cache. |
| **MCP\_DISCOVERY\_CACHE\_MAX\_STALE\_S** | Configures MCP discovery cache max stale s. |
| **MCP\_DISCOVERY\_CACHE\_STRIKES** | Configures MCP discovery cache strikes. |
| **MCP\_DISCOVERY\_CACHE\_TTL\_S** | Configures MCP discovery cache TTL s. |
| **MCP\_OAUTH\_CALLBACK\_PORT** | Sets the local OAuth callback port for MCP authentication. |
| **MCP\_PROTOCOL\_NEGOTIATION** | Configures MCP protocol negotiation. |
| **MCP\_REMOTE\_SERVER\_CONNECTION\_BATCH\_SIZE** | Sets parallel startup connections for remote MCP servers. |
| **MCP\_SDK\_GENERATION** | Chooses the MCP client runtime generation. |
| **MCP\_SERVER\_CONNECTION\_BATCH\_SIZE** | Sets parallel startup connections for local stdio MCP servers. |
| **MCP\_TIMEOUT** | Sets the MCP server startup timeout. |
| **MCP\_TOOL\_TIMEOUT** | Sets the overall MCP tool execution timeout. |
| **NO\_PROXY** | Lists hosts that bypass configured proxies. |
| **OTEL\_ATTRIBUTE\_VALUE\_LENGTH\_LIMIT** | Sets the OpenTelemetry attribute-value length limit. |
| **OTEL\_EXPORTER\_OTLP\_ENDPOINT** | Sets the OpenTelemetry OTLP endpoint. |
| **OTEL\_EXPORTER\_OTLP\_HEADERS** | Sets headers sent to the OTLP exporter. |
| **OTEL\_EXPORTER\_OTLP\_PROTOCOL** | Sets the OTLP transport protocol. |
| **OTEL\_LOGS\_EXPORTER** | Selects the OpenTelemetry logs exporter. |
| **OTEL\_LOG\_ASSISTANT\_RESPONSES** | Controls logging of assistant response text in OpenTelemetry events. |
| **OTEL\_LOG\_RAW\_API\_BODIES** | Controls logging of raw API request and response bodies. |
| **OTEL\_LOG\_TOOL\_CONTENT** | Controls logging of tool input and output content. |
| **OTEL\_LOG\_TOOL\_DETAILS** | Controls logging of detailed tool metadata. |
| **OTEL\_LOG\_USER\_PROMPTS** | Controls logging of user prompt text. |
| **OTEL\_METRICS\_EXPORTER** | Selects the OpenTelemetry metrics exporter. |
| **OTEL\_METRICS\_INCLUDE\_ACCOUNT\_UUID** | Controls whether account UUID is attached to metrics. |
| **OTEL\_METRICS\_INCLUDE\_ENTRYPOINT** | Controls whether the session entrypoint is attached to metrics. |
| **OTEL\_METRICS\_INCLUDE\_RESOURCE\_ATTRIBUTES** | Controls whether OTEL\_RESOURCE\_ATTRIBUTES are copied to metric labels. |
| **OTEL\_METRICS\_INCLUDE\_SESSION\_ID** | Controls whether session ID is attached to metrics. |
| **OTEL\_METRICS\_INCLUDE\_VERSION** | Controls whether Claude Code version is attached to metrics. |
| **OTEL\_METRIC\_EXPORT\_INTERVAL** | Sets the OpenTelemetry metric export interval. |
| **OTEL\_RESOURCE\_ATTRIBUTES** | Adds resource attributes to OpenTelemetry data. |
| **SLASH\_COMMAND\_TOOL\_CHAR\_BUDGET** | Sets the metadata character budget exposed to the Skill tool; the legacy name remains accepted. |
| **TASK\_MAX\_OUTPUT\_LENGTH** | Sets the output limit for subagent results before they are saved to disk. |
| **USE\_BUILTIN\_RIPGREP** | Chooses bundled ripgrep or a system-installed rg binary. |

</details>

<details>
<summary><strong>Deprecated or No-Op Environment Variables</strong></summary>

These names can appear in older setup guides or shell profiles. They are kept here for troubleshooting, but they should not be treated as current configuration controls.

| Older variable | Current note |
| --- | --- |
| **ANTHROPIC\_SMALL\_FAST\_MODEL** | Deprecated background-model variable; use ANTHROPIC\_DEFAULT\_HAIKU\_MODEL. |
| **ENABLE\_PROMPT\_CACHING\_1H\_BEDROCK** | Deprecated alias; use ENABLE\_PROMPT\_CACHING\_1H. |
| **CLAUDE\_CODE\_CONNECT\_TIMEOUT\_MS** | Removed and no longer changes behavior; use API\_TIMEOUT\_MS for request timing. |
| **CLAUDE\_CODE\_MAX\_SUBAGENTS\_PER\_SESSION** | Removed and no longer changes behavior; current limits use concurrency and spawn-depth controls. |
| **CLAUDE\_CODE\_ENABLE\_AUTO\_MODE** | Compatibility variable with no current effect; auto mode is available through permission modes. |
| **CLAUDE\_CODE\_ENABLE\_OPUS\_4\_7\_FAST\_MODE** | Removed fast-mode rollout variable. |
| **CLAUDE\_CODE\_OPUS\_4\_6\_FAST\_MODE\_OVERRIDE** | No-op compatibility variable from an older fast-mode rollout. |

</details>

## Older, Removed, and Replaced Command Names

Older tutorials and screenshots can mention commands that no longer belong in the current A-Z list. Use the current alternative when one exists.

| Old command | Use now |
| --- | --- |
| **/pr-comments [PR]** | Ask Claude directly to inspect pull-request comments, or use the current code-review/GitHub workflow. |
| **/tag** | Legacy command name; do not rely on it in current installations. |
| **/ultraplan** | Use Plan Mode through **/plan**. |
| **/vim** | Set Editor mode through **/config**. |

## Common Workflows

### Start a New Repository

```
/init
/status
/model
```

Create project guidance, confirm the environment, and choose the model before starting work.

### Understand an Unfamiliar Codebase

```
/status
/context
/plan map the project structure and main entry points
```

Check the session, inspect loaded context, and plan the investigation before editing.

### Review a Pull Request

```
/code-review high 123
/security-review
/diff
```

Run a correctness review, check security-sensitive changes, and inspect the final diff.

### Prepare a Safe Refactor

```
/review
/plan refactor the auth flow without changing behavior
/diff
```

Review the current state, plan the refactor, then inspect the resulting change.

### Manage a Long Session

```
/context
/compact keep decisions and unresolved issues
/usage
```

Check what is filling context, compact deliberately, and review current usage.

### Run a Multi-File Change

```
/review
/code-review --fix
/batch rename OldThing NewThing
```

Review first, apply review fixes where appropriate, then fan out a large repetitive change.

### Debug a Failure

```
/debug trace the failing checkout flow
/review
/diff
```

Collect debugging information, review the change, and inspect the resulting patch.

### Switch Between Tasks

```
/rename feature-auth
/clear
/resume feature-auth
```

Name a conversation, start a fresh task, then return to the earlier session later.

### Set Up and Use MCP

```
/mcp
/mcp__github__list_prs
```

Configure or authenticate the server, then run a prompt published by that server.

### Work Across Devices

```
/remote-control
/remote-env
/teleport
```

Expose a local session remotely, choose a cloud environment, or pull a web session back to the terminal.

### Review Usage and Limits

```
/usage
/cost
/stats
```

Open the usage view and its cost or statistics tabs.

### Start a Headless One-Off Task

```
claude -p "review this diff and list risks"
```

Run one non-interactive task and return the result to the shell.

### Reduce Repetitive Permission Prompts

```
/fewer-permission-prompts
/permissions
/hooks
```

Find common read-only calls, adjust rules, and inspect hook behavior.

### Work Toward a Clear Goal

```
/goal fix the failing checkout test and stop after tests pass
/context
/review
```

Give Claude a completion condition, then monitor context and review the result.

## Custom, Community, and Internal Command Names

These names are kept for lookup because they can appear in source-oriented references, custom command packs, community workflows, or older material. They are not part of the current built-in A-Z list.

| Name | Where it can appear |
| --- | --- |
| **/ant-trace** | Internal tracing name seen in source-oriented references. |
| **/backfill-sessions** | Internal session-data maintenance name. |
| **/break-cache** | Internal cache-maintenance name. |
| **/bridge** | Older or internal bridge-session name. |
| **/bridge-kick** | Older or internal bridge restart name. |
| **/brief** | Non-standard brief-output command name. |
| **/bughunter** | Community or experimental bug-finding workflow name. |
| **/commit** | Common community custom command for generating and creating a commit. |
| **/commit-push-pr** | Common custom workflow that commits, pushes, and opens a PR. |
| **/ctx\_viz** | Internal context-debugging name. |
| **/debug-tool-call** | Internal tool-call debugging name. |
| **/env** | Non-standard environment-inspection command name. |
| **/files** | Non-standard context-file listing command name. |
| **/fix-pipeline** | Community CI repair command name. |
| **/good-claude** | Easter-egg or experimental name found in source-oriented lists. |
| **/init-verifiers** | Experimental verifier-setup name. |
| **/issue** | Community GitHub issue command name. |
| **/lint** | Common community custom command for lint workflows. |
| **/merge-to-main** | Community merge workflow name. |
| **/mock-limits** | Internal rate-limit testing name. |
| **/oauth-refresh** | Internal or older OAuth refresh name. |
| **/perf-issue** | Internal performance-reporting name. |
| **/pr** | Common community custom command for pull-request creation. |
| **/pr\_comments** | Older internal underscore form associated with the removed /pr-comments command. |
| **/push** | Common community custom command for pushing the current branch. |
| **/remote-setup** | Older or experimental remote-session setup name. |
| **/reset-limits** | Internal rate-limit testing name. |
| **/session** | Non-standard session-management UI name found in older references. |
| **/summary** | Non-standard session-summary name found in older references. |
| **/thinkback** | Internal thinking-analysis name. |
| **/thinkback-play** | Internal animated thinking-replay name. |
| **/vitest** | Community custom command for Vitest workflows. |
| **/x402** | Experimental integration name found in source-oriented lists. |

## FAQ

<details>
<summary><strong>What is the difference between a slash command and a CLI command in Claude Code?</strong></summary>

A slash command starts with `/` and runs inside an active Claude Code session. A CLI command or flag runs in your shell, such as `claude -p`, `claude update`, or `claude --model sonnet`.

</details>

<details>
<summary><strong>How do I see all commands available in my Claude Code installation?</strong></summary>

Type `/` on an empty prompt and start typing to filter the command menu. The menu reflects commands, skills, plugins, and MCP prompts available in that installation, subject to platform, account, provider, and policy restrictions.

</details>

<details>
<summary><strong>What is the difference between /clear and /compact?</strong></summary>

`/clear` starts a new conversation with empty conversational context. `/compact` summarizes the current conversation so you can continue the same task with less context pressure.

</details>

<details>
<summary><strong>What does /plan do?</strong></summary>

`/plan` enters Plan Mode and can take an optional task description. Use it when you want Claude to inspect and plan before making changes.

</details>

<details>
<summary><strong>How do I create custom commands?</strong></summary>

Create a Claude Code skill or command definition in the appropriate project or user configuration directory. Custom skills can appear in the `/` menu and can accept arguments. Use `/reload-skills` after changing skill files during a running session.

</details>

<details>
<summary><strong>Can MCP servers add slash commands?</strong></summary>

Yes. MCP servers can publish prompts that appear as commands in the form `/mcp__servername__promptname`. The exact list depends on the servers connected to your installation.

</details>

<details>
<summary><strong>What is the difference between /doctor and /status?</strong></summary>

`/doctor` runs a diagnostic checkup and can propose fixes. `/status` shows current version, model, account, connectivity, and session information.

</details>

<details>
<summary><strong>How do I review a pull request now that /pr-comments is gone?</strong></summary>

Ask Claude directly to inspect the pull-request comments, or use `/code-review` or `/review` for the review workflow. Use the GitHub App or GitHub CLI integration when the task needs repository or PR access.

</details>

<details>
<summary><strong>Can Claude Code run non-interactively in CI or scripts?</strong></summary>

Yes. Use `claude -p "prompt"` for a non-interactive run. Flags such as `--output-format`, `--json-schema`, `--max-turns`, and `--max-budget-usd` control machine-readable and bounded runs.

</details>

<details>
<summary><strong>How do I change keyboard shortcuts?</strong></summary>

Run `/keybindings` to open the keybindings configuration. Built-in editing and terminal shortcuts can also depend on your terminal, operating system, and editor mode.

</details>

## Related Resources

- [Printable PDF](./claude-code-commands-cheat-sheet.pdf)
- [Claude Code Commands Cheat Sheet on ScriptByAI](https://www.scriptbyai.com/claude-code-commands-cheat-sheet/)
- [Claude Code Resource List](https://www.scriptbyai.com/claude-code-resource-list/)
- [Claude Code Timeline](https://www.scriptbyai.com/claude-code-timeline/)
- [OpenAI Codex Commands Cheat Sheet](https://www.scriptbyai.com/codex-commands-cheat-sheet/)
