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

datawork 是一个**本地优先（Local-First）**的个人 AI Agent 系统。它把个人资料、AI 对话、记忆、待办、项目、脚本、插件和标准 MCP 协议放进同一个本地工作环境，让 AI 不只停留在聊天框，而是进入你的长期工作流。

datawork 关注的不是“让 AI 一次性回答一个问题”，而是帮助你在阅读、写作、编码、整理、复盘和执行中，持续沉淀自己的上下文、经验、工具和工作流。

它的初心是让每个人得到 **AI、编码、记录** 三种力量的联合助力：AI 扩展思考能力，编码扩展行动能力，记录保存原始数据、思考痕迹和任务过程，从而**更好地关注自己的想法与思考、专注真实业务，并在每一次行动中实现有效积累**。

**核心特性**：本地优先的工作区存储，无需 datawork 账号、无需注册、无需登录。工作区数据默认保存在本地（SQLite + 文件）。你可以使用 Ollama 等本地模型，也可以按需配置 OpenAI、Claude、Gemini、DeepSeek、Qwen、Kimi 等第三方模型 API。支持中英文界面。可通过 Python 插件无限拓展其能力，也可对接任意标准 MCP server。

**日用场景**：翻译、阅读辅助、日常对话、本地搜索查阅、文件编辑、项目笔记、待办协作、小脚本的创作与运行、自定义工具开发、代码审核与研读等，也有专属的code agent，可用于复杂项目代码开发。

## datawork 与其他工具的关系

datawork 不试图替代 ChatGPT、Cursor、Claude Code、Obsidian 或 Notion。它更像是这些工具之间的**本地上下文中心与行动层**：

- 把分散在文件、笔记、AI 对话、Todo、代码项目和自动化脚本里的内容连接起来；
- 让每次对话、任务、开发和整理都能沉淀为可搜索、可复用、可继续调用的个人资产；
- 通过 MCP 与插件体系，把 datawork 中长期积累的记忆、Todo 和工具能力带到外部编辑器与其他 Agent 工作台中。


## 核心特性

| 模块 | 特性 |
|------|------|
| **双 Agent 系统** | **通用 Agent**（多角色，日常对话/信息整理/写作）+ **Code Agent**（编码/调试/长任务多轮工具调用）；两者共享模型、记忆、待办、文件白名单、插件与 MCP 配置 |
| **三模式主程序 AI** | Quick（快速对话）/ Expert（通用 Agent 接入）/ Code（Code Agent 接入）一键切换，三模式共享上下文、互不污染 |
| **工具与扩展** | 三层工具体系：内置工具（文件 / 检索 / 执行 / 互动）+ datawork 插件（用户写 .py 即插件）+ 标准 MCP（既可接入任意外部 server，也可将 datawork 的记忆库与 Todo 系统开启为 MCP server，供其他应用连接调用）|
| **特色机制** | MCP 权限审批（按只读/写入/执行分级弹窗）+ `ask_user` 主动提问 + `wait_for_seconds` 主动延迟 + 用户主动干预（多轮中途插话）+ 智能滚动（贴底跟随、阅读历史不打扰）|
| **模型与适配** | 已适配 10 家供应商：DeepSeek / Kimi / 小米 MiMo / Qwen / GLM / OpenAI / OpenRouter / Claude / Ollama / Gemini；可视化模型管理（思考 🧠 / 视觉 👁 / 工具 🔧 三种能力徽章）；DeepSeek V4 思考模式 + 工具调用全程流式输出 |
| **记忆与待办** | 多记忆库（全文搜索 / 类型标记 / 右键添加 / 复制路径）+ 三层 Todo 系统（清单 / Todo / Task）+ AI 对话、项目经验与任务过程的长期沉淀 + 待办内置工具与外部 Todo MCP 完全对齐 |
| **Coder 编辑器** | 多 tab 文件编辑 + 资源管理器（浏览、自动刷新）+ Git 集成（本地备份 + 远程推送 / 编辑器 Diff 审核 / 提交历史代码研读对话，沉淀到 git notes）+ Python / Go 命令行 / Web 工程辅助 |
| **Web 与移动** | 内置 Web 服务（chat / editor / PPT 工作台），手机端响应式自适应；可在局域网用任意浏览器访问 |
| **数据与安全** | 本地工作区存储（SQLite + 文件）；文件白名单 + 工具权限分级 + 会话级缓存；Web 请求自动识别（避免桌面端弹窗卡死） |

