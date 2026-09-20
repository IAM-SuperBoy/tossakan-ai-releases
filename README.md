<div align="center">
  <img src="assets/logo.png" alt="Tossakan logo" width="200" height="200" />

  <h1>Tossakan AI — Releases</h1>

  <p><strong>Same idea. Same room. Same tool. Everyone in sync.</strong></p>

  <p>
    <img alt="Platform" src="https://img.shields.io/badge/platform-macOS%20%7C%20Linux%20%7C%20Windows-5b8cff?style=flat-square" />
    <img alt="Release" src="https://img.shields.io/badge/release-latest-7ee3c3?style=flat-square" />
    <img alt="License" src="https://img.shields.io/badge/distribution-binaries%20only-9aa4b8?style=flat-square" />
  </p>
</div>

---

> [!NOTE]
> This repository ships **release binaries only**. The application source code lives in a
> separate private repository. GitHub automatically attaches **"Source code (zip)"** and
> **"Source code (tar.gz)"** links to every release — those are auto-generated snapshots of
> **this repository's own files** (this README + assets), **not** the application's source
> code. Safe to ignore.

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

Pass `-y`/`--yes` to skip the confirmation prompt. `tossakan.sh update` automatically remembers whether you originally installed using `curl` or `gh`, and downloads from the correct release repository. You can also explicitly override them if needed (e.g. `tossakan.sh update gh`).

### Windows PowerShell

```powershell
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" update
```

Alternatively, you can always re-run the original install command above to update.

## Uninstall

### If you installed the web stack (chat + agent)

`tossakan.sh` (or `tossakan.ps1` on Windows) is already on disk under
`~/.local/share/tossakan-releases/` — no download needed:

```bash
~/.local/share/tossakan-releases/tossakan.sh uninstall
```

```powershell
& "$env:USERPROFILE\.local\share\tossakan-releases\tossakan.ps1" uninstall
```

Both stop the running web stack first, then remove the release install and the PATH/completion
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
| macOS | Apple Silicon (arm64) |
| Linux | x86_64, arm64 |
| Windows | x86_64, arm64 |

---

## What is Tossakan?

Tossakan turns an AI assistant into a **shared team resource** instead of a single-player tool.
A central service holds the credentials and the project context; a team connects to it through a
**web app in the browser** — no install needed. A whole group — engineers, product managers, and
other business stakeholders alike — sees the **same** conversation, the **same** list of work in
progress, and the **same** AI output as it happens. A stakeholder doesn't need to read code to
follow a decision, ask a question, or steer scope — they read the same shared conversation a
developer is already working in, from the same browser tab.

> **The single biggest benefit:** an AI assistant stops being a private, single-player tool and
> becomes a shared team resource — visible, joinable, and auditable by the whole team, not just
> the person typing.

## How a request flows

1. A developer or stakeholder sends a request in a shared channel, from the browser.
2. The shared agent service picks it up — everyone in the channel sees the same conversation.
3. Complex work is captured as a **plan** made of steps with explicit dependencies.
4. Independent steps (or long research) can run as **isolated helper tasks** so they never block
   or crowd out the main conversation.
5. The AI uses real tools — editing files, tracking tickets, checking in code, messaging the
   team, browsing the web — against a choice of AI models.
6. The output lands back in the shared channel, visible to everyone, and becomes part of the
   durable record.

## Project → Channel → Topic

Work is organized in three nested levels:

```
Project                    ← the overall codebase/workspace
└── Channel                ← a shared room the whole team watches (e.g. #general, #payments)
    └── Topic              ← a focused side-thread inside a channel
```

- A **Project** is the outermost scope — everything below belongs to one project.
- A **Channel** is a shared room within a project. Everyone connected to it — developers and
  stakeholders alike — sees the same live conversation and the same list of work in progress.
- A **Topic** is a focused side-thread *inside* a channel — a way to branch off exploratory work
  (e.g. "try approach B") without derailing or losing the channel's main conversation.

**Topic and "idea" are the same thing, two names for one level:** *Topic* is the user-facing name
you see in the UI; *idea* is the same concept's internal/technical name (used in commands like
`/idea <name>` to create or switch topics, and in the underlying data model). There's no
separate hidden layer — when you switch to a topic, you are switching the active "idea" the
channel is working on. Shared memory follows this same hierarchy too, scoped from narrowest to
broadest: topic (idea) → channel → project → global.

### Your own space, invite others in

By default, each user gets their **own channel** — a personal space to work in. When something
important comes up that needs more than one person, you can **invite anyone into your channel**
to work on it together — the same shared conversation, plan, and results everyone in that
channel already sees. There's no separate "shared mode" to switch into: a personal channel and a
team channel are the same concept, just with a different guest list.

> **Coming soon:** fine-grained **permissions** for who can do what inside a shared channel — this
> is on the roadmap and not yet available.

## Where to run it

Tossakan runs in two modes — pick the one that matches how much of the "collaborative" story you want:

| | **Local** (on your own machine) | **Server** (deployed centrally) |
|---|---|---|
| Feels like | A regular coding agent — just you | A regular coding agent by default — becomes a shared team resource once you invite others |
| Who sees the conversation | Only you | Only you, until you invite others into that channel — then everyone invited, in real time |
| Access | Web browser | Web browser, from anywhere |
| State survives disconnect | No — tied to your local session | Yes — the server keeps running and keeps the record |
| Best for | Solo experimentation, personal workflow | Fully collaborative AI teamwork across a whole team |

Installing locally is the fastest way to try Tossakan the same way you'd try any coding agent.
Installing on a server unlocks the full collaborative model described in this README — a channel
you can invite the whole team, technical or not, into to watch and join from a browser.

