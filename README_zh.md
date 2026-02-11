<div align="center">
  <img src="nanobot_logo.png" alt="nanobot" width="500">
  <h1>nanobot: 超轻量级个人AI助手</h1>
  <p>
    <a href="https://pypi.org/project/nanobot-ai/"><img src="https://img.shields.io/pypi/v/nanobot-ai" alt="PyPI"></a>
    <a href="https://pepy.tech/project/nanobot-ai"><img src="https://static.pepy.tech/badge/nanobot-ai" alt="Downloads"></a>
    <img src="https://img.shields.io/badge/python-≥3.11-blue" alt="Python">
    <img src="https://img.shields.io/badge/license-MIT-green" alt="License">
    <a href="./COMMUNICATION.md"><img src="https://img.shields.io/badge/Feishu-Group-E9DBFC?style=flat&logo=feishu&logoColor=white" alt="Feishu"></a>
    <a href="./COMMUNICATION.md"><img src="https://img.shields.io/badge/WeChat-Group-C5EAB4?style=flat&logo=wechat&logoColor=white" alt="WeChat"></a>
    <a href="https://discord.gg/MnCvHqpUGB"><img src="https://img.shields.io/badge/Discord-Community-5865F2?style=flat&logo=discord&logoColor=white" alt="Discord"></a>
  </p>
</div>