## 双 Agent 系统

两套各自独立、可并行使用的 Agent 系统：

- **通用 Agent**：日常对话、信息整理、跨域助理；可同时存在多个角色（A/B/...）；入口在主程序 AI 的 Quick/Expert 模式、Mini 全局窗口、Web chat 等
- **Code Agent**：专注编码、调试、代码理解；强工作目录概念（项目根 + .git 上下文）；独立 ContextManager + token 阈值压缩；入口在主程序 AI 的 **Code 模式** 与命令行终端

两者**共享**：模型管理、记忆库、Todo 系统、文件白名单、datawork 插件、外部 MCP server、研读笔记。

## 工具体系（三层）

```
L1 内置工具      ← datawork 自带，开箱即用
L2 datawork 插件 ← 用户写 .py 文件即可补充能力
L3 标准 MCP      ← 接入外部 server，与 Cursor / Claude Desktop 等共享
```

- **内置工具**（部分）：`file_read/write/edit` / `grep` / `glob` / `run_command` / `run_python` / `code_search` / `memory_operations` / `link_parser` / `todo_*` / `wait_for_seconds` / `ask_user` / `review_notes_*`
- **datawork 插件**：放在 `datawork_tools_config/custom_tools/` 下的 .py 文件即被识别；可见性两态（`always` 常驻 / `marketplace` 按需查阅）；通用 Agent 与 Code Agent 共享一份
- **标准 MCP**：在配置中填入 server 启动命令即可接入外部 MCP server；通用 Agent 与 Code Agent 共享同一份 MCP 协议层（`src/mcp_runtime/`）；同时可将 datawork 自身的记忆库与 Todo 系统开启为 MCP server，让 Cursor、Claude Desktop 等其他应用直接连接调用

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

**无注册 | 无登录 | 工作区数据默认本地化**

当前桌面版主要面向 **Windows 10 及以上系统**构建和测试。

## 适合谁

datawork 不一定适合所有人。如果你只是偶尔问 AI 一个问题，或者只需要一个极简聊天窗口，ChatGPT、Claude 等工具可能已经足够。

datawork 更适合这些用户：

- **重度 AI 用户**：已经在认真使用 AI 工作，并且觉得 AI 对话、提示词、任务过程和阶段性结论值得长期保存与复用；
- **被碎片化工作流困扰的人**：资料散落在文件夹、笔记、聊天记录、浏览器、Todo、截图、手机和多个 AI 平台之间，希望有一个本地工作台把它们接住；
- **重度记录者、知识工作者、研究者、独立开发者和长期项目型用户**：有大量笔记、文件、链接、项目过程和经验需要持续管理；
- **需要跨设备、跨项目整理资料的人**：经常在手机、电脑、浏览器之间记录想法、传递文件、整理任务，并希望后续还能被搜索、调用和沉淀；
- **希望 AI 进入长期工作流的人**：不只想让 AI 回答问题，而是希望它能读文件、改文件、写脚本、调用工具、更新 Todo、沉淀记忆；
- **希望复用个人上下文的人**：正在使用 Cursor、Claude Desktop、Claude Code 或其他 AI 工具，并希望它们能通过 MCP 访问自己的记忆库和 Todo 系统；
- **愿意掌控本地数据与工具扩展的人**：重视本地优先，也希望用 Python 插件或 MCP 把自己的小自动化逐步变成可复用能力。

datawork 可能不太适合只想体验一次性 AI 问答、完全不需要本地资料管理、任务跟踪或工具扩展的轻度用户。

## 一个典型工作流

