# VerifAIble

**Make every bit of information verifiable to everyone.**

[中文版](README_zh.md) · [Website](https://ai.verifaible.space/)

![Release](https://img.shields.io/github/v/release/ChizhongWang/OpenVerifAIble?label=release)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Android%20%7C%20Web-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)

---

## What is VerifAIble?

VerifAIble is an AI-powered content creation platform where **every AI response is backed by verifiable evidence**. Unlike traditional AI chatbots that generate plausible but unverifiable text, VerifAIble's Agent system actively searches the web, collects evidence, and creates citations that link directly to highlighted source material — making AI-generated content auditable and trustworthy.

🌐 Try it at [ai.verifaible.space](https://ai.verifaible.space/)

---

## Key Features

### AI Agent with 18 Built-in Tools

VerifAIble's AI doesn't just generate text — it **takes action**. The built-in Agent autonomously searches the web, navigates pages, extracts data, and creates citations through a complete tool loop (reasoning → tool calls → result feedback → continued reasoning). It supports progressive tool discovery and sub-agent orchestration for complex multi-step tasks.

### 7 Providers, 12+ Models — Your Choice

Switch between **12+ LLMs** from 7 providers with one click: OpenAI (GPT-5.1/5.2), Google Gemini (3-Pro/3-Flash), DeepSeek (Chat/R1), Anthropic (Claude Sonnet 4.6), MiniMax (M2.5), Zhipu (GLM-5), and Moonshot (Kimi-K2.5). Each model streams responses in real-time via SSE.

### Verifiable Citations — 7 Evidence Types

Every claim can be traced back to its source. Click any citation to see the **original content highlighted** on the source page. Supports 7 evidence types:

| Type | How It Works |
|------|-------------|
| **Text** | Highlights the exact sentence on the source page |
| **Table** | Crosshair positioning on the exact row and column |
| **PDF** | Opens built-in PDF viewer, jumps to the right page and passage |
| **Video** | Jumps to the exact timestamp in a YouTube video |
| **Dynamic Page** | Replays browser actions (clicks, date pickers, JS) then highlights |
| **Document** | Links to uploaded documents with anchor navigation |
| **Image** | Links to source images with metadata |

### Built-in Research Browser

No need to switch between apps. VerifAIble includes a **built-in Chromium browser** with split-view — chat with AI on one side, browse and verify sources on the other. Organize your research with workspaces and tabs.

### Cross-Platform

Available on **macOS**, **Windows**, **Android**, and the **Web**. Desktop apps built with Electron, mobile with Capacitor, all sharing the same Vue 3 frontend.

### Multi-Language Support

Full UI support for **English**, **简体中文**, and **日本語**.

---

## Download

### macOS (Apple Silicon)
- [VerifAIble-0.0.0-arm64.dmg](https://github.com/ChizhongWang/OpenVerifAIble/releases/download/v0.0.0/VerifAIble-0.0.0-arm64.dmg)

### Windows
Coming soon

### Web
- [ai.verifaible.space](https://ai.verifaible.space/)

> **Note:** This app is not code-signed. On first launch, you may need to allow it in **System Preferences > Security & Privacy**.

---

## Related Projects

| Project | Description |
|---------|-------------|
| [verifaible-bench](https://github.com/ChizhongWang/verifaible-bench) | Benchmark for evaluating LLM agents on verifiable evidence collection (6 models, 21 test cases) |
| [verifaible-model](https://github.com/ChizhongWang/verifaible-model) | SFT fine-tuning for evidence collection capabilities |

---

## License

MIT

---

© 2026 VerifAIble