**nanobot** 是一个**超轻量级**的个人AI助手，灵感来自 [Clawdbot](https://github.com/openclaw/openclaw)

仅需 **~4,000** 行代码即可交付核心代理功能 —— 比 Clawdbot 的 43 万行代码 **小 99%**。

实时代码行数：**3,412 行**（随时运行 `bash core_agent_lines.sh` 验证）

## 新闻动态

- **2026-02-05** 新增飞书渠道、DeepSeek提供商和增强的定时任务支持！
- **2026-02-04** 发布 v0.1.3.post4，支持多提供商和Docker！查看[发布说明](https://github.com/HKUDS/nanobot/releases/tag/v0.1.3.post4)了解详情。
- **2026-02-03** 集成vLLM支持本地LLM，改进自然语言任务调度！
- **2026-02-02** nanobot正式发布！欢迎试用 nanobot！

## nanobot的核心特性：

**超轻量级**：仅约3,400行核心代理代码 —— 比Clawdbot小99%。

**研究友好**：代码简洁易读，便于理解、修改和扩展进行研究。

**极速响应**：最小化占用意味着更快的启动速度、更低的资源使用和更快的迭代。

**易于使用**：一键部署，开箱即用。

## 架构设计

<p align="center">
  <img src="nanobot_arch.png" alt="nanobot architecture" width="800">
</p>

## 功能特性

<table align="center">
  <tr align="center">
    <th><p align="center">7×24实时市场分析</p></th>
    <th><p align="center">全栈软件工程师</p></th>
    <th><p align="center">智能日程管理</p></th>
    <th><p align="center">个人知识助手</p></th>
  </tr>
  <tr>
    <td align="center"><p align="center"><img src="case/search.gif" width="180" height="400"></p></td>
    <td align="center"><p align="center"><img src="case/code.gif" width="180" height="400"></p></td>
    <td align="center"><p align="center"><img src="case/scedule.gif" width="180" height="400"></p></td>
    <td align="center"><p align="center"><img src="case/memory.gif" width="180" height="400"></p></td>
  </tr>
  <tr>
    <td align="center">发现 • 洞察 • 趋势</td>
    <td align="center">开发 • 部署 • 扩展</td>
    <td align="center">调度 • 自动化 • 组织</td>
    <td align="center">学习 • 记忆 • 推理</td>
  </tr>
</table>

## 安装

**从源码安装**（最新功能，推荐用于开发）

```bash
git clone https://github.com/HKUDS/nanobot.git
cd nanobot
pip install -e .
```

**使用 [uv](https://github.com/astral-sh/uv) 安装**（稳定、快速）

```bash
uv tool install nanobot-ai
```

**从PyPI安装**（稳定版）

```bash
pip install nanobot-ai
```

## 快速开始

> [!TIP]
> 在 `~/.nanobot/config.json` 中设置你的API密钥。
> 获取API密钥：[OpenRouter](https://openrouter.ai/keys)（LLM）· [Brave Search](https://brave.com/search/api/)（可选，用于网络搜索）
> 你也可以将模型更改为 `minimax/minimax-m2` 以降低成本。

**1. 初始化**

```bash
nanobot onboard
```

**2. 配置**（`~/.nanobot/config.json`）

```json
{
  "providers": {
    "openrouter": {
      "apiKey": "sk-or-v1-xxx"
    }
  },
  "agents": {
    "defaults": {
      "model": "anthropic/claude-opus-4-5"
    }
  },
  "tools": {
    "web": {
      "search": {
        "apiKey": "BSA-xxx"
      }
    }
  }
}
```


**3. 开始聊天**

```bash
nanobot agent -m "2+2等于几？"
```

就这样！2分钟内你就拥有了一个可用的AI助手。

## 本地模型（vLLM）

使用vLLM或任何兼容OpenAI的服务器运行你自己的本地模型。

**1. 启动vLLM服务器**

```bash
vllm serve meta-llama/Llama-3.1-8B-Instruct --port 8000
```

**2. 配置**（`~/.nanobot/config.json`）

```json
{
  "providers": {
    "vllm": {
      "apiKey": "dummy",
      "apiBase": "http://localhost:8000/v1"
    }
  },
  "agents": {
    "defaults": {
      "model": "meta-llama/Llama-3.1-8B-Instruct"
    }
  }
}
```

**3. 开始聊天**

```bash
nanobot agent -m "你好，我的本地LLM！"
```

> [!TIP]
> 对于不需要身份验证的本地服务器，`apiKey` 可以是任何非空字符串。

## 聊天应用

通过Telegram、Discord、WhatsApp或飞书与你的nanobot交流 —— 随时随地。

| 渠道 | 配置难度 |
|---------|-------|
| **Telegram** | 简单（只需token） |
| **Discord** | 简单（机器人token + intents） |
| **WhatsApp** | 中等（扫描二维码） |
| **飞书** | 中等（应用凭证） |

<details>
<summary><b>Telegram</b>（推荐）</summary>

**1. 创建机器人**
- 打开Telegram，搜索 `@BotFather`
- 发送 `/newbot`，按照提示操作
- 复制token

**2. 配置**

```json
{
  "channels": {
    "telegram": {
      "enabled": true,
      "token": "YOUR_BOT_TOKEN",
      "allowFrom": ["YOUR_USER_ID"]
    }
  }
}
```

> 从Telegram的 `@userinfobot` 获取你的用户ID。

**3. 运行**

```bash
nanobot gateway
```

</details>

<details>
<summary><b>Discord</b></summary>

**1. 创建机器人**
- 访问 https://discord.com/developers/applications
- 创建应用 → 机器人 → 添加机器人
- 复制机器人token

**2. 启用intents**
- 在机器人设置中，启用 **MESSAGE CONTENT INTENT**
- （可选）如果计划使用基于成员数据的允许列表，启用 **SERVER MEMBERS INTENT**

**3. 获取你的用户ID**
- Discord设置 → 高级 → 启用 **开发者模式**
- 右键点击你的头像 → **复制用户ID**

**4. 配置**

```json
{
  "channels": {
    "discord": {
      "enabled": true,
      "token": "YOUR_BOT_TOKEN",
      "allowFrom": ["YOUR_USER_ID"]
    }
  }
}
```

**5. 邀请机器人**
- OAuth2 → URL生成器
- 范围：`bot`
- 机器人权限：`发送消息`、`读取消息历史`
- 打开生成的邀请URL并将机器人添加到你的服务器

**6. 运行**

```bash
nanobot gateway
```

</details>

<details>
<summary><b>WhatsApp</b></summary>

需要 **Node.js ≥18**。

**1. 连接设备**

```bash
nanobot channels login
# 使用WhatsApp → 设置 → 关联设备扫描二维码
```

**2. 配置**

```json
{
  "channels": {
    "whatsapp": {
      "enabled": true,
      "allowFrom": ["+1234567890"]
    }
  }
}
```

**3. 运行**（两个终端）

```bash
# 终端1
nanobot channels login

# 终端2
nanobot gateway
```

</details>

<details>
<summary><b>飞书</b></summary>

使用 **WebSocket** 长连接 —— 无需公网IP。

```bash
pip install nanobot-ai[feishu]
```

**1. 创建飞书机器人**
- 访问[飞书开放平台](https://open.feishu.cn/app)
- 创建新应用 → 启用 **机器人** 能力
- **权限**：添加 `im:message`（发送消息）
- **事件**：添加 `im.message.receive_v1`（接收消息）
  - 选择 **长连接** 模式（需要先运行nanobot建立连接）
- 从"凭证与基础信息"获取 **App ID** 和 **App Secret**
- 发布应用

**2. 配置**

```json
{
  "channels": {
    "feishu": {
      "enabled": true,
      "appId": "cli_xxx",
      "appSecret": "xxx",
      "encryptKey": "",
      "verificationToken": "",
      "allowFrom": []
    }
  }
}
```

> 长连接模式下 `encryptKey` 和 `verificationToken` 是可选的。
> `allowFrom`：留空允许所有用户，或添加 `["ou_xxx"]` 限制访问。

**3. 运行**

```bash
nanobot gateway
```

> [!TIP]
> 飞书使用WebSocket接收消息 —— 不需要webhook或公网IP！

</details>

## 配置说明

配置文件：`~/.nanobot/config.json`

### LLM提供商

> [!NOTE]
> Groq通过Whisper提供免费语音转录。如果配置了，Telegram语音消息将自动转录。

| 提供商 | 用途 | 获取API密钥 |
|----------|---------|-------------|
| `openrouter` | LLM（推荐，访问所有模型） | [openrouter.ai](https://openrouter.ai) |
| `anthropic` | LLM（Claude直接接入） | [console.anthropic.com](https://console.anthropic.com) |
| `openai` | LLM（GPT直接接入） | [platform.openai.com](https://platform.openai.com) |
| `deepseek` | LLM（DeepSeek直接接入） | [platform.deepseek.com](https://platform.deepseek.com) |
| `groq` | LLM + **语音转录**（Whisper） | [console.groq.com](https://console.groq.com) |
| `gemini` | LLM（Gemini直接接入） | [aistudio.google.com](https://aistudio.google.com) |


<details>
<summary><b>完整配置示例</b></summary>

```json
{
  "agents": {
    "defaults": {
      "model": "anthropic/claude-opus-4-5"
    }
  },
  "providers": {
    "openrouter": {
      "apiKey": "sk-or-v1-xxx"
    },
    "groq": {
      "apiKey": "gsk_xxx"
    }
  },
  "channels": {
    "telegram": {
      "enabled": true,
      "token": "123456:ABC...",
      "allowFrom": ["123456789"]
    },
    "discord": {
      "enabled": false,
      "token": "YOUR_DISCORD_BOT_TOKEN",
      "allowFrom": ["YOUR_USER_ID"]
    },
    "whatsapp": {
      "enabled": false
    },
    "feishu": {
      "enabled": false,
      "appId": "cli_xxx",
      "appSecret": "xxx",
      "encryptKey": "",
      "verificationToken": "",
      "allowFrom": []
    }
  },
  "tools": {
    "web": {
      "search": {
        "apiKey": "BSA..."
      }
    }
  }
}
```

</details>

## 命令行参考

| 命令 | 说明 |
|---------|-------------|
| `nanobot onboard` | 初始化配置和工作区 |
| `nanobot agent -m "..."` | 与代理聊天 |
| `nanobot agent` | 交互式聊天模式 |
| `nanobot gateway` | 启动网关 |
| `nanobot status` | 显示状态 |
| `nanobot channels login` | 连接WhatsApp（扫描二维码） |
| `nanobot channels status` | 显示渠道状态 |

<details>
<summary><b>定时任务（Cron）</b></summary>

```bash
# 添加任务
nanobot cron add --name "每日任务" --message "早上好！" --cron "0 9 * * *"
nanobot cron add --name "每小时" --message "检查状态" --every 3600

# 列出任务
nanobot cron list

# 删除任务
nanobot cron remove <job_id>
```

</details>

## Docker

> [!TIP]
> `-v ~/.nanobot:/root/.nanobot` 参数将本地配置目录挂载到容器中，使你的配置和工作区在容器重启后保持不变。

在容器中构建和运行nanobot：

```bash
# 构建镜像
docker build -t nanobot .

# 初始化配置（仅第一次）
docker run -v ~/.nanobot:/root/.nanobot --rm nanobot onboard

# 在主机上编辑配置以添加API密钥
vim ~/.nanobot/config.json

# 运行网关（连接到Telegram/WhatsApp）
docker run -v ~/.nanobot:/root/.nanobot -p 18790:18790 nanobot gateway

# 或运行单个命令
docker run -v ~/.nanobot:/root/.nanobot --rm nanobot agent -m "你好！"
docker run -v ~/.nanobot:/root/.nanobot --rm nanobot status
```

## 项目结构

```
nanobot/
├── agent/          # 核心代理逻辑
│   ├── loop.py     #    代理循环（LLM ↔ 工具执行）
│   ├── context.py  #    提示词构建器
│   ├── memory.py   #    持久化记忆
│   ├── skills.py   #    技能加载器
│   ├── subagent.py #    后台任务执行
│   └── tools/      #    内置工具（包括spawn）
├── skills/         # 内置技能（github、weather、tmux...）
├── channels/       # WhatsApp集成
├── bus/            # 消息路由
├── cron/           # 定时任务
├── heartbeat/      # 主动唤醒
├── providers/      # LLM提供商（OpenRouter等）
├── session/        # 对话会话
├── config/         # 配置管理
└── cli/            # 命令行
```

## 贡献与路线图

欢迎提交PR！代码库故意保持小巧和易读。

**路线图** —— 选择一个项目并[提交PR](https://github.com/HKUDS/nanobot/pulls)！

- [x] **语音转录** — 支持Groq Whisper（Issue #13）
- [ ] **多模态** — 看见和听见（图像、语音、视频）
- [ ] **长期记忆** — 永不忘记重要上下文
- [ ] **更好的推理** — 多步规划和反思
- [ ] **更多集成** — Discord、Slack、邮件、日历
- [ ] **自我改进** — 从反馈和错误中学习

### 贡献者

<a href="https://github.com/HKUDS/nanobot/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=HKUDS/nanobot&max=100&columns=12" />
</a>


## Star历史

<div align="center">
  <a href="https://star-history.com/#HKUDS/nanobot&Date">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=HKUDS/nanobot&type=Date&theme=dark" />
      <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=HKUDS/nanobot&type=Date" />
      <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=HKUDS/nanobot&type=Date" style="border-radius: 15px; box-shadow: 0 0 30px rgba(0, 217, 255, 0.3);" />
    </picture>
  </a>
</div>

<p align="center">
  <em> 感谢访问 nanobot！</em><br><br>
  <img src="https://visitor-badge.laobi.icu/badge?page_id=HKUDS.nanobot&style=for-the-badge&color=00d4ff" alt="Views">
</p>


<p align="center">
  <sub>nanobot 仅供教育、研究和技术交流目的使用</sub>
</p>