1. 把项目资料、笔记和代码放入本地工作区；
2. 使用通用 Agent 讨论需求、收集信息、生成 Todo；
3. 使用 Code Agent 读取项目、编辑文件、运行脚本、调试或审核代码；
4. 将关键结论沉淀到记忆库，将任务进度保存在 Todo 系统中；
5. 将 datawork 的记忆库和 Todo 系统开启为 MCP server，让 Cursor、Claude Desktop 等外部工具继续连接使用。

## 具体案例

以下案例并不是额外的宣传口号，而是 datawork 在真实使用和开发过程中已经形成的工作方式。它们对应的都是很具体的问题：能力如何沉淀、上下文如何长期保存、碎片想法如何变成行动、不同工具之间如何重新连接。

### 1. 自进化的能力：把临时需求沉淀为可复用工具

在使用或开发过程中，如果遇到新的具体需求，可以按需临时开发一个本地 datawork 插件。插件开发完成后，通用 Agent 与 Code Agent 都可以调用同一份能力。

这意味着一次性的任务处理，可以进一步沉淀为长期可复用的工具：Agent 不只是使用现有工具，也可以在人的确认和权限控制下参与开发新工具，让系统逐步具备“自主开发、自主进化、能力复用”的特征。

### 2. 复用已有 Skills：把过去积累的能力继续用起来

很多重度 AI 用户已经在其他工具中积累了自己的 skills、提示词、流程文档、脚本或工作方法。datawork 不要求这些积累从零开始重建，而是可以通过配置路径的方式，把已有的 skills 继续纳入当前工作流。

这让过去分散在不同工具里的个人能力资产，可以被通用 Agent 和 Code Agent 继续读取、理解和复用。用户不必被某一个 IDE、某一个 AI 平台或某一种工作流绑定，而是可以把已经验证有效的方法逐步迁移到一个更开放、可连接、可长期沉淀的本地系统中。

### 3. Todo 系统：让碎片想法快速变成可执行任务

datawork 内置了完整的三层 Todo 系统（清单 / Todo / Task）和顺畅的可视化界面。日常想到的事情、开发中的临时判断、项目中的下一步动作，都可以快速记录、快速拆分、快速完成。

更重要的是，这套 Todo 既方便人使用，也方便 Agent 使用：用户可以复制 Todo 或清单路径发给 Agent，Agent 就能围绕这些任务开始行动，也可以在授权下维护待办事项、更新进度、补充子任务。datawork 因此不只是一个记录工具，而是一个把零散思考、任务管理和 Agent 行动连接起来的系统。

这种方式让思考沉淀变得非常轻量：很多碎片想法不需要先进入复杂文档，也不依赖某一个专门 IDE 或项目管理系统，就可以先被接住、被整理，并在需要时交给 Agent 或外部工具继续推进。

### 4. 协作模式：在复杂任务中管理长期上下文

主界面 AI 提供协作模式。在 Code Agent 执行复杂开发、调试或长流程任务时，用户仍然可以和通用 Agent 沟通：梳理当前对话内容、沉淀阶段性结论、完善上下文、更新 Todo，或对下一步行动进行校准。

这种模式的价值不只是“多个 Agent 同时工作”，而是让复杂任务的上下文被持续整理和保存。人在关键节点参与判断，通用 Agent 负责解释、归纳和承接上下文，Code Agent 负责项目内的执行。即使两个月后重新打开任务，Agent 也能快速理解当时的原貌、决策和进展，从而更准确地继续推进。

### 5. 代码研读：让每一次提交都成为可复盘的知识资产

在开发过程中，每一次 Git 提交都可以在 datawork 的 Git 界面中被后续阅读、审核和讨论。用户可以围绕某一次提交持续追加笔记、备注和研读记录，这些内容会沉淀到对应提交的 notes 中。

同时，用户也可以复制某次提交的研读线索，与外部任意 Agent 工具继续沟通，让外部工具围绕该提交的 diff、说明和已有笔记进行辅助分析。这有助于提升代码质量，帮助用户理解项目演化过程，也让代码审查和学习不再只停留在一次性的提交记录里。

### 6. 文件传输助手：随时捕获并连接手机与电脑之间的资料

