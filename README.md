<div align="center">

<img src="https://github.com/jkjoker/datawork/blob/datawork/images/datawork_logo_new.png" alt="datawork" width="128" />

# datawork

**Local-First Personal AI Agent System**

*For anyone who encodes — 给每一个需要对信息进行编码的人*

<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Platform-Windows-blue?logo=windows" alt="Windows" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/Built%20with-Python-3776AB?logo=python&logoColor=white" alt="Python" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Achangelog"><img src="https://img.shields.io/badge/Version-3.8.7f11.7.4.20261006-green" alt="Version" /></a>
<a href="https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout"><img src="https://img.shields.io/badge/License-Proprietary-red" alt="License" /></a>

[官方主页](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout) · [详细介绍](https://publish.obsidian.md/xm/wiki/%F0%9F%92%8E%20%E5%85%B3%E4%BA%8E/datawork) · [下载](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout) · [更新日志](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Achangelog)

---

[English](#english) | 简体中文

</div>

## 项目简介

datawork 是一个本地优先的个人 AI Agent 系统，把资料、对话、任务、代码和工具放在同一个本地工作区，让 AI 能围绕长期上下文持续协助工作。

## 核心能力

| 模块 | 说明 |
|---|---|
| 本地优先工作区 | 工作区数据默认保存在本地，无需 datawork 账号、注册或登录。 |
| Code Agent | 面向编码、调试、文件编辑、脚本执行、代码研读和长任务推进。 |
| 通用 Agent | 面向日常对话、信息整理、写作、知识管理和跨模块任务。 |
| Workflow | 将领域内的 skill、提示词、工具和判断标准沉淀为可编辑、可维护的 Agent 运行环境。 |
| 记忆与 Todo | 多记忆库与三层 Todo 系统，用于长期保存经验、任务和项目过程。 |
| 工具与 MCP | 支持内置工具、Python 插件和标准 MCP server。 |
| 模型管理 | 支持多供应商、多协议族、自定义模型、推理深度与模型能力配置。 |
| Web Studio | 支持通过浏览器访问本地工作区，用于多端查看、对话和任务推进。 |
| AI 调用账本 | 记录模型用量、费用、耗时和来源入口。 |
| 权限与安全 | 文件白名单、工具权限审批和会话级权限模式。 |

## 界面预览

<div align="center">
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020260619221829.png" width="55%" />
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020260619222051.png" width="35%" />
</div>

## 快速开始

```text
1. 下载安装包
2. 安装并启动 datawork
3. 设置工作路径与笔记保存路径
4. 在「模型管理」中添加模型
5. 发送一条消息确认 AI 联通状态
```

当前桌面版主要面向 **Windows 10 及以上系统**构建和测试。

## 文档

- [官方主页 / 下载](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout)
- [详细介绍](https://publish.obsidian.md/xm/wiki/%F0%9F%92%8E%20%E5%85%B3%E4%BA%8E/datawork)
- [更新日志](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Achangelog)

## 许可证

datawork 当前为**专有软件**，不是开源项目，源码未对外开放。Windows 桌面应用是目前唯一对外开放的产品形态。

若有分发授权、商业使用或其他对外合作需求，请联系作者沟通。

## 联系

**作者**：jk.zhou  
**Email**：1406584456@qq.com  
**个人网站**：[publish.obsidian.md/xm](https://publish.obsidian.md/xm)

---

<a name="english"></a>

<div align="center">

# datawork

**Local-First Personal AI Agent System**

*For anyone who encodes — For everyone who needs to encode information*

</div>

## About

datawork is a local-first personal AI Agent system. It brings AI conversations, files, memory, todos, projects, scripts, plugins, and the standard MCP protocol into one local workspace.

It is designed for long-term workflows across reading, writing, coding, organizing, reviewing, and execution, with a focus on accumulating context, experience, tools, and workflows over time.

## Key Features

| Area | Description |
|---|---|
| Local-first workspace | Workspace data is stored locally by default. No datawork account, registration, or login is required. |
| Code Agent | For coding, debugging, file editing, script execution, code review, and long-running tasks. |
| General Agent | For daily chat, information organization, writing, knowledge management, and cross-module tasks. |
| Workflow | Editable Agent environments built from domain skills, prompts, tools, and criteria. |
| Memory and Todo | Multiple memory libraries and a three-level Todo system for long-term task and project records. |
| Tools and MCP | Built-in tools, Python plugins, and standard MCP servers. |
| Model management | Multiple providers, protocol families, custom models, reasoning depth, and capability configuration. |
| Web Studio | Browser access to the local workspace for multi-device conversations and task work. |
| AI call ledger | Records model usage, cost, latency, and entry point. |
| Permissions and safety | File whitelist, tool approval, and session-level permission modes. |

## Screenshots

<div align="center">
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020260619221829.png" width="55%" />
<img src="https://github.com/jkjoker/datawork/blob/datawork/images/Pasted%20image%2020260619222051.png" width="35%" />
</div>

## Quick Start

```text
1. Download the installer
2. Install and start datawork
3. Set the workspace and note paths
4. Add a model in Model Management
5. Send a message to verify AI connectivity
```

The current desktop version is built and tested mainly for **Windows 10 and later**.

## Documentation

- [Homepage / Download](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Aabout)
- [Detailed Introduction](https://publish.obsidian.md/xm/wiki/%F0%9F%92%8E%20%E5%85%B3%E4%BA%8E/datawork)
- [Changelog](https://publish.obsidian.md/xm/wiki/%E6%95%99%E7%A8%8B/datawork%EF%BC%9Achangelog)

## License

datawork is proprietary software. It is not open source, and the source code is not publicly available. The Windows desktop application is currently the only public product form.

For distribution authorization, commercial use, or other external cooperation, please contact the author.

## Contact

**Author**: jk.zhou  
**Email**: 1406584456@qq.com  
**Website**: [publish.obsidian.md/xm](https://publish.obsidian.md/xm)
