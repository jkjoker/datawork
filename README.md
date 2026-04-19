<div align="center">

<img src="https://github.com/jkjoker/datawork/blob/datawork/images/datawork_128x128.ico" alt="datawork" width="128" />

# datawork

**Local-First Personal AI Agent System**

*For anyone who encodes — 给每个需要对信息进行编码的人*

<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Platform-Windows-blue?logo=windows" alt="Windows" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Built%20with-Python-3776AB?logo=python&logoColor=white" alt="Python" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Version-3.8.4a5.20251203-green" alt="Version" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/License-Proprietary-red" alt="License" /></a>

[官方主页](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout) · [下载](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout) · [更新日志](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Achangelog)

---

[English](#english) | 简体中文

</div>

## 项目简介

datawork 是一个**本地优先**的个人AI Agent系统，集成了笔记、Python自动化与AI大模型的能力，适合作为个人日常工作台。

datawork 旨在让每个人都能得到这三者的联合助力，从而**更好地关注自己的想法与思考、专注真实业务，并在每一次行动中实现有效积累**。

**核心特性**：全离线、全本地、无注册、无登录、支持中英文界面。个人可通过Python无限拓展其能力。

**日用场景**：翻译、阅读辅助、日常对话、本地搜索查阅、文件编辑、项目笔记、小脚本的创作与运行、自定义MCP开发等。

## 核心特性

| 模块 | 特性 |
|------|------|
| **AI Agent** | 多轮MCP工具调用（deepseek单次支持最多200轮，含专属上下文压缩和状态管理机制，已特别适配推理模式下的工具调用）、多Agent协同、9种模型支持、自定义MCP开发 |
| **知识库** | 本地向量知识库、本地全文检索（自定义范围+正则）、Mini全局窗口、数据主权 |
| **Coder 编辑器** | 资源管理器（浏览、编辑、自动刷新）、Git集成、Python/Go代码运行、MCP开发 |
| **自动化** | Python环境管理、Agent安全运行（白名单+权限控制）、离线语音识别（Vosk）、Web服务 |

## 界面预览

<div align="center">
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/coder.png" width="55%" />
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/setup.png" width="35%" />
</div>


## 快速开始

```
1. 下载安装包 → 解压
2. 双击 datawork_setup.exe 安装
3. 启动程序，按提示设置工作路径即可使用
```

**推荐使用安装版**：启动更快、运行更稳、更新只需重新安装

**无注册 | 无登录 | 数据本地化**

## 技术栈

| 领域 | 技术 |
|------|------|
| 桌面应用 | Python, Tkinter |
| AI集成 | OpenAI / Claude / Gemini / DeepSeek / Qwen / Kimi / GLM / OpenRouter / Ollama / MCP Protocol |
| 向量检索 | Embedding, Vector Database |
| 语音识别 | Vosk (离线) |

## 联系

**作者**: jk.zhou — 专注于Agent系统开发与数据工作  
**Email**: 1406584456@qq.com | **个人网站**: [publish.obsidian.md/xm](https://publish.obsidian.md/xm)

---

<a name="english"></a>

<div align="center">

# datawork

**Local-First Personal AI Agent System**

*For anyone who encodes — For everyone who needs to encode information*

</div>

## About

datawork is a **local-first** personal AI Agent system that integrates Notes, Python automation, and AI.

It empowers you to **better focus on your thoughts and real-world tasks, and achieve effective accumulation in every action** through the combined power of these three elements.

**Core Specs**: Fully offline, fully local, no registration, no login required. **Multi-language UI (English/Chinese)**. Extensible via Python.

**Daily Use Cases**: Translation, reading assistance, daily chat, local search, file editing, project notes, script creation & execution, custom MCP development, etc.

## Key Features

| Category | Features |
|----------|----------|
| **AI Agent** | Multi-turn MCP (DeepSeek supports up to 200 tool rounds per session, with dedicated context compression and state management, specially adapted for tool calls in reasoning mode), Multi-Agent collaboration, 9 model providers, Custom MCP development |
| **Knowledge Base** | Local vector database, Full-text search (custom scope + regex), Global Mini window, Data sovereignty |
| **Coder** | File explorer (browse, edit, auto-refresh), Git integration, Python/Go execution, MCP development |
| **Automation** | Python env management, Agent safe execution (whitelist + permissions), Offline speech recognition (Vosk), Web server |

## Screenshots

<div align="center">
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/coder.png" width="55%" />
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/setup.png" width="35%" />
</div>

## Quick Start

```
1. Download installer → Extract
2. Run datawork_setup.exe to install
3. Launch and set your workspace path as prompted
```

**Installer Benefits**: Faster startup, more stable, easy updates

**No registration | No login | Local data only**

## Tech Stack

- **Desktop**: Python, Tkinter
- **AI**: OpenAI / Claude / Gemini / DeepSeek / Qwen / Kimi / GLM / OpenRouter / Ollama / MCP Protocol
- **Vector Search**: Embedding & Vector Database
- **Speech**: Vosk (Offline)

## Contact

**Author**: jk.zhou — Focused on Agent System Development & Data Engineering  
**Email**: 1406584456@qq.com | **Website**: [publish.obsidian.md/xm](https://publish.obsidian.md/xm)

---

<div align="center">

**© 2024-2026 jk.zhou. All rights reserved.**

</div>