datawork 也包含文件传输助手这类具体而高频的小工具。用户可以在手机和电脑之间快速传输、暂存和捕获文件或资料，把临时出现的信息及时接入自己的本地工作区。

这类能力看起来很小，但在真实工作流中非常重要：它让截图、文件、临时资料和移动端捕获的内容不再散落在不同设备里，而是更容易进入后续的搜索、整理、Todo、记忆和 Agent 工作流。

## 许可证

datawork 当前为**专有软件**，不是开源项目，源码未对外开放。Windows 桌面应用已开放下载，支持 **Windows 10 及以上系统**，可直接安装使用，这也是目前唯一对外开放的产品形态。若有分发授权、商业使用或其他对外合作需求，请联系作者沟通。

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

datawork is a **local-first** personal AI Agent system. It brings your personal files, AI conversations, memory, todos, projects, scripts, plugins, and the standard MCP protocol into one local workspace — so AI does not stay inside a chat box, but becomes part of your long-term workflow.

datawork is not about asking AI to answer one question at a time. It is about helping you continuously accumulate context, experience, tools, and workflows as you read, write, code, organize, review, and execute.

Its original motivation is to combine three kinds of power for individuals: **AI, coding, and recording**. AI extends thinking, coding extends action, and recording preserves raw materials, thought traces, and task processes — empowering you to **better focus on your thoughts and real-world tasks, and achieve effective accumulation in every action**.

**Core Specs**: Local-first workspace storage, no datawork account, no registration, no login required. Workspace data is stored locally by default (SQLite + files). You can use local models such as Ollama, or configure third-party model APIs such as OpenAI, Claude, Gemini, DeepSeek, Qwen, Kimi, and others. **Multi-language UI (English/Chinese)**. Extensible via Python plugins, and connectable to any standard MCP server.

**Daily Use Cases**: Translation, reading assistance, daily chat, local search, file editing, project notes, todo collaboration, script creation & execution, custom tool development, code review & study, etc.; it also includes a dedicated Code Agent for complex project code development.

## How datawork Relates to Other Tools

datawork does not try to replace ChatGPT, Cursor, Claude Code, Obsidian, or Notion. It acts more like a **local context hub and action layer** between these tools:

- Connect content scattered across files, notes, AI conversations, todos, code projects, and automation scripts;
- Turn every conversation, task, development session, and organizing effort into searchable, reusable, and callable personal assets;
- Bring the memory, todos, and tool capabilities accumulated in datawork to external editors and other Agent workbenches through MCP and the plugin system.

You can keep using the tools you already like. datawork's role is to help the context, tasks, notes, scripts, and tool capabilities produced around those tools settle into a local system that can be searched, reused, and connected again.


## Key Features

