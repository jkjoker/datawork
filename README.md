<div align="center">

<img src="https://github.com/jkjoker/datawork/blob/datawork/images/datawork_logo_new.png" alt="datawork" width="128" />

# datawork

**Local-First Personal AI Agent System**

*For anyone who encodes — 给每一个需要对信息进行编码的人*

<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Platform-Windows-blue?logo=windows" alt="Windows" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Built%20with-Python-3776AB?logo=python&logoColor=white" alt="Python" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Achangelog"><img src="https://img.shields.io/badge/Version-3.8.7f10.1.17.20260913-green" alt="Version" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/License-Proprietary-red" alt="License" /></a>

[官方主页](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout) · [下载](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout) · [更新日志](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Achangelog)

---

[English](#english) | 简体中文

</div>

## 目录

- [项目简介](#项目简介)
- [30 秒理解 datawork](#30-秒理解-datawork)
- [datawork 与其他工具的关系](#datawork-与其他工具的关系)
- [核心特性](#核心特性)
- [架构总览](#架构总览)
- [Code 模式与多种内核形态](#code-模式与多种内核形态)
- [双 Agent 系统](#双-agent-系统)
- [工具体系（三层）](#工具体系三层)
- [模型、协议与供应商](#模型协议与供应商)
- [记忆、Todo 与数据](#记忆todo-与数据)
- [可观测性：AI 调用账本](#可观测性ai-调用账本)
- [安全与权限](#安全与权限)
- [任务编排：输入队列与跨模块引用](#任务编排输入队列与跨模块引用)
- [Web Studio 与多端](#web-studio-与多端)
- [内置教程体系](#内置教程体系)
- [界面预览](#界面预览)
- [快速开始](#快速开始)
- [适合谁](#适合谁)
- [一个典型工作流](#一个典型工作流)
- [具体案例](#具体案例)
- [性能与工程化](#性能与工程化)
- [许可证](#许可证)
- [技术栈](#技术栈)
- [联系](#联系)

## 项目简介

datawork 是一个**本地优先（Local-First）**的个人 AI Agent 系统。它把个人资料、AI 对话、记忆、待办、项目、脚本、插件和标准 MCP 协议放进同一个本地工作环境，让 AI 不只停留在聊天框，而是进入你的长期工作流。

datawork 关注的不是“让 AI 一次性回答一个问题”，而是帮助你在阅读、写作、编码、整理、复盘和执行中，持续沉淀自己的上下文、经验、工具和工作流。

它的初心是让每个人得到 **AI、编码、记录** 三种力量的联合助力：AI 扩展思考能力，编码扩展行动能力，记录保存原始数据、思考痕迹和任务过程，从而**更好地关注自己的想法与思考、专注真实业务，并在每一次行动中实现有效积累**。

**核心特性**：本地优先的工作区存储，无需 datawork 账号、无需注册、无需登录。工作区数据默认保存在本地（SQLite + 文件）。你可以按需接入任意第三方模型 API，模型与供应商都可以自行注册与扩展。支持中英文界面。可通过 Python 插件无限拓展其能力，也可对接任意标准 MCP server。

**日用场景**：翻译、阅读辅助、日常对话、本地搜索查阅、文件编辑、项目笔记、待办协作、小脚本的创作与运行、自定义工具开发、代码审核与研读等，也有专属的 Code Agent，可用于复杂项目代码开发。目前 datawork 的 Code Agent 已实现完全全程在 datawork 中开发 datawork 自身。

<div align="center">
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020260619221829.png" width="55%" />
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020260619222051.png" width="35%" />
</div>

## 30 秒理解 datawork

> **一个本地优先的个人 AI Agent 系统：以 Code Agent 为核心内核，向上承载多种 Agent 形态，向下统一模型协议族、工具、记忆与 Todo——把 AI 从聊天框变成可长期运转的本地工作系统。**

```
┌──────────────────────────────────────────────────────────────────┐
│ 入口层   主界面 AI（Code 模式）· Coder 区 · Web Studio            │
│          命令行终端 · Mini 全局窗口 · 手机浏览器                   │
├──────────────────────────────────────────────────────────────────┤
│ 形态层   内置 Code │ ACP 外部 Agent │ ACP Sub-Agent               │
│          DSH（可选内核）│ Workflow（垂直 Agent 运行环境）           │
├──────────────────────────────────────────────────────────────────┤
│ 能力层   三层工具（内置 / 插件 / 标准 MCP）· 记忆 · Todo           │
│          输入队列 · 跨模块引用 · 内置教程 · 权限与审批              │
├──────────────────────────────────────────────────────────────────┤
│ 模型层   协议族（OpenAI 兼容 / Responses / Anthropic / Gemini …）  │
│          可视化模型管理 · 自行注册模型与供应商 · 推理深度           │
├──────────────────────────────────────────────────────────────────┤
│ 数据层   SQLite + 本地文件（工作区自包含）· AI 调用账本             │
└──────────────────────────────────────────────────────────────────┘
```

## datawork 与其他工具的关系

datawork 不试图替代 ChatGPT、Cursor、Claude Code、Obsidian 或 Notion。它更像是这些工具之间的**本地上下文中心与行动层**：

- 把分散在文件、笔记、AI 对话、Todo、代码项目和自动化脚本里的内容连接起来；
- 让每次对话、任务、开发和整理都能沉淀为可搜索、可复用、可继续调用的个人资产；
- 通过 MCP 与插件体系，把 datawork 中长期积累的记忆、Todo 和工具能力带到外部编辑器与其他 Agent 工作台中。

你可以继续使用自己喜欢的工具；datawork 负责让围绕这些工具产生的上下文、任务、笔记、脚本和工具能力，沉淀到一个可搜索、可复用、可再次连接的本地系统中。

## 核心特性

| 模块 | 特性 |
|------|------|
| **Code 模式与多形态内核** | 主界面 AI 统一为 **Code 模式**，可在 **内置 Code / ACP 外部 Agent / DSH / Workflow** 之间按任务切换；Coder 区、Web Studio、命令行终端共享同一套 Code 内核 |
| **双 Agent 系统** | **通用 Agent**（多角色，日常对话 / 信息整理 / 写作）+ **Code Agent**（编码 / 调试 / 长任务多轮工具调用）；两者共享模型、记忆、待办、文件白名单、插件与 MCP 配置 |
| **ACP 外部 Agent** | 接入 Claude Code / Codex / Kimi / OpenCode / CodeBuddy 等外部 Agent；Claude Agent 可接入 DeepSeek、智谱、阿里云、MiniMax、小米等国产平台；带权限审批与 MCP 工具注入 |
| **ACP Sub-Agent** | 不依赖外部 Agent 的完整系统，只取它背后的专项能力（搜索 / 研究 / 代码分析）当作工具调用 |
| **Workflow** | 垂直 Agent 运行环境：把该领域的 skill、提示词、工具等全部当作这个 Agent 自己的记忆的一部分，随时编辑、精准维护；支持自建多个 workflow、按需隐藏；内置首个业务核心「职位筛选」 |
| **工具与扩展** | 三层工具体系：内置工具（文件 / 检索 / 执行 / 互动）+ datawork 插件（写一个 Python 文件即可补充能力）+ 标准 MCP（既可接入任意外部 server，也可将 datawork 的记忆库与 Todo 系统开启为 MCP server，供其他应用连接调用）|
| **模型、协议与供应商** | 内置多种协议族（OpenAI 兼容 / Responses / Anthropic / Gemini 等）；可视化模型管理（思考 🧠 / 视觉 👁 / 工具 🔧 三种能力徽章）；可自行注册未内置模型与供应商，接入中转 / 第三方网关；支持推理深度档位 |
| **记忆与待办** | 多记忆库（全文搜索 / 类型标记 / 右键添加 / 复制路径）+ 三层 Todo 系统（清单 / Todo / Task，支持固定与备注）+ AI 对话、项目经验与任务过程的长期沉淀 |
| **可观测性** | **AI 调用账本**：全系统每次模型调用可查 token / 缓存命中 / 费用 / 耗时 / 来源入口，带数据分析页 |
| **多 Tab 与并行** | 笔记、命令行终端、Code 模式、资源管理器、编辑器均支持多 Tab；Code 模式支持多个会话同时运行 |
| **任务编排** | 输入队列（待办 / 任务 / 记忆一键送入指定队列排队执行）+ 跨模块引用（输入框用 @ 引用 Todo / 文件 / 文件夹 / 记忆 / Skill）|
| **特色机制** | 工具权限审批（按只读 / 写入 / 执行分级）+ 会话级权限模式（跟随全局 / 自动批准 / 每次询问）+ Agent 主动提问 + Agent 主动延迟 + 用户主动干预（多轮中途插话）+ 智能滚动（贴底跟随、阅读历史不打扰）|
| **Coder 编辑器与 Git** | 多 Tab 文件编辑 + 资源管理器（路径直达、自动刷新）+ Git 集成（本地备份 / 远程推送 / 工作区·暂存区·提交历史三种 Diff 查看器 / 提交历史代码研读对话，沉淀到 git notes）+ Markdown / HTML / SVG 实时预览 + 图片查看器 |
| **Web Studio 与移动** | **把本地电脑变成一台「云电脑」**：默认在局域网内，手机或任意浏览器打开即可像坐在电脑前一样对话、读写文件、操作工作区；若自己有服务器，配置中转后在外网也能正常使用 |
| **内置教程** | 教程随程序内置，Agent 可通过工具读取教程并给出准确指导——不熟悉的功能直接问 Agent 即可 |
| **数据与安全** | 本地工作区存储（SQLite + 文件）；文件白名单 + 工具权限分级 + 会话级缓存；Web 请求自动识别（避免桌面端弹窗卡死）|

## 架构总览

datawork 的骨架可以概括为「**双内核 + 三层工具 + 协议族 + 本地数据**」：

- **双内核**：Code Agent 内核（独立上下文管理、token 阈值压缩、工具编排）与通用 Agent 内核（多角色，面向日常与跨模块任务）。
- **三层工具**：内置工具 → datawork 插件 → 标准 MCP。命名严格区分，**「MCP」一词专指标准 MCP 协议**，不与前两层混称。
- **协议族**：模型接入统一走协议抽象层，新增供应商无需单独适配；未内置的供应商会自动走通用协议适配。
- **本地数据**：记忆、Todo、会话、研读笔记、配置全部落在本地工作区（SQLite + 文件），工作区自包含、可整体备份；数据路径统一基于用户设置的全局基础路径。

## Code 模式与多种内核形态

主界面 AI 已统一为 **Code 模式**。同一个入口下，可以按任务选择不同的内核形态：

| 形态 | 说明 |
|------|------|
| **内置 Code** | 默认形态，开箱即用。完整的 Code Agent 内核：文件读写、检索、命令执行、代码语义搜索、Todo 工具、协作工具、上下文压缩 |
| **ACP 外部 Agent** | 以标准 ACP（Agent Client Protocol）接入外部 Agent。模型动态发现、推理深度配置、权限审批、MCP 工具注入一应俱全；Claude Agent 还可接入 10+ 家国产模型平台 |
| **ACP Sub-Agent** | 把外部 Agent 的**专项能力**（搜索、研究、代码分析等）单独取出来，作为工具供内置 Agent 调用；每次调用独立、权限自动批准、模型可按 profile 覆盖 |
| **DSH** | 声明式 Agent 内核，线协议与工具输出对齐 DeepSeek Harness 官方实现。保留为**可选内核**，在「Code Agent 设置 → DSH」中开启即可使用 |
| **Workflow** | 垂直 Agent 运行环境（见下节）。支持用户自建、多 workflow 切换、按需在 Agent 选择器中显示或隐藏 |

**会话自由流动**：会话不绑定产生它的模式。历史列表不按来源过滤，打开旧会话时会归一化进当前内核继续推进，因此切换形态不会丢失任何历史资产。

**Workflow：垂直 Agent 运行环境**

Workflow 不是流程编排，而是**为某个专业领域策展一个 Agent 运行环境**——让 Agent 在干扰更少的环境中自主工作。

它的核心思路是：**把该领域的 skill、提示词、工具等，全部当作这个 Agent 自己的记忆的一部分**。它们不是写死在程序里的功能，而是随时可以编辑、可以精准维护的资产——你对这个领域的理解变了，改一改它就跟上了。

- **随时编辑、精准维护**：提示词、判断标准、工具与 skill 都可以直接改，改完立即生效，不需要等待版本更新。
- **可自建、可切换**：支持定义多个 workflow，在选择器里按需显示或隐藏；每个 workflow 可独立配置用户项目工作区与 Git 上下文。
- **内置业务核心「职位筛选」**：领域化提示词 + 专属工具 + 成体系的筛选标准 + 浏览器采集工具，开箱即用，也可作为自建 workflow 的参考模板。

## 双 Agent 系统

两套各自独立、可并行使用的 Agent 系统：

- **通用 Agent**：日常对话、信息整理、跨域助理；可同时存在多个角色（A/B/…）；入口在 Mini 全局窗口、Web 端与命令行终端。
- **Code Agent**：专注编码、调试、代码理解；强工作目录概念（项目根 + Git 上下文）；独立上下文管理与阈值压缩；入口在主界面 AI 的 **Code 模式**、Coder 区、Web Studio 与命令行终端。

两者**共享**：模型管理、记忆库、Todo 系统、文件白名单、datawork 插件、外部 MCP server、研读笔记。

## 工具体系（三层）

```
L1 内置工具      ← datawork 自带，开箱即用
L2 datawork 插件 ← 写一个 Python 文件即可补充能力
L3 标准 MCP      ← 接入外部 server，与 Cursor / Claude Desktop 等共享
```

- **内置工具**：覆盖文件读写与检索、命令与脚本执行、代码语义搜索、记忆操作、网页解析、Todo 操作、主动提问与主动等待、代码研读笔记等。
- **datawork 插件**：把一个 Python 文件放进插件目录即被识别；可见性两态（常驻 / 按需查阅）；通用 Agent 与 Code Agent 共享一份。
- **标准 MCP**：填入 server 启动命令即可接入外部 MCP server；通用 Agent 与 Code Agent 共享同一份 MCP 协议层；同时可将 datawork 自身的记忆库与 Todo 系统开启为 MCP server，让 Cursor、Claude Desktop 等其他应用直接连接调用。

## 模型、协议与供应商

- **协议族**：内置 OpenAI 兼容、Responses、Anthropic、Gemini 等主流协议形态；自定义供应商可选用协议模板，也可自动走通用协议适配。
- **统一模型配置编辑器**：编辑锁定 / 浏览可切换双形态，三个入口（主界面、Coder、Code Agent 设置）行为统一。
- **自行注册**：可注册未内置的模型，补充它的能力、上下文长度、价格与显示名；也可自行添加外部供应商与中转 / 第三方网关。
- **能力管理**：可视化模型管理，思考 🧠 / 视觉 👁 / 工具 🔧 三种能力徽章；推理深度按官方文档分档，并支持用户覆盖内置元数据。
- **国产模型适配**：已针对 DeepSeek、Kimi、小米 MiMo、Qwen、GLM 等模型做重点适配，思考模式 + 工具调用全程流式输出。
- **一致性保障**：模型被删除后会一并清理各处引用，发送前校验、界面即时同步，不会带着失效模型名发请求。

## 记忆、Todo 与数据

- **记忆系统**：多记忆库、全文搜索、类型标记、右键“添加到记忆”、复制记忆路径；Agent 可通过内置工具对记忆进行查询、新增、更新与整理。
- **Todo 系统**：清单 / Todo / Task 三层结构，支持固定与备注；既方便人使用，也方便 Agent 使用——用户可以把 Todo 或清单路径发给 Agent，Agent 围绕任务行动并在授权下维护进度。
- **数据稳定性**：所有数据库采用短连接 + 线程隔离，保持单文件自包含，在云同步目录下也不会因“文件被占用不同步”而丢数据。
- **路径基准**：数据路径统一基于用户设置的全局基础路径，不隐式回退到随机目录。

## 可观测性：AI 调用账本

全系统每一次模型调用都会留下记录：

- **记录内容**：token 用量、缓存命中、费用（绑定调用当时的价格快照）、耗时（含首 token 时间）、来源入口与会话归属。
- **互斥桶设计**：明确区分“供应商返回 0”与“供应商没返回”，不把未知当成零。
- **覆盖范围**：主界面、Code Agent、Coder、Mini Chat、Web 端、Workflow、ACP 外部 Agent、ACP Sub-Agent 等全部入口；外部 Agent 进程内的调用标记为“不可观测”，不与零值混淆。
- **数据分析页**：按供应商 / 模型 / 会话 / 状态 / 入口 / 时间维度过滤与汇总，支持 CSV 导出；成本统一按人民币统计。
- **写入安全**：账本写入完全 fail-open，不影响主调用链路；异常时通过可重放的日志兜底与启动恢复暴露风险。

## 安全与权限

- **工具风险分级**：所有工具按「只读 / 写入 / 执行」三档分级，高风险操作弹窗确认。
- **会话级权限模式**：跟随全局 / 自动批准 / 每次询问三种，可针对单个会话覆盖，不必被反复弹窗打断。
- **文件白名单**：限制 Agent 可访问的路径范围；触及白名单外路径时，弹窗可一键追加白名单并放行。
- **ACP 权限审批**：拦截外部 Agent 的权限与终端反向请求，按工具类型做会话级缓存；命令行操作必须经过 DataWork 审批。
- **Web 端策略**：自动识别 Web 请求，避免浏览器用户因看不到桌面弹窗而卡死。
- **信息脱敏**：自定义服务商地址遮蔽、错误信息脱敏，不把密钥写入日志。

## 任务编排：输入队列与跨模块引用

- **输入队列**：持久化消息队列，支持把 Todo / Task / 记忆条目的**路径信息**推送到指定队列上下文（Coder / Mini Chat / 主界面 Code），实现任务编排；发送路径而非原文，便于 Agent 定位与操作具体条目。支持自动出队、手动管理、历史搜索与草稿箱。
- **跨模块引用**：在输入框用 @ 引用 Todo / 文件 / 文件夹 / 记忆 / Skill，弹出框支持搜索过滤与键盘导航；已接入主界面、Coder、Mini Chat 等多个入口。

## Web Studio 与多端

Web 工作台的意义不只是「网页版」，而是**把本地电脑变成一台云电脑**——在手机或任意浏览器上打开，就能像坐在电脑前一样使用它：对话、读写文件、操作工作区、推进任务。电脑仍在本地运行，浏览器只是你的操作入口，数据始终留在自己的机器上。

- **默认：局域网内直接可用**。手机、平板、其他电脑连上同一个网络，打开浏览器就能用，不需要额外配置。
- **进阶：自己配一台中转，在外网也能用**。如果你有自己的服务器，配置好中转，电脑放在家里开着，人在外面也能正常使用。
- **安全、便利、功能完整、可扩展**。访问有密码保护；浏览器端能做的事与坐在电脑前基本一致；局域网开箱即用、外网只需自己配一台中转；整套能力也仍可继续扩展。
- **Web Studio**：对话流与交互**参考 DeepSeek DSH 项目的 UI 设计**；包含对话、工作区管理、会话管理（标题筛选 / 导航时间线）、用量统计与上下文圆环、背景图等；支持刷新不中断与自动恢复、多任务并行运行。
- **Web Coder 编辑器**：按 VSCode Workbench 风格重构，接入真实工作区与原生 Git；提供工作区 / 暂存区 / 提交历史三种 Diff 查看器、图片查看器、Markdown / HTML / SVG 实时预览与全工作区搜索替换。
- **其他页面**：chat、PPT 工作台、多媒体播放器、Vlog 录制、文件传输助手、PDF 阅读器。

## 内置教程体系

教程随程序内置（作为代码打包，不依赖外部文件），并接入 Agent 工具：

- 覆盖入门理解、数据与知识、开发流程、会话与文件、系统维护等模块；
- 新功能（Workflow、ACP Agent、模型管理等）均有对应教程；
- Agent 可通过工具读取教程内容，长教程自动分段，避免被上下文预算截断；
- 因此遇到不熟悉的功能，**直接问 Agent 即可得到基于当前版本的准确指导**。

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

初次使用建议：

1. 在「模型管理」中添加模型（推荐 DeepSeek，协议选「内置协议」）；
2. 配置全局基础路径与笔记保存路径；
3. 发一条消息确认 AI 已正常联通，即可开始使用。

配置成功后，可以直接问 Agent 任何「怎么做」的问题——它会读取内置教程，给出针对当前版本的准确说明。例如：

- **这个 Workflow 怎么用？**
- **怎么创建一个 Workflow？**
- **怎么创建一个插件？**
- **某个插件怎么用？**
- **ACP / DSH / 模型管理 / 记忆 / Todo 怎么用？**

凡是教程覆盖到的功能，直接问即可。

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
2. 用通用 Agent 讨论需求、收集信息、生成 Todo；
3. 在主界面 AI 的 Code 模式里读取项目、编辑文件、运行脚本、调试或审核代码（也可按任务切换到 ACP 外部 Agent 或 Workflow）；
4. 将关键结论沉淀到记忆库，将任务进度保存在 Todo 系统中；
5. 将 datawork 的记忆库和 Todo 系统开启为 MCP server，让 Cursor、Claude Desktop 等外部工具继续连接使用。

## 具体案例

以下案例并不是额外的宣传口号，而是 datawork 在真实使用和开发过程中已经形成的工作方式。它们对应的都是很具体的问题：能力如何沉淀、上下文如何长期保存、碎片想法如何变成行动、不同工具之间如何重新连接。

### 1. 在 datawork 中开发 datawork：Code Agent 的真实能力验证

datawork 的 Code Agent 目前已经实现完全全程在 datawork 中开发 datawork 自身——从需求讨论、代码阅读、文件编辑、脚本运行、调试排查到提交管理，整个开发过程都不需要离开 datawork。

开发过程中积累的所有内容——Todo、变更记录、记忆片段、Skills、插件——全部自然地沉淀在 datawork 的本地工作区中，后续可以随时检索、复盘和复用。

### 2. 自进化的能力：把临时需求沉淀为可复用工具

在使用或开发过程中，如果遇到新的具体需求，可以按需临时开发一个本地 datawork 插件。插件开发完成后，通用 Agent 与 Code Agent 都可以调用同一份能力。

这意味着一次性的任务处理，可以进一步沉淀为长期可复用的工具：Agent 不只是使用现有工具，也可以在人的确认和权限控制下参与开发新工具，让系统逐步具备“自主开发、自主进化、能力复用”的特征。

### 3. 复用已有 Skills：把过去积累的能力继续用起来

很多重度 AI 用户已经在其他工具中积累了自己的 skills、提示词、流程文档、脚本或工作方法。datawork 不要求这些积累从零开始重建，而是可以通过配置路径的方式，把已有的 skills 继续纳入当前工作流。

这让过去分散在不同工具里的个人能力资产，可以被通用 Agent 和 Code Agent 继续读取、理解和复用。用户不必被某一个 IDE、某一个 AI 平台或某一种工作流绑定，而是可以把已经验证有效的方法逐步迁移到一个更开放、可连接、可长期沉淀的本地系统中。

### 4. Todo 系统：让碎片想法快速变成可执行任务

datawork 内置了完整的三层 Todo 系统（清单 / Todo / Task）和顺畅的可视化界面。日常想到的事情、开发中的临时判断、项目中的下一步动作，都可以快速记录、快速拆分、快速完成。

更重要的是，这套 Todo 既方便人使用，也方便 Agent 使用：用户可以复制 Todo 或清单路径发给 Agent，Agent 就能围绕这些任务开始行动，也可以在授权下维护待办事项、更新进度、补充子任务。datawork 因此不只是一个记录工具，而是一个把零散思考、任务管理和 Agent 行动连接起来的系统。

### 5. Workflow：把专业领域策展成垂直 Agent 环境

有些任务不是“把指令说清楚”就能做好，而是需要一整套被策展过的环境：领域化的提示词、专用的工具集、成体系的判断标准、以及只在这个领域里出现的上下文。

Workflow 的核心思路是：**把 skill、提示词、工具等全部当作这个 Agent 自己的记忆的一部分**。它们不是写死在程序里的功能，而是随时可以编辑、可以精准维护的资产——你对这个领域的理解变了，改一改它就跟上了。

用户既可以使用内置的 Workflow（例如「职位筛选」），也可以自己定义一个：把平时反复口述给 AI 的那套方法，连同它需要的工具和判断标准，一起沉淀成可复用、可迭代、可维护的 Agent 环境。

### 6. Code Agent 的协作能力：让长任务上下文可以交接

Code Agent 默认具备协作定位与读取能力：它可以定位当前会话、读取对话历史、生成并读取协作文档的路径。当任务很长、上下文开始混乱，或需要把进展交接出去时，这套能力让上下文可以被整理、被交接、被重新接续。

协作文档本身通过通用的文件编辑工具维护，走正常的写入审批流程——协作能力不是一套独立机制，而是长任务上下文管理的一部分。因此即使两个月后重新打开任务，Agent 也能快速理解当时的原貌、决策和进展，从而更准确地继续推进。

### 7. 代码研读：让每一次提交都成为可复盘的知识资产

在开发过程中，每一次 Git 提交都可以在 datawork 的 Git 界面中被后续阅读、审核和讨论。用户可以围绕某一次提交持续追加笔记、备注和研读记录，这些内容会沉淀到对应提交的 notes 中。

同时，用户也可以复制某次提交的研读线索，与外部任意 Agent 工具继续沟通，让外部工具围绕该提交的 diff、说明和已有笔记进行辅助分析。这有助于提升代码质量，帮助用户理解项目演化过程，也让代码审查和学习不再只停留在一次性的提交记录里。

### 8. 文件传输助手：随时捕获并连接手机与电脑之间的资料

datawork 也包含文件传输助手这类具体而高频的小工具。用户可以在手机和电脑之间快速传输、暂存和捕获文件或资料，把临时出现的信息及时接入自己的本地工作区。

这类能力看起来很小，但在真实工作流中非常重要：它让截图、文件、临时资料和移动端捕获的内容不再散落在不同设备里，而是更容易进入后续的搜索、整理、Todo、记忆和 Agent 工作流。

## 性能与工程化

- **启动更快**：按需延迟加载，主界面、编码区、写作区的打开明显更快。
- **长会话更稳**：会话数据改为增量追加写入，长会话写入更快、更抗中断。
- **缓存命中**：工具定义顺序稳定化，提升模型前缀缓存命中率；界面实时显示缓存命中与上下文用量。
- **日志降噪**：日志分级重构，日常运行不刷屏，仅在排查时展开调用链；不记录密钥与完整请求内容。
- **统一重试**：网络抖动按异常类型差异化重试（连接类与 5xx 上限更高、超时类更保守），指数退避且可立即终止。
- **数据稳定**：所有数据库统一短连接与线程隔离，保持单文件自包含，云同步目录下不丢数据。

## 许可证

datawork 当前为**专有软件**，不是开源项目，源码未对外开放。Windows 桌面应用已开放下载，支持 **Windows 10 及以上系统**，可直接安装使用，这也是目前唯一对外开放的产品形态。若有分发授权、商业使用或其他对外合作需求，请联系作者沟通。

## 技术栈

| 领域 | 技术 |
|------|------|
| 桌面应用 | Python, Tkinter |
| Web 服务 | FastAPI / Uvicorn / Jinja2 |
| AI 接入 | 协议抽象层：OpenAI 兼容 / Responses / Anthropic / Gemini 等协议族；支持自行注册模型与供应商 |
| Agent 协议 | ACP（Agent Client Protocol） |
| 工具协议 | MCP（Model Context Protocol） |
| 向量检索 | Embedding + Vector Database（实验室模块） |
| 数据存储 | SQLite + 本地文件（记忆 / 待办 / 会话 / 配置 / 研读笔记） |
| 可观测性 | AI 调用账本（独立数据库 + 数据分析页） |
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

## Contents

- [About](#about)
- [datawork in 30 Seconds](#datawork-in-30-seconds)
- [How datawork Relates to Other Tools](#how-datawork-relates-to-other-tools)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [Code Mode and Multiple Kernel Forms](#code-mode-and-multiple-kernel-forms)
- [Dual-Agent System](#dual-agent-system)
- [Tool System (Three Layers)](#tool-system-three-layers)
- [Models, Protocols and Providers](#models-protocols-and-providers)
- [Memory, Todos and Data](#memory-todos-and-data)
- [Observability: AI Call Ledger](#observability-ai-call-ledger)
- [Security and Permissions](#security-and-permissions)
- [Task Orchestration: Input Queue and Cross-Module References](#task-orchestration-input-queue-and-cross-module-references)
- [Web Studio and Multi-Device](#web-studio-and-multi-device)
- [Built-in Tutorial System](#built-in-tutorial-system)
- [Screenshots](#screenshots)
- [Quick Start](#quick-start)
- [Who It Is For](#who-it-is-for)
- [A Typical Workflow](#a-typical-workflow)
- [Concrete Use Cases](#concrete-use-cases)
- [Performance and Engineering](#performance-and-engineering)
- [License](#license)
- [Tech Stack](#tech-stack)
- [Contact](#contact)

## About

datawork is a **local-first** personal AI Agent system. It brings your personal files, AI conversations, memory, todos, projects, scripts, plugins, and the standard MCP protocol into one local workspace — so AI does not stay inside a chat box, but becomes part of your long-term workflow.

datawork is not about asking AI to answer one question at a time. It is about helping you continuously accumulate context, experience, tools, and workflows as you read, write, code, organize, review, and execute.

Its original motivation is to combine three kinds of power for individuals: **AI, coding, and recording**. AI extends thinking, coding extends action, and recording preserves raw materials, thought traces, and task processes — empowering you to **better focus on your thoughts and real-world tasks, and achieve effective accumulation in every action**.

**Core Specs**: Local-first workspace storage, no datawork account, no registration, no login required. Workspace data is stored locally by default (SQLite + files). You can connect to any third-party model API, and both models and providers can be registered and extended by yourself. **Multi-language UI (English/Chinese)**. Extensible via Python plugins, and connectable to any standard MCP server.

**Daily Use Cases**: Translation, reading assistance, daily chat, local search, file editing, project notes, todo collaboration, script creation & execution, custom tool development, code review & study, etc.; it also includes a dedicated Code Agent for complex project code development. The Code Agent has already been used to develop datawork itself entirely within datawork, end to end.

<div align="center">
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020260619221829.png" width="55%" />
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020260619222051.png" width="35%" />
</div>

## datawork in 30 Seconds

> **A local-first personal AI Agent system: the Code Agent core sits at the center, multiple Agent forms are layered on top, and model protocol families, tools, memory, and todos are unified underneath — turning AI from a chat box into a durable local working system.**

```
┌──────────────────────────────────────────────────────────────────┐
│ Entry     Main AI (Code mode) · Coder · Web Studio               │
│           Terminal · Mini global window · Mobile browser          │
├──────────────────────────────────────────────────────────────────┤
│ Forms     Built-in Code │ ACP external Agent │ ACP Sub-Agent     │
│           DSH (optional kernel) │ Workflow (vertical Agent env)  │
├──────────────────────────────────────────────────────────────────┤
│ Abilities Three-layer tools (built-in / plugins / standard MCP)   │
│           Memory · Todo · Input queue · References · Tutorials    │
├──────────────────────────────────────────────────────────────────┤
│ Models    Protocol families (OpenAI-compatible / Responses /      │
│           Anthropic / Gemini …) · visual model manager            │
├──────────────────────────────────────────────────────────────────┤
│ Data      SQLite + local files (self-contained workspace)         │
│           AI call ledger                                          │
└──────────────────────────────────────────────────────────────────┘
```

## How datawork Relates to Other Tools

datawork does not try to replace ChatGPT, Cursor, Claude Code, Obsidian, or Notion. It acts more like a **local context hub and action layer** between these tools:

- Connect content scattered across files, notes, AI conversations, todos, code projects, and automation scripts;
- Turn every conversation, task, development session, and organizing effort into searchable, reusable, and callable personal assets;
- Bring the memory, todos, and tool capabilities accumulated in datawork to external editors and other Agent workbenches through MCP and the plugin system.

You can keep using the tools you already like. datawork's role is to help the context, tasks, notes, scripts, and tool capabilities produced around those tools settle into a local system that can be searched, reused, and connected again.

## Key Features

| Category | Features |
|----------|----------|
| **Code Mode & Multiple Kernels** | The Main AI is unified as **Code mode**, where you can switch between **Built-in Code / ACP external Agent / DSH / Workflow** per task; the Coder area, Web Studio, and terminal share the same Code kernel |
| **Dual-Agent System** | **General Agent** (multi-role, daily chat / info organization / writing) + **Code Agent** (coding / debugging / long multi-turn tool calls); both share models, memory, todos, file whitelist, plugins & MCP config |
| **ACP External Agents** | Connect Claude Code / Codex / Kimi / OpenCode / CodeBuddy and more; the Claude Agent can also connect to 10+ Chinese model platforms (DeepSeek, Zhipu, Aliyun, MiniMax, Xiaomi, …); with permission approval and MCP tool injection |
| **ACP Sub-Agent** | Take only the specialized capability behind an external Agent (search / research / code analysis) and call it as a tool |
| **Workflow** | A vertical Agent runtime environment: the domain's skills, prompts, and tools are all treated as part of that Agent's own memory, editable at any time and maintained precisely; supports authoring multiple workflows and hiding them on demand; ships with a first business core, "Job Screening" |
| **Tools & Extensibility** | Three-layer tool system: built-in tools (file / search / exec / interaction) + datawork plugins (drop in a Python file to extend) + standard MCP (connect to any external server, and expose datawork's memory libraries and Todo system as an MCP server for other apps to use) |
| **Models, Protocols & Providers** | Built-in protocol families (OpenAI-compatible / Responses / Anthropic / Gemini, etc.); visual model manager with reasoning 🧠 / vision 👁 / tools 🔧 capability badges; register your own models and providers, including relay/third-party gateways; reasoning-depth tiers |
| **Memory & Todos** | Multi memory libraries (full-text search / type tagging / right-click add / copy path) + three-tier Todo system (List / Todo / Task, with pinning and notes) + long-term accumulation of AI conversations, project experience, and task processes |
| **Observability** | **AI call ledger**: every model call across the system records tokens / cache hits / cost / latency / entry point, with a data analysis page |
| **Multi-Tab & Parallelism** | Notes, terminal, Code mode, file explorer, and editor all support multiple tabs; Code mode can run several sessions in parallel |
| **Task Orchestration** | Input queue (send todos / tasks / memory entries into a chosen queue context) + cross-module references (@-reference todos / files / folders / memory / skills in any input box) |
| **Signature Mechanisms** | Tiered tool-call approval (read-only / write / execute) + session-level permission modes (follow global / auto-approve / ask every time) + Agent-initiated questions + Agent-initiated waits + user mid-loop intervention + smart auto-scroll |
| **Coder Editor & Git** | Multi-tab editing + file explorer (path jump, auto-refresh) + Git integration (local backup / remote push / three diff viewers for workspace, staged, and commit history / commit-history code-study chat persisted via git notes) + Markdown / HTML / SVG live preview + image viewer |
| **Web Studio & Mobile** | **Turns your local computer into a "cloud computer"**: works on your LAN by default — open it in a phone or any browser and use it as if you were sitting in front of it; and if you have your own server, a relay lets you use it from anywhere |
| **Built-in Tutorials** | Tutorials ship with the app and Agents can read them through a tool — just ask the Agent about any feature you are unfamiliar with |
| **Data & Safety** | Local workspace storage (SQLite + files); file whitelist + tiered tool permissions + session-level cache; web request auto-detection (avoids desktop popup deadlocks) |

## Architecture

The skeleton of datawork can be summarized as **two kernels + three tool layers + protocol families + local data**:

- **Two kernels**: the Code Agent kernel (independent context management, token-threshold compression, tool orchestration) and the General Agent kernel (multi-role, for daily and cross-module tasks).
- **Three tool layers**: built-in tools → datawork plugins → standard MCP. The naming is strictly separated: **"MCP" refers only to the standard MCP protocol**, never to the other two layers.
- **Protocol families**: model access always goes through a protocol abstraction layer, so adding a provider needs no separate adapter; providers that are not built in fall back to a generic protocol adaptation.
- **Local data**: memory, todos, sessions, study notes, and configuration all live in the local workspace (SQLite + files), self-contained and backup-friendly; data paths are always derived from the user-configured base path.

## Code Mode and Multiple Kernel Forms

The Main AI is unified as **Code mode**. Under this single entry point you can pick a kernel form per task:

| Form | Description |
|------|-------------|
| **Built-in Code** | The default form, ready out of the box. A complete Code Agent kernel: file read/write, search, command execution, semantic code search, todo tools, collaboration tools, context compression |
| **ACP external Agent** | Connect external Agents via the standard ACP (Agent Client Protocol). Dynamic model discovery, reasoning-depth configuration, permission approval, and MCP tool injection are all included; the Claude Agent can additionally connect to 10+ Chinese model platforms |
| **ACP Sub-Agent** | Extract only the **specialized capability** of an external Agent (search, research, code analysis) and expose it as a tool for the built-in Agent; each call is isolated, permissions are auto-approved, and the model can be overridden per profile |
| **DSH** | A declarative Agent kernel whose wire protocol and tool output are aligned with the official DeepSeek Harness implementation. Kept as an **optional kernel** — enable it under "Code Agent Settings → DSH" |
| **Workflow** | A vertical Agent runtime environment (see below). Supports user authoring, multi-workflow switching, and hiding from the Agent selector on demand |

**Sessions flow freely**: a session is not bound to the mode that produced it. The history list is not filtered by origin, and opening an old session normalizes it into the current kernel — so switching forms never loses history.

**Workflow: a vertical Agent runtime environment**

Workflow is not flow orchestration. It is a way to **curate an Agent runtime environment for a specific domain**, so the Agent can work autonomously with less noise.

Its core idea is that **the domain's skills, prompts, and tools are all treated as part of that Agent's own memory**. They are not features hardcoded into the program, but assets you can edit at any time and maintain precisely — when your understanding of the domain changes, you change them and the Agent follows.

- **Edit any time, maintain precisely**: prompts, judgment criteria, tools, and skills can all be changed directly, taking effect immediately without waiting for a release.
- **Author and switch**: define multiple workflows and show or hide them in the selector; each workflow can independently configure the user project workspace and Git context.
- **Built-in business core "Job Screening"**: a domain prompt + dedicated tools + a coherent screening standard + browser collection tools, ready to use and a good reference template for authoring your own workflows.

## Dual-Agent System

Two independent and parallel-usable Agent systems:

- **General Agent**: Daily chat, info organization, cross-domain assistant; supports multiple roles (A/B/…); entry points include the Mini global window, the Web UI, and the terminal.
- **Code Agent**: Focused on coding, debugging, code understanding; strong working-directory concept (project root + Git context); independent context management with threshold compression; entry points: the Main AI's **Code mode**, the Coder area, Web Studio, and the terminal.

Both **share**: model management, memory, Todo, file whitelist, datawork plugins, external MCP servers, and code-study notes.

## Tool System (Three Layers)

```
L1 Built-in tools      ← shipped with datawork
L2 datawork plugins    ← drop in a Python file to extend
L3 Standard MCP        ← connect external servers; share with Cursor / Claude Desktop / etc.
```

- **Built-in tools**: file read/write and search, command and script execution, semantic code search, memory operations, web page parsing, todo operations, Agent-initiated questions and waits, code-study notes, and more.
- **datawork plugins**: drop a Python file into the plugin directory and it is auto-detected; two visibility modes (resident / on-demand); shared by both Agents.
- **Standard MCP**: fill in a server launch command to connect an external MCP server; both Agents share the same MCP protocol layer; datawork can also expose its own memory libraries and Todo system as an MCP server, so tools like Cursor and Claude Desktop can connect to and use them directly.

## Models, Protocols and Providers

- **Protocol families**: built-in OpenAI-compatible, Responses, Anthropic, and Gemini protocol forms; custom providers can pick a protocol template or fall back to a generic protocol adaptation.
- **Unified model configuration editor**: an editable-locked / browse toggle with two forms, behaving identically across three entry points (Main AI, Coder, Code Agent settings).
- **Register your own**: register models that are not built in, including their capabilities, context window, pricing, and display name; add external providers and relay / third-party gateways.
- **Capability management**: a visual model manager with reasoning 🧠 / vision 👁 / tools 🔧 capability badges; reasoning-depth tiers follow official documentation, and user overrides of built-in metadata are supported.
- **Chinese model adaptation**: focused adaptation for DeepSeek, Kimi, Xiaomi MiMo, Qwen, GLM and others, with reasoning mode and tool calls fully streaming.
- **Consistency**: when a model is deleted, references are cleaned up across the system, validated before sending, and reflected in the UI immediately — no more requests sent with a stale model name.

## Memory, Todos and Data

- **Memory**: multiple memory libraries, full-text search, type tagging, right-click "add to memory", copy memory path; Agents can query, add, update, and organize memory through built-in tools.
- **Todo**: a three-tier structure (List / Todo / Task) with pinning and notes; convenient for both humans and Agents — send a todo or list path to an Agent and it can work around those tasks and maintain progress under permission.
- **Data stability**: every database uses short connections with thread isolation and stays self-contained in a single file, so data is not lost when a cloud-synced file is locked.
- **Path basis**: data paths are always derived from the user-configured base path, never silently falling back to a random directory.

## Observability: AI Call Ledger

Every model call in the system leaves a record:

- **What is recorded**: token usage, cache hits, cost (bound to a price snapshot at call time), latency (including first-token time), entry point, and session ownership.
- **Mutually exclusive buckets**: "the provider returned 0" and "the provider returned nothing" are explicitly distinguished; unknown is never treated as zero.
- **Coverage**: Main AI, Code Agent, Coder, Mini Chat, Web UI, Workflow, ACP external Agent, ACP Sub-Agent, and more; calls made inside an external Agent process are marked "unobservable" rather than zero.
- **Data analysis page**: filter and aggregate by provider / model / session / status / entry point / time, with CSV export; costs are reported in RMB.
- **Write safety**: ledger writes are fully fail-open and never affect the main call path; failures are surfaced through a replayable log fallback and startup recovery.

## Security and Permissions

- **Tiered tool risk**: every tool is classified as read-only / write / execute, and high-risk operations require confirmation.
- **Session-level permission modes**: follow global / auto-approve / ask every time, overridable per session, so you are not interrupted by repeated dialogs.
- **File whitelist**: restricts the paths an Agent can access; when a path outside the whitelist is touched, a dialog can add it and allow in one click.
- **ACP permission approval**: intercepts permission and terminal reverse requests from external Agents, with session-level caching keyed by tool type; command-line operations must pass DataWork approval.
- **Web-side policy**: web requests are detected automatically, so browser users are not blocked by a desktop dialog they cannot see.
- **Data masking**: custom provider addresses are masked and error messages are sanitized; keys are never written to logs.

## Task Orchestration: Input Queue and Cross-Module References

- **Input queue**: a persistent message queue that pushes the **path information** of todos / tasks / memory entries into a chosen queue context (Coder / Mini Chat / Main AI Code) for task orchestration; sending paths rather than full text makes it easy for an Agent to locate and act on specific entries. Supports auto-dequeue, manual management, history search, and a draft box.
- **Cross-module references**: type @ in any input box to reference a todo / file / folder / memory / skill, with a popup that supports search filtering and keyboard navigation; integrated into the Main AI, Coder, Mini Chat, and more.

## Web Studio and Multi-Device

The web workspace is not just a "web version". It **turns your local computer into a cloud computer** — open it in a phone or any browser and use it as if you were sitting in front of it: chat, read and write files, operate the workspace, push tasks forward. The computer keeps running locally; the browser is only your entry point, and your data never leaves your own machine.

- **Default: works right on your LAN.** A phone, tablet, or another computer on the same network just opens a browser — no extra setup.
- **Advanced: add your own relay to use it from anywhere.** If you have a server, configure a relay and your computer can stay at home, switched on, while you use it from outside.
- **Security, convenience, completeness, and extensibility are all covered.** Access is password-protected; what you can do in the browser matches sitting in front of the computer; LAN works out of the box and remote access needs only your own relay; and the whole capability set can keep growing.
- **Web Studio**: its **conversation flow and interaction follow the UI design of the DeepSeek DSH project**; it includes chat, workspace management, session management (title filter / navigation timeline), usage stats and a context ring, background image, and more; supports refresh-without-interruption, auto-recovery, and parallel multi-task runs.
- **Web Coder editor**: rebuilt in the VSCode Workbench style, connected to a real workspace with native Git; provides three diff viewers (workspace / staged / commit history), an image viewer, Markdown / HTML / SVG live preview, and whole-workspace search & replace.
- **Other pages**: chat, PPT workbench, media player, Vlog recorder, file transfer assistant, PDF reader.

## Built-in Tutorial System

Tutorials ship inside the application (packaged as code, not external files) and are exposed to the Agent as a tool:

- Covering onboarding, data and knowledge, development workflow, sessions and files, and system maintenance;
- New features (Workflow, ACP Agents, model management, etc.) each have their own tutorial;
- Agents can read tutorial content through a tool, with long tutorials split into sections so they are not truncated by the context budget;
- So when you are unfamiliar with a feature, **just ask the Agent** — it will answer based on the current version.

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

Suggested first steps:

1. Add a model in "Model Management" (DeepSeek recommended, protocol: Built-in);
2. Configure the global base path and the notes save path;
3. Send a message to confirm the AI is connected, then you are ready to go.

Once it is working, just ask the Agent any "how do I…" question — it reads the built-in tutorials and answers based on the current version. For example:

- **How do I use this Workflow?**
- **How do I create a Workflow?**
- **How do I create a plugin?**
- **How do I use a particular plugin?**
- **How do I use ACP / DSH / model management / memory / todos?**

If a feature is covered by the tutorials, just ask.

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
3. In the Main AI's Code mode, read the project, edit files, run scripts, debug, or review code (or switch to an ACP external Agent or a Workflow per task);
4. Save key conclusions into memory libraries, and keep task progress in the Todo system;
5. Expose datawork's memory and Todo as an MCP server, so external tools such as Cursor or Claude Desktop can continue to use them.

## Concrete Use Cases

The following cases are not additional marketing claims. They are real working patterns that have already emerged from using and developing datawork. They address concrete problems: how capabilities are accumulated, how context is preserved over time, how fragmented thoughts become executable actions, and how different tools can be connected again.

### 1. Developing datawork within datawork: a real proof of the Code Agent

The Code Agent in datawork has already achieved full end-to-end development of datawork itself entirely within datawork — from requirement discussion, code reading, file editing, script execution, and debugging to commit management, the entire development process does not require leaving datawork.

Everything accumulated during development — todos, change logs, memory entries, skills, plugins — is naturally preserved in datawork's local workspace, ready to be searched, reviewed, and reused at any time.

### 2. Self-evolving capability: turn temporary needs into reusable tools

During use or development, when a new concrete need appears, you can create a local datawork plugin on demand. Once the plugin is ready, both the General Agent and the Code Agent can use the same capability.

This means a one-off task can be further accumulated into a reusable tool. The Agent does not only call existing tools; with human confirmation and permission control, it can also participate in building new tools, allowing the system to gradually develop the characteristics of self-development, self-evolution, and capability reuse.

### 3. Reusing existing skills: keep using capabilities accumulated elsewhere

Many heavy AI users have already built up their own skills, prompts, process documents, scripts, or working methods in other tools. datawork does not require these assets to be rebuilt from scratch. By configuring a path, existing skills can be brought into the current workflow and reused directly.

This allows personal capability assets scattered across different tools to be read, understood, and reused by both the General Agent and the Code Agent. Users do not have to be locked into a single IDE, AI platform, or workflow. Instead, proven methods can gradually move into a more open, connectable, and durable local system.

### 4. Todo system: turn fragmented thoughts into executable tasks

datawork includes a complete three-tier Todo system (List / Todo / Task) with a smooth visual interface. Daily thoughts, temporary development decisions, and next actions in a project can be quickly captured, broken down, and completed.

More importantly, this Todo system is convenient for both humans and Agents. A user can copy the path of a Todo or list and send it to an Agent; the Agent can then start working around those tasks, and, with permission, maintain the todo list, update progress, and add subtasks. In this sense, datawork is not only a recording tool, but a system that connects scattered thinking, task management, and Agent action.

### 5. Workflow: curate a vertical Agent environment for a domain

Some tasks cannot be done well just by stating an instruction clearly. They need a whole curated environment: a domain-specific prompt, a dedicated toolset, a coherent set of judgment criteria, and the context that only appears in that domain.

The core idea of Workflow is that **the domain's skills, prompts, and tools are all treated as part of that Agent's own memory**. They are not features hardcoded into the program, but assets you can edit at any time and maintain precisely — when your understanding of the domain changes, you change them and the Agent follows.

You can use a built-in Workflow (such as "Job Screening"), or define your own: take the method you would otherwise repeat to an AI again and again, together with the tools and judgment criteria it needs, and turn it into a reusable, iterable, and maintainable Agent environment.

### 6. Code Agent collaboration: hand long-task context over

The Code Agent has built-in collaboration and reading capabilities by default: it can locate the current session, read conversation history, and produce and read the path of a collaboration document. When a task gets long, when context starts to blur, or when progress needs to be handed over, this lets the context be organized, handed over, and picked up again.

Collaboration documents themselves are maintained through the general file-editing tools and go through the normal write-approval flow — collaboration is not a separate mechanism, but part of long-task context management. So even if the task is reopened two months later, the Agent can quickly understand the original situation, decisions, and progress, then continue more accurately.

### 7. Code study: turn every commit into reviewable knowledge

During development, every Git commit can later be read, reviewed, and discussed in datawork's Git interface. Users can continuously add notes, comments, and code-study records around a specific commit, and those records are persisted into the notes of that commit.

Users can also copy the study clue of a commit and discuss it with any external Agent tool, allowing that tool to analyze the commit's diff, message, and existing notes. This helps improve code quality, makes it easier to understand how a project evolves, and turns code review and learning into something more durable than a one-time commit record.

### 8. File Transfer Assistant: capture and connect materials across phone and desktop

datawork also includes practical, high-frequency tools such as the File Transfer Assistant. Users can quickly transfer, temporarily store, and capture files or materials between phone and desktop, bringing transient information into their local workspace in time.

This may look like a small capability, but it matters in real workflows. Screenshots, files, temporary materials, and mobile-captured content no longer have to remain scattered across devices; they can more easily enter later search, organization, Todo, memory, and Agent workflows.

## Performance and Engineering

- **Faster startup**: on-demand lazy loading makes the Main AI, coding area, and writing area open noticeably faster.
- **Stabler long sessions**: session data is now appended incrementally, making long sessions faster to write and more interruption-resistant.
- **Cache hits**: stable tool-definition ordering improves model prefix-cache hit rates; cache hits and context usage are shown live in the UI.
- **Quieter logs**: a tiered logging rework keeps routine runs quiet and expands call chains only when diagnosing; keys and full request content are never logged.
- **Unified retry**: network flakiness is retried by exception type (higher limits for connection errors and 5xx, more conservative for timeouts), with exponential backoff and immediate cancellation.
- **Data stability**: all databases use short connections with thread isolation and stay self-contained in a single file, so cloud-synced folders do not cause data loss.

## License

datawork is currently **proprietary software**, not an open-source project, and its source code is not publicly available. The Windows desktop application is available for download and supports **Windows 10 and above** — it can be installed and used directly. This is the only product form currently released to the public. For distribution authorization, commercial use, or other external collaboration, please contact the author.

## Tech Stack

- **Desktop**: Python, Tkinter
- **Web**: FastAPI / Uvicorn / Jinja2
- **AI Access**: protocol abstraction layer — OpenAI-compatible / Responses / Anthropic / Gemini protocol families; user-registerable models and providers
- **Agent Protocol**: ACP (Agent Client Protocol)
- **Tool Protocol**: MCP (Model Context Protocol)
- **Vector Search**: Embedding + Vector Database (Lab module)
- **Storage**: SQLite + local files (memory / todos / sessions / config / review notes)
- **Observability**: AI call ledger (dedicated database + data analysis page)
- **VCS**: Git (local backup + remote push + code-study chat persisted via git notes)

## Contact

**Author**: jk.zhou — Focused on Agent System Development & Data Engineering  
**Email**: 1406584456@qq.com | **Website**: [publish.obsidian.md/xm](https://publish.obsidian.md/xm)

---

<div align="center">

**© 2024-2026 jk.zhou. All rights reserved.**

</div>