### Why server mode's persistence matters

| Benefit | What it means in practice |
|---|---|
| 🔌 **Disconnect anytime, work keeps going** | Close your laptop or lose your connection mid-task — the agent keeps running on the server. Reconnect later (same client or a different one) and the finished result is waiting for you. |
| 🔁 **Server restarts don't lose your place** | If the server process itself stops and comes back, in-flight plans and tasks are automatically picked back up — you don't have to remember or re-explain where you left off. |
| 🧑‍🤝‍🧑 **One shared source of truth** | Every teammate reconnecting sees the exact same conversation and results — nobody is stuck with a stale local copy or has to re-ask what happened while they were away. |
| 🕵️ **Nothing is lost to a cleared screen** | Clearing what a client displays only trims the *view* — the durable record on the server is untouched and still there to look back on. |
| 📈 **A growing, searchable history** | Because the record lives on the server rather than in any one person's session, it accumulates into a full project history instead of resetting every time someone closes their app. |

## Architecture — what lives on the server vs. what you access from a client

```mermaid
flowchart TB
    WEB("🌐 Web app<br/>runs in a browser")

    WEB <-->|"connect / disconnect, any time"| SVC

    subgraph SVC["Agent server — always on, keeps running and keeps the record"]
        direction TB
        LOCAL("💻 Local server<br/>on your own machine<br/>just you")
        SHARED("☁️ Shared server<br/>deployed centrally<br/>whole team connects")
        REC("🗄️ Durable record<br/>conversation, tasks, and results<br/>kept independently of any client")
        LOCAL --> REC
        SHARED --> REC
    end

    classDef client fill:#5b8cff,stroke:#3a5fd1,color:#ffffff,rx:20,ry:20
    classDef local fill:#7ee3c3,stroke:#3fae8e,color:#0a3d31,rx:20,ry:20
    classDef shared fill:#ffb86b,stroke:#d1873a,color:#3d2405,rx:20,ry:20
    classDef record fill:#c9a6ff,stroke:#8a5fd1,color:#2b0a4d,rx:20,ry:20
    classDef zone fill:#f5f7ff,stroke:#5b8cff,color:#1a2a5e

    class WEB client
    class LOCAL local
    class SHARED shared
    class REC record
    class SVC zone
```

Whether the agent runs as a **local server** on your own machine or a **shared server** deployed
centrally for the team, the same web app connects to it the same way — only who else can join
differs. Either way, the server is the thing that keeps a submitted task running and keeps the
durable record, not the client.

Everything a client shows is a **view** onto state that actually lives in the server zone. A
user can disconnect the moment a task is submitted and reconnect later — from the same client or
a different one — to see the finished result. Clearing the visible conversation (starting fresh
context) only trims what a client shows going forward — it does not touch the durable record in
the server zone, which stays available to look back on.

## Core building blocks

### Collaboration

| | |
|---|---|
| 🧵 **Channels & Topics** | A channel is a shared room; a topic is a focused side-thread inside it — branch off exploratory work without losing the main conversation. See [Project → Channel → Topic](#project--channel--topic) below. |
| 🧩 **Sub-agents & delegation** | Delegate a piece of work to a sub-agent that runs it separately — long research or a big task never blocks or crowds out the main conversation. |
| 🗂️ **Trackable plans & tasks** | Work is captured as a plan made of tracked tasks with explicit dependencies (todo → in progress → done) — independent tasks run in parallel, dependent ones wait. |
| 🤖 **Choice of AI models** | Anthropic (Claude) · OpenAI (GPT) · Google (Gemini) · Amazon Bedrock (incl. Bedrock Mantle) · Microsoft Azure OpenAI · DeepSeek · Meta (Muse Spark) · GitHub Copilot · self-hosted/local (Ollama). |
| 🛠️ **Real tools, not just chat** | The AI edits files, tracks tickets, checks in code, sends team messages, and browses the web — not just suggestions. |
| 📖 **Reusable playbooks** | Named, repeatable playbooks for recurring work (planning, reviewing, looking things up). |
| 🧠 **Shared memory** | Facts saved at four nested levels (topic → channel → project → global), narrowest match wins. |
| 🕓 **Full historical record** | Every message, decision, and AI action is a persistent, searchable record — not a disappearing chat. |
| 🌍 **Multi-language support** | Works in any language you write in — the AI's response language follows whichever LLM/model is active, since language handling varies model to model. |
| 🔐 **Google & GitHub SSO** | Sign in with your existing Google or GitHub account — no separate credentials to manage for the team. |

### Insight & tooling

| | |
|---|---|
| 📊 **Usage stats** | Built-in stats on activity and AI usage across the channel — see what's happening at a glance. |
| 💰 **Per-person cost allocation** | Cost is broken down and attributed to each individual, not just a single team-wide total. |
| 🗺️ **Built-in code graph** | Indexes the codebase for structural lookups, and keeps the index updated as the code changes — no separate indexing step to remember. |

## Who sees what

| Role | What they see |
|---|---|
| **Everyone in the channel** | The same live conversation, plan/task progress, and AI output — regardless of how they connect. |
| **Org admin** | Full usage logs and conversation history across the organization, including per-person stats and cost allocation. |
| **Sub-agents** | Run isolated from the main conversation — their detailed work doesn't clutter the shared thread, only the result does. |
| **The AI** | The same shared project context and credentials every team member is already working against — no separate, siloed setup per person. |

## Durable record

Every message, decision, and AI action is kept as a persistent record per channel — not an
ephemeral chat session. Planned ahead: semantic search over past discussion, and a full audit
trail of AI actions.

---

<div align="center">
  <sub>Tossakan AI — same idea, same room, same tool, everyone in sync.</sub>
</div>
