<div align="center">

<img src="https://github.com/jkjoker/datawork/blob/datawork/images/datawork_128x128.ico" alt="datawork" width="128" />

# datawork

**Local-First Personal AI Agent System**

*For anyone who encodes — 给每一个需要对信息进行编码的人*

<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Platform-Windows-blue?logo=windows" alt="Windows" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Built%20with-Python-3776AB?logo=python&logoColor=white" alt="Python" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Version-3.8.6f10.3.20260531-green" alt="Version" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/License-Proprietary-red" alt="License" /></a>

[官方主页](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout) · [下载](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout) · [更新日志](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Achangelog)

---

[English](#english) | 简体中文

</div>

## 项目简介

datawork 是一个**本地优先（Local-First）**的个人 AI Agent 系统，集成了笔记 / 待办 / Python 自动化 / 多家 AI 大模型 / 标准 MCP 协议的能力。

旨在让每个人都能得到这些能力的联合助力，从而**更好地关注自己的想法与思考、专注真实业务，并在每一次行动中实现有效积累**。

**核心特性**：全离线、全本地、无注册、无登录、支持中英文界面。可通过 Python 插件无限拓展其能力，也可对接任意标准 MCP server。

**日用场景**：翻译、阅读辅助、日常对话、本地搜索查阅、文件编辑、项目笔记、待办协作、小脚本的创作与运行、自定义工具开发、代码审核与研读等，也有专属的code agent，可用于复杂项目代码开发。

## 核心特性

| 模块 | 特性 |
|------|------|
| **双 Agent 系统** | **通用 Agent**（多角色，日常对话/信息整理/写作）+ **Code Agent**（编码/调试/长任务多轮工具调用）；两者共享模型、记忆、待办、文件白名单、插件与 MCP 配置 |
| **三模式主程序 AI** | Quick（快速对话）/ Expert（通用 Agent 接入）/ Code（Code Agent 接入）一键切换，三模式共享上下文、互不污染 |
| **工具与扩展** | 三层工具体系：内置工具（文件 / 检索 / 执行 / 互动）+ DataWork 插件（用户写 .py 即插件）+ 标准 MCP（接入任意外部 server，可一键将 DataWork 作为 MCP server，与其他工作台协同）|
| **特色机制** | MCP 权限审批（按只读/写入/执行分级弹窗）+ `ask_user` 主动提问 + `wait_for_seconds` 主动延迟 + 用户主动干预（多轮中途插话）+ 智能滚动（贴底跟随、阅读历史不打扰）|
| **模型与适配** | 已适配 10 家供应商：DeepSeek / Kimi / 小米 MiMo / Qwen / GLM / OpenAI / OpenRouter / Claude / Ollama / Gemini；可视化模型管理（思考 🧠 / 视觉 👁 / 工具 🔧 三种能力徽章）；DeepSeek V4 思考模式 + 工具调用全程流式输出 |
| **记忆与待办** | 多记忆库（全文搜索 / 类型标记 / 右键添加 / 复制路径）+ 三层 Todo 系统（清单 / Todo / Task）+ 待办内置工具与外部 Todo MCP 完全对齐 |
| **Coder 编辑器** | 多 tab 文件编辑 + 资源管理器（浏览、自动刷新）+ Git 集成（本地备份 + 远程推送 / 编辑器 Diff 审核 / 提交历史代码研读对话，沉淀到 git notes）+ Python / Go 命令行 / Web 工程辅助 |
| **Web 与移动** | 内置 Web 服务（chat / editor / PPT 工作台），手机端响应式自适应；可在局域网用任意浏览器访问 |
| **数据与安全** | 全本地存储（SQLite + 文件）；文件白名单 + 工具权限分级 + 会话级缓存；Web 请求自动识别（避免桌面端弹窗卡死） |

## 双 Agent 系统

两套各自独立、可并行使用的 Agent 系统：

- **通用 Agent**：日常对话、信息整理、跨域助理；可同时存在多个角色（A/B/...）；入口在主程序 AI 的 Quick/Expert 模式、Mini 全局窗口、Web chat 等
- **Code Agent**：专注编码、调试、代码理解；强工作目录概念（项目根 + .git 上下文）；独立 ContextManager + token 阈值压缩；入口在主程序 AI 的 **Code 模式** 与命令行终端

两者**共享**：模型管理、记忆库、Todo 系统、文件白名单、DataWork 插件、外部 MCP server、研读笔记。

## 工具体系（三层）

```
L1 内置工具      ← datawork 自带，开箱即用
L2 DataWork 插件 ← 用户写 .py 文件即可补充能力
L3 标准 MCP      ← 接入外部 server，与 Cursor / Claude Desktop 等共享
```

- **内置工具**（部分）：`file_read/write/edit` / `grep` / `glob` / `run_command` / `run_python` / `code_search` / `memory_operations` / `link_parser` / `todo_*` / `wait_for_seconds` / `ask_user` / `review_notes_*`
- **DataWork 插件**：放在 `datawork_tools_config/custom_tools/` 下的 .py 文件即被识别；可见性两态（`always` 常驻 / `marketplace` 按需查阅）；通用 Agent 与 Code Agent 共享一份；**可一键导出为标准 FastMCP server 项目**，让其他 MCP 客户端也能复用
- **标准 MCP**：在配置中填入 server 启动命令即可；通用 Agent 与 Code Agent 共享同一份 MCP 协议层（`src/mcp_runtime/`）

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

**安装版优势**：启动更快、运行更稳、更新只需重新安装

**无注册 | 无登录 | 数据本地化**

## 技术栈

| 领域 | 技术 |
|------|------|
| 桌面应用 | Python, Tkinter |
| Web 服务 | FastAPI / Uvicorn / Jinja2 |
| AI 适配 | OpenAI / Claude / Gemini / DeepSeek / Qwen / Kimi / 小米 MiMo / GLM / OpenRouter / Ollama |
| 协议 | MCP（Model Context Protocol，含独立运行时 `src/mcp_runtime/`）|
| 向量检索 | Embedding + Vector Database（实验室模块） |
| 数据存储 | SQLite + 本地文件（记忆 / 待办 / 配置 / 研读笔记） |
| 版本协作 | Git（本地备份 + 远程推送 + git notes 持久化研读对话） |

## 联系

**作者**: jk.zhou — 专注于 Agent 系统开发与数据工作  
**Email**: 1406584456@qq.com | **个人网站**: [publish.obsidian.md/xm](https://publish.obsidian.md/xm)

---

<a name="english"></a>

<div align="center">

# datawork

**Local-First Personal AI Agent System**

*For anyone who encodes — For everyone who needs to encode information*

</div>

## About

datawork is a **local-first** personal AI Agent system that integrates notes, todos, Python automation, multi-vendor LLMs, and the standard MCP protocol.

It empowers you to **better focus on your thoughts and real-world tasks, and achieve effective accumulation in every action** through the combined power of these elements.

**Core Specs**: Fully offline, fully local, no registration, no login required. **Multi-language UI (English/Chinese)**. Extensible via Python plugins, and connectable to any standard MCP server.

**Daily Use Cases**: Translation, reading assistance, daily chat, local search, file editing, project notes, todo collaboration, script creation & execution, custom tool development, code review & study, etc.; it also includes a dedicated Code Agent for complex project code development.

## Key Features

| Category | Features |
|----------|----------|
| **Dual-Agent System** | **General Agent** (multi-role, daily chat / info organization / writing) + **Code Agent** (coding / debugging / long multi-turn tool calls); both share models, memory, todos, file whitelist, plugins & MCP config |
| **Tri-mode Main AI** | Quick (fast chat) / Expert (General Agent) / Code (Code Agent) — one-click switching; the three modes share context without polluting each other |
| **Tools & Extensibility** | Three-layer tool system: built-in tools (file / search / exec / interaction) + DataWork Plugins (drop-in `.py` files) + standard MCP (connect any external server; plugins can be exported as MCP servers with one click) |
| **Signature Mechanisms** | MCP permission approval (read-only / write / execute tiers with popup confirmation) + `ask_user` (Agent-initiated questions) + `wait_for_seconds` (Agent-initiated delay) + user mid-loop intervention + smart auto-scroll (sticky-bottom follow, history-reading non-disruption) |
| **Models** | 10 providers: DeepSeek / Kimi / Xiaomi MiMo / Qwen / GLM / OpenAI / OpenRouter / Claude / Ollama / Gemini; visual model manager with reasoning 🧠 / vision 👁 / tools 🔧 capability badges; DeepSeek V4 reasoning + tool-calls fully streaming |
| **Memory & Todos** | Multi memory libraries (full-text search / type tagging / right-click add / copy path) + three-tier Todo system (List / Todo / Task) + built-in todo tools fully aligned with external Todo MCP |
| **Coder Editor** | Multi-tab file editing + file explorer (auto-refresh) + Git integration (local backup + remote push / editor diff review / commit-history code-study chat persisted via git notes) + Python / Go terminal / Web project helpers |
| **Web & Mobile** | Built-in web server (chat / editor / PPT workbench), mobile-responsive; accessible via any browser on LAN |
| **Data & Safety** | Fully local storage (SQLite + files); file whitelist + tiered tool permissions + session-level cache; web request auto-detection (avoids desktop popup deadlocks) |

## Dual-Agent System

Two independent and parallel-usable Agent systems:

- **General Agent**: Daily chat, info organization, cross-domain assistant; supports multiple roles (A/B/...); entry points include Main AI's Quick/Expert mode, the Mini global window, and Web chat
- **Code Agent**: Focused on coding, debugging, code understanding; strong working-directory concept (project root + .git context); independent ContextManager with token-threshold compression; entry points: Main AI's **Code mode** and the command-line terminal

Both **share**: model management, memory, Todo, file whitelist, DataWork plugins, external MCP servers, and code-study notes.

## Tool System (Three Layers)

```
L1 Built-in tools      ← shipped with datawork
L2 DataWork Plugins    ← drop a .py file to extend
L3 Standard MCP        ← connect external servers; share with Cursor / Claude Desktop / etc.
```

- **Built-in (subset)**: `file_read/write/edit` / `grep` / `glob` / `run_command` / `run_python` / `code_search` / `memory_operations` / `link_parser` / `todo_*` / `wait_for_seconds` / `ask_user` / `review_notes_*`
- **DataWork Plugins**: any `.py` under `datawork_tools_config/custom_tools/` is auto-detected; two visibility modes (`always` resident / `marketplace` on-demand); shared by both Agents; **one-click export as a standard FastMCP server project** for cross-tool reuse
- **Standard MCP**: configure server launch command; both Agents share the same MCP runtime (`src/mcp_runtime/`)

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
- **Web**: FastAPI / Uvicorn / Jinja2
- **AI Vendors**: OpenAI / Claude / Gemini / DeepSeek / Qwen / Kimi / Xiaomi MiMo / GLM / OpenRouter / Ollama
- **Protocol**: MCP (Model Context Protocol, with standalone runtime `src/mcp_runtime/`)
- **Vector Search**: Embedding + Vector Database (Lab module)
- **Storage**: SQLite + local files (memory / todos / config / review notes)
- **VCS**: Git (local backup + remote push + code-study chat persisted via git notes)

## Contact

**Author**: jk.zhou — Focused on Agent System Development & Data Engineering  
**Email**: 1406584456@qq.com | **Website**: [publish.obsidian.md/xm](https://publish.obsidian.md/xm)

---

<div align="center">

**© 2024-2026 jk.zhou. All rights reserved.**

</div>