| Category | Features |
|----------|----------|
| **Dual-Agent System** | **General Agent** (multi-role, daily chat / info organization / writing) + **Code Agent** (coding / debugging / long multi-turn tool calls); both share models, memory, todos, file whitelist, plugins & MCP config |
| **Tri-mode Main AI** | Quick (fast chat) / Expert (General Agent) / Code (Code Agent) — one-click switching; the three modes share context without polluting each other |
| **Tools & Extensibility** | Three-layer tool system: built-in tools (file / search / exec / interaction) + datawork plugins (drop-in `.py` files) + standard MCP (connect to any external server, and expose datawork's memory libraries and Todo system as an MCP server for other apps to use) |
| **Signature Mechanisms** | External MCP tool-call approval (read-only / write / execute tiers with popup confirmation) + `ask_user` (Agent-initiated questions) + `wait_for_seconds` (Agent-initiated delay) + user mid-loop intervention + smart auto-scroll (sticky-bottom follow, history-reading non-disruption) |
| **Models** | 10 providers: DeepSeek / Kimi / Xiaomi MiMo / Qwen / GLM / OpenAI / OpenRouter / Claude / Ollama / Gemini; visual model manager with reasoning 🧠 / vision 👁 / tools 🔧 capability badges; DeepSeek V4 reasoning + tool-calls fully streaming |
| **Memory & Todos** | Multi memory libraries (full-text search / type tagging / right-click add / copy path) + three-tier Todo system (List / Todo / Task) + long-term accumulation of AI conversations, project experience, and task processes + built-in todo tools fully aligned with external Todo MCP |
| **Coder Editor** | Multi-tab file editing + file explorer (auto-refresh) + Git integration (local backup + remote push / editor diff review / commit-history code-study chat persisted via git notes) + Python / Go terminal / Web project helpers |
| **Web & Mobile** | Built-in web server (chat / editor / PPT workbench), mobile-responsive; accessible via any browser on LAN |
| **Data & Safety** | Local workspace storage (SQLite + files); file whitelist + tiered tool permissions + session-level cache; web request auto-detection (avoids desktop popup deadlocks) |

## Dual-Agent System

Two independent and parallel-usable Agent systems:

- **General Agent**: Daily chat, info organization, cross-domain assistant; supports multiple roles (A/B/...); entry points include Main AI's Quick/Expert mode, the Mini global window, and Web chat
- **Code Agent**: Focused on coding, debugging, code understanding; strong working-directory concept (project root + .git context); independent ContextManager with token-threshold compression; entry points: Main AI's **Code mode** and the command-line terminal

Both **share**: model management, memory, Todo, file whitelist, datawork plugins, external MCP servers, and code-study notes.

## Tool System (Three Layers)

```
L1 Built-in tools      ← shipped with datawork
L2 datawork plugins    ← drop a .py file to extend
L3 Standard MCP        ← connect external servers; share with Cursor / Claude Desktop / etc.
```

- **Built-in (subset)**: `file_read/write/edit` / `grep` / `glob` / `run_command` / `run_python` / `code_search` / `memory_operations` / `link_parser` / `todo_*` / `wait_for_seconds` / `ask_user` / `review_notes_*`
- **datawork plugins**: any `.py` under `datawork_tools_config/custom_tools/` is auto-detected; two visibility modes (`always` resident / `marketplace` on-demand); shared by both Agents
- **Standard MCP**: configure server launch commands to connect external MCP servers; both Agents share the same MCP runtime (`src/mcp_runtime/`); datawork can also expose its own memory libraries and Todo system as an MCP server, so tools like Cursor and Claude Desktop can connect to and use them directly

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

**No registration | No login | Local workspace data by default**

Current desktop releases are primarily built and tested for **Windows 10 and above**.

## Who It Is For

datawork is not necessarily for everyone. If you only ask AI an occasional question, or only need a minimal chat window, tools like ChatGPT or Claude may already be enough.

datawork is a better fit for people who:

- **Heavy AI users**: people who already work seriously with AI and want to preserve and reuse valuable conversations, prompts, task processes, and intermediate conclusions;
- **People struggling with fragmented workflows**: people whose materials are scattered across folders, notes, chat logs, browsers, todos, screenshots, phones, and multiple AI platforms, and who want a local workspace to hold them together;
- **Heavy note-takers, knowledge workers, researchers, independent developers, and long-term project users**: people with many notes, files, links, project traces, and accumulated experience to manage over time;
- **People who organize information across devices and projects**: people who often capture ideas, transfer files, and organize tasks across phone, desktop, and browser, and want those materials to remain searchable, callable, and reusable later;
- **People who want AI inside long-term workflows**: people who want AI not only to answer questions, but also to read files, edit files, write scripts, call tools, update todos, and accumulate memory;
- **People who want to reuse personal context**: people already using Cursor, Claude Desktop, Claude Code, or other AI tools, and who want those tools to access their own memory libraries and Todo system through MCP;
- **People who care about local-first data control and tool extension**: people who value local-first storage and want to gradually turn their own small automations into reusable capabilities through Python plugins or MCP.

datawork may be less suitable for light users who only want one-off AI Q&A and do not need local material management, task tracking, or tool extension.

## A Typical Workflow

1. Put project materials, notes, and code into a local workspace;
2. Discuss requirements, collect information, and generate todos with the General Agent;
3. Use the Code Agent to read a project, edit files, run scripts, debug, or review code;
4. Save key conclusions into memory libraries, and keep task progress in the Todo system;
5. Expose datawork's memory and Todo as an MCP server, so external tools such as Cursor or Claude Desktop can continue to use them.

## Concrete Use Cases

The following cases are not additional marketing claims. They are real working patterns that have already emerged from using and developing datawork. They address concrete problems: how capabilities are accumulated, how context is preserved over time, how fragmented thoughts become executable actions, and how different tools can be connected again.

### 1. Self-evolving capability: turn temporary needs into reusable tools

During use or development, when a new concrete need appears, you can create a local datawork plugin on demand. Once the plugin is ready, both the General Agent and the Code Agent can use the same capability.

This means a one-off task can be further accumulated into a reusable tool. The Agent does not only call existing tools; with human confirmation and permission control, it can also participate in building new tools, allowing the system to gradually develop the characteristics of self-development, self-evolution, and capability reuse.

### 2. Reusing existing skills: keep using capabilities accumulated elsewhere

Many heavy AI users have already built up their own skills, prompts, process documents, scripts, or working methods in other tools. datawork does not require these assets to be rebuilt from scratch. By configuring a path, existing skills can be brought into the current workflow and reused directly.

This allows personal capability assets scattered across different tools to be read, understood, and reused by both the General Agent and the Code Agent. Users do not have to be locked into a single IDE, AI platform, or workflow. Instead, proven methods can gradually move into a more open, connectable, and durable local system.

### 3. Todo system: turn fragmented thoughts into executable tasks

datawork includes a complete three-tier Todo system (List / Todo / Task) with a smooth visual interface. Daily thoughts, temporary development decisions, and next actions in a project can be quickly captured, broken down, and completed.

More importantly, this Todo system is convenient for both humans and Agents. A user can copy the path of a Todo or list and send it to an Agent; the Agent can then start working around those tasks, and, with permission, maintain the todo list, update progress, and add subtasks. In this sense, datawork is not only a recording tool, but a system that connects scattered thinking, task management, and Agent action.

This makes thought accumulation lightweight. Many fragmented ideas do not need to become complex documents first, nor do they depend on a specific IDE or project-management system. They can first be captured and organized, then handed to an Agent or external tool when needed.

### 4. Collaboration mode: manage long-term context in complex tasks

The Main AI interface includes a collaboration mode. While the Code Agent is running a complex development, debugging, or long-running task, the user can still talk with the General Agent to organize the current conversation, preserve intermediate conclusions, refine context, update todos, or calibrate the next step.

The value of this mode is not just that multiple Agents can work at the same time. It is that the context of a complex task can be continuously organized and preserved. The user participates in key judgments, the General Agent explains, summarizes, and carries context, and the Code Agent performs project-level execution. Even if the task is reopened two months later, the Agent can quickly understand the original situation, decisions, and progress, then continue more accurately.

### 5. Code study: turn every commit into reviewable knowledge

During development, every Git commit can later be read, reviewed, and discussed in datawork's Git interface. Users can continuously add notes, comments, and code-study records around a specific commit, and those records are persisted into the notes of that commit.

Users can also copy the study clue of a commit and discuss it with any external Agent tool, allowing that tool to analyze the commit's diff, message, and existing notes. This helps improve code quality, makes it easier to understand how a project evolves, and turns code review and learning into something more durable than a one-time commit record.

### 6. File Transfer Assistant: capture and connect materials across phone and desktop

datawork also includes practical, high-frequency tools such as the File Transfer Assistant. Users can quickly transfer, temporarily store, and capture files or materials between phone and desktop, bringing transient information into their local workspace in time.

This may look like a small capability, but it matters in real workflows. Screenshots, files, temporary materials, and mobile-captured content no longer have to remain scattered across devices; they can more easily enter later search, organization, Todo, memory, and Agent workflows.

## License

datawork is currently **proprietary software**, not an open-source project, and its source code is not publicly available. The Windows desktop application is available for download and supports **Windows 10 and above** — it can be installed and used directly. This is the only product form currently released to the public. For distribution authorization, commercial use, or other external collaboration, please contact the author.

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




