# 🧠 ThinkCheck × Hermes — 水晶之心

> 为开源智能体 [Hermes Agent](https://github.com/NousResearch/hermes-agent) 装上自我审视的"逻辑之眼"。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://python.org)
[![ThinkCheck 3.0](https://img.shields.io/badge/ThinkCheck-3.0-orange.svg)](https://github.com/luoxuejian000/hermes-agent)
[![Forked from NousResearch/hermes-agent](https://img.shields.io/badge/forked%20from-NousResearch%2Fhermes--agent-green.svg)](https://github.com/NousResearch/hermes-agent)

本项目是 NousResearch 出品的 [Hermes Agent](https://github.com/NousResearch/hermes-agent) 的增强分支。它在保留原项目所有强大能力（自我进化、三层记忆、广泛模型支持）的基础上，深度集成了我自研的 **ThinkCheck 3.0 推理评估引擎**。

**它的独特之处在于**：Hermes Agent 在生成文本后，会自动调用 ThinkCheck 进行“逻辑体检”，评估其推理质量（U统一性/D发展性/A对抗性/H和谐度），并给出通俗的改进建议。这使得“水晶之心”不止是一个能干的 Agent，更是一个能自我审视、持续进化的可靠伙伴。

---

## ✅ 与官方版本的核心区别

| 能力维度 | 官方 Hermes Agent | 🧠 水晶之心 (本仓库) |
| :--- | :--- | :--- |
| **推理质量评估** | ❌ 不支持 | ✅ 支持，提供U/D/A/H四维诊断报告 |
| **内容逻辑自检** | ❌ 不支持 | ✅ 支持，可自动发现并标注逻辑矛盾 |
| **概念漂移检测** | ❌ 不支持 | ✅ 支持，精确定位术语含义偏移 |
| **自我审视工具** | 无 | `thinkcheck_evaluate`，可被 Agent 自主调用 |

---

## 🧠 ThinkCheck 3.0 评估引擎

本仓库集成的 **ThinkCheck 3.0**，是一款基于晶脉哲学与谐振理论开发的AI推理质量诊断系统。

**四维评估指标**：

- **U (统一性)**：概念在文本中使用的语义一致性。
- **D (发展性)**：论证层次递进与新信息引入的节奏。
- **A (对抗性)**：文本内部逻辑矛盾的密度。
- **H (和谐度)**：综合前三项后得出的整体推理健康度。

---

## What is Hermes Agent?

Hermes Agent is a self-improving AI agent that creates skills from experience, improves them during use, and runs anywhere. It supports virtually every major model provider and works across CLI, Telegram, Discord, Slack, WhatsApp, Signal, and more — all from a single gateway process.

Use any model you want — [Nous Portal](https://portal.nousresearch.com), [OpenRouter](https://openrouter.ai) (200+ models), [NovitaAI](https://novita.ai), [NVIDIA NIM](https://build.nvidia.com), [Xiaomi MiMo](https://platform.xiaomimimo.com), [z.ai/GLM](https://z.ai), [Kimi/Moonshot](https://platform.moonshot.ai), [MiniMax](https://www.minimax.io), [Hugging Face](https://huggingface.co), OpenAI, or your own endpoint. Switch with `hermes model` — no code changes, no lock-in.

| | |
| :--- | :--- |
| **A real terminal interface** | Full TUI with multiline editing, slash-command autocomplete, conversation history, interrupt-and-redirect, and streaming tool output. |
| **Lives where you do** | Telegram, Discord, Slack, WhatsApp, Signal, and CLI — all from a single gateway process. Voice memo transcription, cross-platform conversation continuity. |
| **A closed learning loop** | Agent-curated memory with periodic nudges. Autonomous skill creation after complex tasks. Skills self-improve during use. FTS5 session search with LLM summarization for cross-session recall. [Honcho](https://github.com/plastic-labs/honcho) dialectic user modeling. Compatible with the [agentskills.io](https://agentskills.io) open standard. |
| **Scheduled automations** | Built-in cron scheduler with delivery to any platform. Daily reports, nightly backups, weekly audits — all in natural language, running unattended. |
| **Delegates and parallelizes** | Spawn isolated subagents for parallel workstreams. Write Python scripts that call tools via RPC, collapsing multi-step pipelines into zero-context-cost turns. |
| **Runs anywhere, not just your laptop** | Seven terminal backends — local, Docker, SSH, Singularity, Modal, Daytona, and Vercel Sandbox. Daytona and Modal offer serverless persistence — your agent's environment hibernates when idle and wakes on demand, costing nearly nothing between sessions. Run it on a $5 VPS or a GPU cluster. |
| **Research-ready** | Batch trajectory generation, trajectory compression for training the next generation of tool-calling models. |

---

## Skip the API-key collection — Nous Portal

Hermes works with whatever provider you want — that's not changing. But if you'd rather not collect five separate API keys for the model, web search, image generation, TTS, and a cloud browser, **[Nous Portal](https://portal.nousresearch.com)** covers all of them under one subscription:

- **300+ models** — pick any of them with `/model <name>`
- **Tool Gateway** — web search (Firecrawl), image generation (FAL), text-to-speech (OpenAI), cloud browser (Browser Use), all routed through your sub. No extra accounts.

One command from a fresh install:

```bash
hermes setup --portal
```

That logs you in via OAuth, sets Nous as your provider, and turns on the Tool Gateway. Check what's wired up any time with `hermes portal status`. Full details on the [Tool Gateway docs page](https://hermes-agent.nousresearch.com/docs/user-guide/features/tool-gateway).

You can still bring your own keys per-tool whenever you want — the gateway is per-backend, not all-or-nothing.

---

## 📦 Installation

### Linux, macOS, WSL2, Termux

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

### Windows (native, PowerShell) — Early Beta

Run this in PowerShell:

```powershell
iex (irm https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.ps1)
```

The installer handles everything: uv, Python 3.11, Node.js, ripgrep, ffmpeg, and a portable Git Bash (MinGit). Hermes uses this bundled Git Bash to run shell commands.

After installation:

```bash
source ~/.bashrc    # reload shell (or: source ~/.zshrc)
hermes              # start chatting!
```

---

## 📚 Documentation

All documentation lives at [hermes-agent.nousresearch.com/docs](https://hermes-agent.nousresearch.com/docs/):

| Section | What's Covered |
|---------|---------------|
| [Quickstart](https://hermes-agent.nousresearch.com/docs/getting-started/quickstart) | Install → setup → first conversation in 2 minutes |
| [CLI Usage](https://hermes-agent.nousresearch.com/docs/user-guide/cli) | Commands, keybindings, personalities, sessions |
| [Configuration](https://hermes-agent.nousresearch.com/docs/user-guide/configuration) | Config file, providers, models, all options |
| [Messaging Gateway](https://hermes-agent.nousresearch.com/docs/user-guide/messaging) | Telegram, Discord, Slack, WhatsApp, Signal, Home Assistant |
| [Security](https://hermes-agent.nousresearch.com/docs/user-guide/security) | Command approval, DM pairing, container isolation |
| [Tools & Toolsets](https://hermes-agent.nousresearch.com/docs/user-guide/features/tools) | 40+ tools, toolset system, terminal backends |
| [Skills System](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills) | Procedural memory, Skills Hub, creating skills |
| [Memory](https://hermes-agent.nousresearch.com/docs/user-guide/features/memory) | Persistent memory, user profiles, best practices |
| [MCP Integration](https://hermes-agent.nousresearch.com/docs/user-guide/features/mcp) | Connect any MCP server for extended capabilities |
| [Cron Scheduling](https://hermes-agent.nousresearch.com/docs/user-guide/features/cron) | Scheduled tasks with platform delivery |
| [Architecture](https://hermes-agent.nousresearch.com/docs/developer-guide/architecture) | Project structure, agent loop, key classes |
| [Contributing](https://hermes-agent.nousresearch.com/docs/developer-guide/contributing) | Development setup, PR process, code style |

---

## 🚀 Quick Start for Contributors

```bash
git clone https://github.com/NousResearch/hermes-agent.git
cd hermes-agent
./setup-hermes.sh     # installs uv, creates venv, installs .[all], symlinks hermes
./hermes              # auto-detects the venv, no need to `source` first
```

Manual path (equivalent to the above):

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv venv .venv --python 3.11
source .venv/bin/activate
uv pip install -e ".[all,dev]"
scripts/run_tests.sh
```

---

## 🌍 Community

- 💬 [Discord](https://discord.gg/NousResearch)
- 📦 [Skills Hub](https://agentskills.io)
- 🐛 [Issues](https://github.com/NousResearch/hermes-agent/issues)
- 🔗 [computer-use-linux](https://github.com/avifenesh/computer-use-linux) — Linux desktop-control MCP server
- 🔗 [HermesClaw](https://github.com/AaronWong1999/hermesclaw) — Community WeChat bridge

---

## 📄 License

MIT — see [LICENSE](LICENSE).

Built by [Nous Research](https://nousresearch.com).
```