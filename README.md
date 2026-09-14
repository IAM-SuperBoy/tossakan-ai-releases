<div align="center">
  <img src="assets/logo.png" alt="Tossakan logo" width="200" height="200" />

  <h1>Tossakan AI — Releases</h1>

  <p><strong>Collaborative AI teamwork — available from a web browser and a terminal.</strong></p>

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
gh release download latest --repo IAM-SuperBoy/tossakan-ai-releases -p 'install.sh' --output - | sh
```

**Option B — curl:**
```bash
curl -fsSL https://github.com/IAM-SuperBoy/tossakan-ai-releases/releases/latest/download/install.sh | sh
```

### Windows PowerShell

**Option A — GitHub CLI:**
```powershell
gh release download latest --repo IAM-SuperBoy/tossakan-ai-releases -p 'install.ps1' --output install.ps1; .\install.ps1
```

**Option B — irm:**
```powershell
irm https://github.com/IAM-SuperBoy/tossakan-ai-releases/releases/latest/download/install.ps1 | iex
```

## Update

Re-run the install command to update to the latest release.

## Uninstall

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
**web app in the browser** (no install needed) or a **terminal-based client** — either way, a
whole group — engineers, product managers, and other business stakeholders alike — sees the
**same** conversation, the **same** list of work in progress, and the **same** AI output as it
happens. A stakeholder doesn't need to read code or open a terminal to follow a decision, ask a
question, or steer scope — they read the same shared conversation a developer is already working
in, from whichever way they prefer to connect.

> **The single biggest benefit:** an AI assistant stops being a private, single-player tool and
> becomes a shared team resource — visible, joinable, and auditable by the whole team, not just
> the person typing.

## How a request flows

1. A developer or stakeholder sends a request in a shared channel (from the browser or the terminal).
2. The shared agent service picks it up — everyone in the channel sees the same conversation.
3. Complex work is captured as a **plan** made of steps with explicit dependencies.
4. Independent steps (or long research) can run as **isolated helper tasks** so they never block
   or crowd out the main conversation.
5. The AI uses real tools — editing files, tracking tickets, checking in code, messaging the
   team, browsing the web — against a choice of AI models.
6. The output lands back in the shared channel, visible to everyone, and becomes part of the
   durable record.

## Core building blocks

### Collaboration

| | |
|---|---|
| 🧵 **Channels & Topics** | A channel is a shared room; a topic is a focused side-thread inside it — branch off exploratory work without losing the main conversation. |
| 🌐💻 **Two ways to connect** | The same service backs a browser-based web app and a terminal client — pick whichever fits; history is identical either way. |
| 🧩 **Sub-agents & delegation** | Delegate a piece of work to a sub-agent that runs it separately — long research or a big task never blocks or crowds out the main conversation. |
| 🗂️ **Trackable plans & tasks** | Work is captured as a plan made of tracked tasks with explicit dependencies (todo → in progress → done) — independent tasks run in parallel, dependent ones wait. |
| 🤖 **Choice of AI models** | Anthropic (Claude) · OpenAI (GPT) · Google (Gemini) · Amazon Bedrock (incl. Bedrock Mantle) · Microsoft Azure OpenAI · DeepSeek · Meta (Muse Spark) · GitHub Copilot · self-hosted/local (Ollama). |
| 🛠️ **Real tools, not just chat** | The AI edits files, tracks tickets, checks in code, sends team messages, and browses the web — not just suggestions. |
| 📖 **Reusable playbooks** | Named, repeatable playbooks for recurring work (planning, reviewing, looking things up). |
| 🧠 **Shared memory** | Facts saved at four nested levels (topic → channel → project → global), narrowest match wins. |
| 🕓 **Full historical record** | Every message, decision, and AI action is a persistent, searchable record — not a disappearing chat. |
| 🌍 **Multi-language support** | Works in any language you write in — the AI's response language follows whichever LLM/model is active, since language handling varies model to model. |

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
  <sub>Tossakan AI — collaborative AI, available from both a web browser and a terminal.</sub>
</div>
