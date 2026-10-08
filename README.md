<div align="center">
  <img src="assets/logo.png" alt="Tossakan logo" width="200" height="200" />

  <h1>Tossakan AI — Releases</h1>

  <p><strong>Same idea. Same room. Same tool.</strong></p>
  <p><strong>The world's most advanced AI harness.</strong></p>

  <p>
    <img alt="Platform" src="https://img.shields.io/badge/platform-macOS%20%7C%20Linux%20%7C%20Windows-5b8cff?style=flat-square" />
    <img alt="Release" src="https://img.shields.io/badge/release-latest-7ee3c3?style=flat-square" />
    <img alt="License" src="https://img.shields.io/badge/distribution-binaries%20only-9aa4b8?style=flat-square" />
  </p>
</div>

> **This release is `single_user`.** The public download is a full solo agent harness (web UI,
> plans, tasks, tools, A2A owner controls). It does **not** include multi-account SSO or inviting
> separate teammates. Team / `multi_users` is a separate licensed mode — see
> [What is Tossakan?](#what-is-tossakan).

---

## Why Tossakan?

**An AI workforce that works while you work on something else.**

- 🤖 **Agents everywhere** — one interface to run as many ideas and agents as you need: a main
  conversation, on-demand specialist sub-agents, and background task agents, all running in
  parallel in ONE tool. Agents can even call other agents (A2A) to hand off work with zero human
  in the middle.
- 💾 **Nothing ever gets lost** — every message, file change, and agent decision is stored and
  searchable forever, with the full reasoning chain behind each one.
- 💰 **See exactly what you're spending** — cost is tracked and shown at every level: idea,
  channel, project, task, sub-task, and agent, so you always know where the spend is going.
- ⚡ **Fast everywhere** — a modern web UI and an equally polished terminal UI, both rendered
  locally so nothing feels sluggish.
- 🎯 **Never blocked** — kick off long-running tasks and keep working on something else; tasks
  **survive crashes, restarts, and power outages** and pick up right where they left off.
- 🗂️ **Git-for-AI-work task orchestration** — declare dependencies once, run independent work in
  parallel, and export any plan to re-run anywhere, including CI/CD.
- 🔍 **Complete transparency** — timestamped, auditable decision trails make debugging and
  compliance painless.
- 🧠 **Isolated task memory** — every task gets its own context, so spawning 100 of them never
  bloats or slows down your main conversation.
- 🔄 **Swap models like batteries** — switch between Claude, Gemini, GPT, and others at the
  project, idea, or task level with zero rewrites.
- 👥 **Built for real teams** — shared, async-friendly workspaces where everyone sees not just
  what an agent did, but *why*.

> **TL;DR:** Agents that run in parallel, remember everything, show you exactly what they cost,
> and never lose your work — even across a crash.

---

## Install

### macOS / Linux

**Option A — GitHub CLI:**
```bash
gh release download latest --repo IAM-SuperBoy/tossakan-ai-releases -p 'install.sh' --output - | sh -s -- gh
```

**Option B — curl:**
```bash
curl -fsSL https://github.com/IAM-SuperBoy/tossakan-ai-releases/releases/latest/download/install.sh | sh
```

### Windows PowerShell

**Option A — GitHub CLI:**
```powershell
gh release download latest --repo IAM-SuperBoy/tossakan-ai-releases -p 'install.ps1' --output install.ps1; .\install.ps1 -Tool gh
```

**Option B — irm:**
```powershell
irm https://github.com/IAM-SuperBoy/tossakan-ai-releases/releases/latest/download/install.ps1 | iex
```

## Run

Once installed, start the whole stack (agent + web UI + browser-worker) with a single
command — the lifecycle script installed alongside the binaries:

### macOS / Linux

```bash
~/.local/share/tossakan-releases/tossakan.sh start
```

By default `start` blocks your terminal (Ctrl+C to stop) — pass `-d`/`--daemon` to run it in
the background and get your terminal back immediately:

```bash
~/.local/share/tossakan-releases/tossakan.sh start -d
```

Open your browser to the URL printed on start to use the web UI.

Manage the running stack with:

```bash
~/.local/share/tossakan-releases/tossakan.sh status    # check what's running
~/.local/share/tossakan-releases/tossakan.sh stop      # stop everything
~/.local/share/tossakan-releases/tossakan.sh resume    # stop then start (blocks; add -d to not block)
```

### Windows PowerShell

```powershell
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" start
```

By default `start` blocks your console (Ctrl+C to stop) — pass `-Daemon` (or `-d`) to run it
in the background and get your console back immediately:

```powershell
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" start -Daemon
```

```powershell
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" status
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" stop
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" resume
```

> **Note:** the web UI (Next.js + browser-worker) requires Node.js on your machine. If you
> installed mux only (option 1 during install), there is no web stack to run — use the
> terminal binary directly instead.

## Update

To update to the latest release, run `update` using the lifecycle script already on disk:

### macOS / Linux

```bash
~/.local/share/tossakan-releases/tossakan.sh update
```

Pass `-y`/`--yes` to skip the confirmation prompt. `tossakan.sh update` remembers whether you
originally installed with `curl` or `gh` and downloads from the matching release repository. You
can override that choice if needed (e.g. `tossakan.sh update gh`).

### Windows PowerShell

```powershell
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" update
```

Alternatively, re-run the original [install](#install) command to update.

## Uninstall

`tossakan.sh` (or `tossakan.ps1` on Windows) is already on disk under
`~/.local/share/tossakan-releases/` — no download needed:

```bash
~/.local/share/tossakan-releases/tossakan.sh uninstall
```

```powershell
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" uninstall
```

Both stop the running stack first, then remove the release install and the PATH/completion
entries the installer added. Pass `-y`/`-Yes` to skip the confirmation prompt (e.g. in CI).

### If `tossakan.sh`/`tossakan.ps1` is missing or damaged

Fall back to downloading the standalone uninstaller:

### macOS / Linux

**Option A — GitHub CLI:**
```bash
gh release download latest --repo IAM-SuperBoy/tossakan-ai-releases -p 'uninstall.sh' --output - | sh
```

**Option B — curl:**
```bash
curl -fsSL https://github.com/IAM-SuperBoy/tossakan-ai-releases/releases/latest/download/uninstall.sh | sh
```

### Windows PowerShell

**Option A — GitHub CLI:**
```powershell
gh release download latest --repo IAM-SuperBoy/tossakan-ai-releases -p 'uninstall.ps1' --output uninstall.ps1; .\uninstall.ps1
```

**Option B — irm:**
```powershell
irm https://github.com/IAM-SuperBoy/tossakan-ai-releases/releases/latest/download/uninstall.ps1 | iex
```

## Supported platforms

| OS | Architecture |
|---|---|
| macOS | Apple Silicon (arm64), Intel (x86_64) |
| Linux | x86_64, arm64 |
| Windows | x86_64, arm64 |

---

## What is Tossakan?

Tossakan is a character in the **Ramayana** and the **Ramakien** epic. He has **ten faces**, and
each face can think and act independently, with its own personality and characteristics. We use
this as an analogy for an **Agent Harness** in the AI world: each “face” is an independent agent
with a specific role or capability, while **Tossakan as a whole** coordinates them as a single
system.

In product terms, Tossakan is that harness: many specialized agents and views, one coordinated
system. Today it shines on software work — plans, tasks, tools, memory, and a web workspace
([Chat, FileView, Terminal, Browser, Plan, Task, SubAgent](#web-interface)) against a real
project. The same model is not limited to codebases; over time it can grow into a broader
personal assistant as well — different “faces” for different jobs, still one Tossakan.

### Public download (`single_user`)

The **public download** is **`single_user` only**: one person on their machine, or a private
server install still under a single-user license. You get the full agent capabilities — models,
tools, ideas, A2A owner controls, code graph — **without** multi-account SSO or inviting separate
teammates.

### Team mode (`multi_users`) — licensed separately

**Team / `multi_users`** is **not** what this download installs. It is licensed separately and
turns the same product into a **shared team resource**: a central service holds credentials and
project context; engineers, PMs, and other stakeholders open the **same** web app, see the
**same** conversation and work in progress, and steer from one browser tab without needing to
read the code. Sections below mark team-only behavior with *(multi_users/team only)*.

> 🚧 **Actively in development.** Team mode is where we're focusing real energy right now — the
> goal is to turn Tossakan into the everyday, shared coding assistant a whole engineering org
> relies on, not just a solo tool. We're looking for **developers** who want to help build it and
> **investors** who want to back it. If that's you, reach out — we'd love to collaborate and get
> this into daily use for real teams doing real work.

> **Scope at a glance**
>
> | | **Public download (`single_user`)** | **Team (`multi_users`)** |
> |---|---|---|
> | Who uses it | You | You + invited teammates (SSO) |
> | What you get | Full agent harness + web UI | Same harness + shared rooms + per-person audit/cost |
> | Biggest upside | Powerful solo coding agent in the browser | One shared source of truth for the whole team |
> | In this release? | **Yes — this download** | **No — separate license** |

## How a request flows

The **agent loop is the same** in single-user and team mode. What changes is *who is watching*.

### Always (single-user and team)

1. You send a request from the **web UI** (or terminal client) on a **channel** / **idea**.
2. The agent service picks it up and runs the turn.
3. Complex work becomes a **plan** of steps with explicit dependencies.
4. Independent steps (or long research) can run as **isolated tasks / sub-agents** so they never
   block or crowd the main conversation.
5. The AI uses real tools — files, tickets, git, messages, browsing — against your chosen models.
6. Output lands back on that idea and becomes part of the **durable record**.

### Additionally in team mode *(multi_users only — not this download)*

- Everyone invited to the **channel** sees the same live conversation and plan/task progress.
- Stakeholders can follow decisions from **Chat / Plan / Task** without a separate hand-off.
- Org admins can attribute usage and cost per signed-in person (SSO).

## Project → Channel → Idea

Work is organized in three nested levels:

```
Project                    ← the overall codebase/workspace
└── Channel                ← a room (e.g. #general, #payments)
    └── Idea               ← a focused side-thread inside a channel
```

- A **Project** is the outermost scope — everything below belongs to one project.
- A **Channel** is a room within a project. In **`single_user`** it is your working room; in
  **`multi_users` / team** everyone invited to it sees the same live conversation and work in
  progress.
- An **Idea** is a focused side-thread *inside* a channel — branch off exploratory work
  (e.g. "try approach B") without derailing the channel's main conversation. Ideas are also the
  unit you can expose as A2A agents.

Create or switch ideas from the client (see [Useful commands](#useful-commands)). Shared memory
follows the same hierarchy, narrowest to broadest: idea → channel → project → global.

## Agent-to-Agent (A2A)

Any idea can optionally become a standalone agent — a thing anyone can call, not just you. The
owner sets visibility to **public** and anyone/any agent that can reach it may discover and call
it; set to **private** (the default) and only the owner can. Owner also controls the published
goal, which skills are allowed, and concurrency — closed by default until opted in. It's one
feature among many; see [Useful commands](#useful-commands) for how to open its settings from
the client.

## Where to run it

Hosting is separate from license mode. You can run **`single_user`** on your laptop **or** on a
private server. Inviting teammates still requires a **`multi_users` / team** license — a server
alone does not unlock SSO or invites on the public download.

| | **Local** (your machine) | **Server** (deployed centrally) |
|---|---|---|
| Feels like | A regular coding agent on your desk | Same agent, reachable from other devices |
| Who sees the conversation (`single_user`) | Only you | Only you (still one license identity) |
| Who sees the conversation (`multi_users`) | N/A for typical solo laptop use | You + people you invite into the channel (SSO) |
| Access | Web browser on this machine | Web browser from anywhere that can reach the host |
| Process keeps running after you leave | Only while this machine stays on | Yes — the host keeps the process and durable record |
| Best for | Solo try-out and day-to-day personal workflow | Always-on agent; team collaboration when licensed |

**Local** is the fastest way to try Tossakan like any other coding agent. **Server** keeps the
process (and [durable record](#durable-record)) running when your laptop sleeps. Shared rooms and
invites are a **team-license** capability — see [What is Tossakan?](#what-is-tossakan).

## Web interface

Tossakan is used primarily through a **web interface** in the browser. After `start`, open the
URL printed in the terminal — no separate desktop app is required for day-to-day work.

In **`single_user`**, that browser session is yours alone. In **`multi_users` / team**, everyone
invited to the channel sees the same idea, channel, and agent session.

### Why web-first

Tossakan also ships a terminal UI (TUI), and we keep it fully up-to-date — but **this release
focuses on the web interface**, and that's a deliberate choice, not a gap:

- 🖼️ **Richer, multi-pane UX** — Chat, FileView, Terminal, Browser, Plan, Task, and SubAgent
  views side-by-side in one workspace. A terminal can't lay out that much structured, visual
  information at once without becoming cramped.
- 🖱️ **Direct manipulation** — click, drag, resize panes, scroll rich diffs, preview files and
  embedded browser pages in place. The web UI supports interactions a text terminal fundamentally
  can't (inline images, rendered markdown, live file trees, an actual embedded browser).
- 👥 **Built for sharing** — in team mode, multiple people opening the *same* live session only
  makes sense with a shareable browser URL; a terminal session isn't something you hand a
  teammate.
- 🚀 **Faster iteration on quality** — investing one high-fidelity surface lets the team polish UX
  details (loading states, live status, inline previews) much faster than maintaining equivalent
  polish across two very different UI toolkits.

**The TUI isn't abandoned** — it's maintained and functional for anyone who prefers the terminal
or is on a mux-only install — but it intentionally has a **more limited UX** than the web client,
and is not bundled with this release. If you want the terminal client, see the note under
[Run](#run).

The web UI is a multi-pane workspace. Core views:

| View | What it is for |
|---|---|
| **Chat** | Live conversation with the agent — messages, tool activity, and replies in one thread. |
| **FileView** | Browse and open project files in the browser without leaving the session. |
| **Terminal** | In-browser terminal attached to the workspace — run commands beside the agent. |
| **Browser** | Embedded browser the agent (and you) can drive — open pages and verify UI changes in place. |
| **Plan** | Structured plan for the current idea — ordered steps, dependencies, status, and progress. |
| **Task** | Individual tasks on that plan — running, waiting, done, or blocked. |
| **SubAgent** | Delegated sub-agents in isolation — their own transcript and status, without crowding main chat. |

Arrange and switch these views in the workspace so coding, browsing, planning, and chat stay
together. Follow along on **Chat** / **Plan** / **Task**, or pin **FileView**, **Terminal**, and
**Browser** next to the same conversation.

> **Install note:** the full web stack (chat UI + browser-worker) needs Node.js. If you installed
> mux only, use the terminal client instead — see the note under [Run](#run).

### `single_user` capabilities (this release)

This public download runs under a **`single_user`** license. Any SSO/login configuration is
cleared: there is no sign-in screen, no Google/GitHub/Okta button, and no separate team-member
accounts. Sign-in only gates *who* can connect — not what the agent can do.

Everything in [Core building blocks](#core-building-blocks) that is **not** marked
*(multi_users/team only)* works here: channels & ideas, A2A idea-agents, sub-agents, plans &
tasks, models, tools, playbooks, shared memory, historical record, multi-language support, and
the code graph. Usage stats are recorded and attributed to the single implicit user.

**Not available on the public `single_user` download:**

| | |
|---|---|
| 🔐 **SSO login (Google/GitHub/Okta)** | Disabled — `[auth]` is cleared regardless of config file contents. |
| 👥 **Multiple separate accounts** | No distinct signed-in identities under a `single_user` license. |
| 🧑‍💼 **Per-person usage/cost breakdown** | Everything rolls up to the one local user. |
| 📨 **Invite teammates** (`/invite`) | Needs separate identities — team license only. |

You get the full AI-agent toolset with minimal setup. Multi-account sign-in and invites are what
**`multi_users` / team** (separate license) adds — not something a server host alone unlocks on
this download.

### Team capabilities (`multi_users` / team only)

> **Not in the public download.** The following applies only with a `multi_users` / team license.

With team mode, each user gets their **own channel** by default — a personal space to work in.
When more than one person needs the same thread, **invite them into that channel**: same
conversation, plan, and results for everyone on the guest list. A personal channel and a team
channel are the same concept with a different roster — there is no separate "shared mode" switch.

SSO is what creates those separate signed-in identities in the first place. A `single_user`
install has no second identity to invite — see
[`single_user` capabilities](#single_user-capabilities-this-release) above.

> **Coming soon:** fine-grained **permissions** for who can do what inside a shared channel —
> on the roadmap, not yet available.

### Why the durable record matters (all license modes)

These benefits come from the app keeping a persistent record on the machine that hosts the
process. They apply on **`single_user`** and **`multi_users` / team** alike — they are not
exclusive to "server mode":

| Benefit | What it means in practice |
|---|---|
| 🔌 **Disconnect anytime, work keeps going** | Close the laptop or lose the connection mid-task — the agent keeps running on the host. Reconnect later (same client or another) and the finished result is waiting. |
| 🔁 **Restarts don't lose your place** | If the agent process stops and comes back, in-flight plans and tasks are picked up again — no need to re-explain where you left off. |
| 🧑‍🤝‍🧑 **One shared source of truth** *(multi_users/team only)* | Every teammate reconnecting sees the same conversation and results. Not applicable to `single_user` (no second person to share with). |
| 🕵️ **Nothing is lost to a cleared screen** | Clearing the client view only trims the *display* — the durable record stays intact. |
| 📈 **A growing, searchable history** | The record lives with the process, not one browser tab, so history accumulates instead of resetting when someone closes the app. |

Local vs server only changes *where* that process lives: a local install runs while your machine
is on; a server install keeps the same durability independent of any one laptop — see
[Where to run it](#where-to-run-it).

## Core building blocks

### Collaboration

| | |
|---|---|
| 🧵 **Channels & Ideas** | A channel is a room; an idea is a focused side-thread inside it — branch exploratory work without losing the main conversation. See [Project → Channel → Idea](#project--channel--idea). |
| 🤝 **Agent-to-Agent (A2A)** | Any idea can optionally become its own callable agent, on owner-controlled terms. See [Agent-to-Agent (A2A)](#agent-to-agent-a2a). |
| 🧩 **Sub-agents & delegation** | Delegate work to a sub-agent that runs separately — long research or a large task never blocks or crowds the main conversation. |
| 🗂️ **Trackable plans & tasks** | Work is a plan of tracked tasks with explicit dependencies (todo → in progress → done) — independent tasks run in parallel; dependents wait. |
| 🤖 **Choice of AI models** | Anthropic (Claude) · OpenAI (GPT) · Google (Gemini) · Amazon Bedrock (incl. Bedrock Mantle) · Microsoft Azure OpenAI · Nvidia OpenAI · DeepSeek · Meta (Muse Spark) · GitHub Copilot · self-hosted/local (Ollama). |
| 🧰 **Skills & MCP tool servers** | Extend the agent with installed skills/playbooks (`/skill`) and external MCP (Model Context Protocol) tool servers (`/mcp`) — add, enable, or disable them per project or channel. |
| 🛠️ **Real tools, not just chat** | The AI edits files, tracks tickets, checks in code, sends messages, and browses the web — not just suggestions. |
| 📖 **Reusable playbooks** | Named, repeatable playbooks for recurring work (planning, reviewing, looking things up). |
| 🧠 **Shared memory** | Facts at four nested levels (idea → channel → project → global); narrowest match wins. |
| 🕓 **Full historical record** | Every message, decision, and AI action is a persistent, searchable record — not a disappearing chat. |
| 🌍 **Multi-language support** | Works in the language you write in; response language follows the active LLM/model. |
| 🔐 **Google/GitHub/Okta SSO** *(multi_users/team only)* | Sign in with Google, GitHub, or Okta — no separate team credentials. **Not on the public `single_user` download** (no SSO screen on this release). |

### Insight & tooling

| | |
|---|---|
| 📊 **Usage stats** | Built-in stats on activity and AI usage at **idea** (`/stat`) and **channel** (`/channel stat`) scope — zoom from one idea out to the whole channel. |
| 💰 **Per-person cost allocation** *(multi_users/team only)* | Cost is broken down and attributed to each individual, not just a single team-wide total. |
| 🗺️ **Built-in code graph** | Indexes the codebase for structural lookups, and keeps the index updated as the code changes — no separate indexing step to remember. |

## Who sees what

| Role | What they see |
|---|---|
| **You (`single_user`)** | Your channels, ideas, plans, tasks, and AI output on this install. |
| **Everyone in the channel** *(multi_users/team)* | The same live conversation, plan/task progress, and AI output — regardless of how they connect. |
| **Idea owner (A2A)** | Controls whether that idea is an agent: enable/disable A2A, private vs public, goal, exposed skills, concurrency. Callers only get what the owner allow-lists. |
| **Remote A2A callers** | Only ideas the owner enabled (and, if public, exposed). They see the Agent Card and may invoke listed skills — nothing more. Private ideas require the authenticated owner. |
| **Org admin** *(multi_users/team)* | Usage logs and conversation history across the org, including per-person stats and cost. |
| **Sub-agents** | Isolated from the main conversation — detailed work stays off the main thread; the result comes back. |
| **The AI** | The project context and credentials configured for this install — one shared setup, not a siloed copy per person. |

## Durable record

Every message, decision, and AI action is kept as a persistent record per channel — not an
ephemeral chat session. See [Why the durable record matters](#why-the-durable-record-matters-all-license-modes)
for disconnect/resume behavior. Planned ahead: semantic search over past discussion, and a full
audit trail of AI actions.

---

## Setting up an LLM provider

Tossakan needs at least one LLM provider configured before it can respond. The first `start`
launches an interactive **setup wizard** that walks you through picking providers and entering
credentials — it writes `~/.tossakan/tossakan.toml`, so you only do this once. You can edit that
file by hand later using the same keys shown below.

| Provider | What you need | Notes |
|---|---|---|
| **AWS Bedrock (Converse)** | Nothing extra — uses your existing AWS credential chain (env vars, shared config profile, SSO, or an assumed role/IMDS) | Always available; no separate API key |
| **AWS Bedrock (Anthropic-native)** | Same AWS credential chain as above | Always available; unlocks the latest Claude-specific features via Bedrock |
| **AWS Bedrock Mantle** | Nothing required by default — auto-generates bearer tokens from your AWS credentials | Optional: `AWS_BEARER_TOKEN_BEDROCK` for a static key, `BEDROCK_MANTLE_BASE_URL` to override the endpoint, or `BEDROCK_MANTLE_ENABLED=false` to turn it off |
| **Anthropic (direct API)** | `ANTHROPIC_API_KEY` (starts with `sk-ant-…`) | |
| **OpenAI** | `OPENAI_API_KEY` (starts with `sk-…`) | Optional `OPENAI_BASE_URL` for a proxy/custom gateway |
| **Google Gemini** | `GOOGLE_API_KEY` (from Google AI Studio) | |
| **Azure OpenAI** | `AZURE_OPENAI_API_KEY` + `AZURE_OPENAI_ENDPOINT` (e.g. `https://<resource>.openai.azure.com`) | Both required |
| **Nvidia OpenAI** | `NVIDIA_OPENAI_API_KEY` (required) + `NVIDIA_OPENAI_ENDPOINT` (optional, defaults to `https://integrate.api.nvidia.com/v1`) | API key required; endpoint optional |
| **DeepSeek** | `DEEPSEEK_API_KEY` | Optional `DEEPSEEK_BASE_URL` for a proxy/self-hosted gateway |
| **Muse Spark (Meta AI)** | `MUSE_SPARK_API_KEY` | Fixed endpoint (`https://api.meta.ai/v1`) |
| **Ollama (local models)** | Nothing required | Optional `OLLAMA_BASE_URL` if your Ollama server isn't on `http://localhost:11434` |
| **GitHub Copilot** | `GITHUB_COPILOT_OAUTH_TOKEN` (or alias `COPILOT_GITHUB_TOKEN`) | Token env vars only on the public download. `install.sh` / `install.ps1` do **not** ship `copilot-login.sh` / `.ps1`. Use a token you already have, or the device-flow helper in the source tree (`scripts/copilot-login.sh` / `.ps1`) when you have repo access. |

Enable as many providers as you like — each configured provider appears in the model picker.
Switching models or providers is a dropdown choice, not a reconfiguration.


## Useful commands

Slash commands work the same in the web UI and the terminal. Type `/` in the chat input to open
the command palette, or run any of the commands below directly.

### Navigate workspace

| Command | What it does |
|---|---|
| `/channel` | List or switch channels inside the current project. |
| `/idea <name>` | Create or switch to an idea inside the current channel. |

### Agent & work

| Command | What it does |
|---|---|
| `/a2a` | Open A2A settings for the current idea — enable/disable, visibility, goal, exposed skills, concurrency. |
| `/a2a-conversation` | Open this idea's A2A conversations board (web client; terminal shows a not-yet-available notice). |
| `/a2a-directory` | Browse the directory of other A2A-enabled agents available to call. |
| `/plan` | Open the plan for the current idea — ordered steps, dependencies, and progress. |
| `/task` | Open the plan/task list for the current idea. |
| `/model` | Pick the AI model (and provider) for this idea. |
| `/effort` | Set how hard the agent should try on the next turn. |
| `/skill` | Browse and run installed skills / playbooks. |
| `/mcp` | Browse, add, enable/disable, or remove MCP (Model Context Protocol) servers, scoped to global, project, or channel. |
| `/agent` | Inspect or manage running sub-agents. |

### Memory, search & review

| Command | What it does |
|---|---|
| `/memory` | View or edit shared memory (idea → channel → project → global). |
| `/review` | Run a code review pass. |
| `/security-review` | Run a security-focused review. |
| `/stat` | Show session statistics for the **current idea**. |
| `/channel stat` | Channel-wide session statistics across **all ideas** in the channel. |

### Code graph

| Command | What it does |
|---|---|
| `/index-repo` | Index the whole repository into the built-in code graph (repeat until coverage converges, then sync). |
| `/index-stat` | Show code-graph coverage — files, symbols, stale entries, per-language breakdown, indexer counters. |
| `/index-reset` | Wipe the code graph for the current project (shows before/after status; does not auto-reindex). |

### Session

| Command | What it does |
|---|---|
| `/clear` | Clear the on-screen view (durable record is untouched). |
| `/compact` | Summarize older context to free room for new work. |
| `/permission` | Adjust tool-permission mode for this session. |
| `/invite` | Invite teammates into the current channel. *(multi_users/team only — not on the public `single_user` download.)* |
| `/logout` | Sign out. *(SSO / signed-in sessions; team mode.)* |

> Tip: the table above is the short day-to-day set, not every command. Team-only entries simply
> do not apply on `single_user`.

## Support

For issues or questions, contact: **iam.tossakan.ai@gmail.com**
