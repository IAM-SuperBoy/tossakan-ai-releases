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

## What is Tossakan?

Tossakan turns an AI assistant into a **shared team resource** instead of a single-player tool.
Work happens inside a channel the whole team — developers and non-technical stakeholders alike —
can watch, join, and pick up from, reachable from either a **web browser** or a **terminal**.

| | |
|---|---|
| 🧵 **Channels & Topics** | A channel is a shared room; a topic is a focused side-thread inside it — branch off exploratory work without losing the main conversation. |
| 🌐💻 **Two ways to connect** | The same service backs a browser-based web app and a terminal client — pick whichever fits; history is identical either way. |
| 🧩 **Isolated helper tasks** | Long research or a big piece of work runs as its own isolated task so it never crowds out the main conversation. |
| 🗂️ **Dependency-aware plans** | Work is captured as a plan of steps with explicit dependencies — independent steps run in parallel, dependent steps wait. |
| 🤖 **Choice of AI models** | Anthropic (Claude) · OpenAI (GPT) · Google (Gemini) · Amazon Bedrock · Microsoft Azure OpenAI · DeepSeek · Meta · self-hosted/local (Ollama). |
| 🛠️ **Real tools, not just chat** | The AI edits files, tracks tickets, checks in code, sends team messages, and browses the web — not just suggestions. |
| 📖 **Reusable playbooks** | Named, repeatable playbooks for recurring work (planning, reviewing, looking things up). |
| 🧠 **Shared memory** | Facts saved at four nested levels (topic → channel → project → global), narrowest match wins. |
| 🕓 **Full historical record** | Every message, decision, and AI action is a persistent, searchable record — not a disappearing chat. |

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

<div align="center">
  <sub>Tossakan AI — collaborative AI, available from both a web browser and a terminal.</sub>
</div>
