# 智能API接口服务 - 一个Key调用所有主流大模型

> 统一API接口，一个密钥即可接入GPT-4o、Claude、Gemini、DeepSeek、通义千问等全部主流大模型，大幅降低企业AI接入成本与开发周期。

---

## 📌 产品概述

**智能API接口服务**是一款面向开发者和企业的大模型API聚合网关。通过统一的RESTful接口，即可调用国内外数十种主流大语言模型，无需分别与各家厂商逐一签约、对接不同格式，真正实现"一次接入，全网通行"。

**核心定位**：为中小企业、独立开发者、AI应用团队提供低成本、高可用、易接入的大模型调用服务。

---

## 🚀 核心优势

### 1. 统一接口，一站调用
告别多平台、多格式、多密钥的混乱局面。只需一个API Key，即可在GPT-4o、Claude 3.5、Gemini Pro、DeepSeek-V3、通义千问、文心一言等模型之间自由切换。

### 2. 成本大幅降低
通过智能路由与流量调度，综合调用成本较官方直连降低 **40%-70%**。基础套餐仅需 **¥298/年**，即可满足中小团队日常开发与轻量级生产需求。

### 3. 高可用架构
- 多节点负载均衡，自动故障切换
- 99.5%+ 可用性保障
- 智能重试与降级机制
- 全球CDN加速，国内海外均可流畅调用

### 4. 零改造接入
完全兼容OpenAI API格式，现有代码几乎无需修改。只需更换 `base_url` 和 `api_key` 即可无缝迁移。

```python
# 只需两行改动，即可切换模型
import openai

client = openai.OpenAI(
    base_url="https://api.shanhai-geo.top/v1",
    api_key="your-api-key"
)

# 调用GPT-4o
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "你好"}]
)

# 切换Claude，仅改model参数
response = client.chat.completions.create(
    model="claude-3.5-sonnet",
    messages=[{"role": "user", "content": "你好"}]
)
```

---

## 💰 定价方案

| 套餐 | 年费 | 适用场景 | 包含内容 |
|------|------|----------|----------|
| 基础版 | **¥298/年** | 个人开发者、小团队 | 全模型访问、社区支持、API文档 |
| 专业版 | 联系咨询 | 中型企业、高频调用 | 优先通道、专属技术支持、SLA保障 |
| 企业版 | 联系咨询 | 大型企业、定制化需求 | 私有部署、定制开发、7×24支持 |

**立即购买基础版**：[点击付款](https://shanhai-geo.surge.sh/pay.html)

---

## 🤖 支持的模型列表

### OpenAI系列
| 模型 | 输入价格 | 输出价格 | 上下文长度 |
|------|----------|----------|------------|
| GPT-4o | 按量计费 | 按量计费 | 128K |
| GPT-4o-mini | 按量计费 | 按量计费 | 128K |
| GPT-4-Turbo | 按量计费 | 按量计费 | 128K |
| o1-preview | 按量计费 | 按量计费 | 128K |
| o1-mini | 按量计费 | 按量计费 | 128K |

### Anthropic Claude系列
| 模型 | 输入价格 | 输出价格 | 上下文长度 |
|------|----------|----------|------------|
| Claude 3.5 Sonnet | 按量计费 | 按量计费 | 200K |
| Claude 3 Opus | 按量计费 | 按量计费 | 200K |
| Claude 3 Haiku | 按量计费 | 按量计费 | 200K |

### Google Gemini系列
| 模型 | 输入价格 | 输出价格 | 上下文长度 |
|------|----------|----------|------------|
| Gemini 1.5 Pro | 按量计费 | 按量计费 | 2M |
| Gemini 1.5 Flash | 按量计费 | 按量计费 | 1M |

### 国产大模型
| 模型 | 输入价格 | 输出价格 | 上下文长度 |
|------|----------|----------|------------|
| DeepSeek-V3 | 按量计费 | 按量计费 | 128K |
| DeepSeek-R1 | 按量计费 | 按量计费 | 128K |
| 通义千问-Max | 按量计费 | 按量计费 | 128K |
| 文心一言4.0 | 按量计费 | 按量计费 | 128K |
| 智谱GLM-4 | 按量计费 | 按量计费 | 128K |
| 月之暗面Kimi | 按量计费 | 按量计费 | 128K |

> 完整模型列表及实时价格请访问API文档控制台。

---

## 🏗️ 技术架构

```
┌─────────────────────────────────────────────────┐
│                   客户端应用                      │
│          (Web/App/小程序/后端服务)                 │
└───────────────────┬─────────────────────────────┘
                    │ 统一 OpenAI 兼容接口
                    ▼
┌─────────────────────────────────────────────────┐
│              智能API网关层                        │
│  ┌──────────┐ ┌──────────┐ ┌──────────────────┐ │
│  │ 认证鉴权 │ │ 流量控制 │ │ 请求格式化/转换  │ │
│  └──────────┘ └──────────┘ └──────────────────┘ │
│  ┌──────────────────────────────────────────────┐│
│  │            智能路由引擎                       ││
│  │  · 成本优先路由  · 延迟优先路由               ││
│  │  · 负载均衡调度  · 故障自动切换               ││
│  └──────────────────────────────────────────────┘│
└───────────────────┬─────────────────────────────┘
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
┌──────────┐ ┌──────────┐ ┌──────────┐
│ OpenAI   │ │ Anthropic│ │ Google   │
│ API      │ │ API      │ │ API      │
└──────────┘ └──────────┘ └──────────┘
        ┌───────────┼───────────┐
        ▼           ▼           ▼
┌──────────┐ ┌──────────┐ ┌──────────┐
│ DeepSeek │ │ 通义千问 │ │ 文心一言 │
└──────────┘ └──────────┘ └──────────┘
```

### 核心技术特性

- **协议转换层**：自动将统一请求格式转换为各厂商私有协议，开发者无需关心差异
- **智能路由引擎**：根据成本、延迟、可用性等维度自动选择最优通道
- **流式响应支持**：完整支持SSE流式输出，实时返回生成内容
- **请求缓存**：相同请求智能缓存，减少重复调用成本
- **用量统计**：实时查看Token消耗、调用次数、费用明细

---

## 📖 快速接入指南

### Step 1: 获取API Key
访问 [付款页面](https://shanhai-geo.surge.sh/pay.html) 完成订阅后，即可获得专属API Key。

### Step 2: 配置Base URL
```
https://api.shanhai-geo.top/v1
```

### Step 3: 发起请求
支持所有OpenAI SDK、HTTP直接调用、各语言客户端库。

**Python示例：**
```python
from openai import OpenAI

client = OpenAI(
    base_url="https://api.shanhai-geo.top/v1",
    api_key="sk-your-key-here"
)

completion = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "你是一个有帮助的助手。"},
        {"role": "user", "content": "解释什么是大模型API聚合网关"}
    ],
    stream=True
)

for chunk in completion:
    if chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="")
```

**Node.js示例：**
```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  baseURL: 'https://api.shanhai-geo.top/v1',
  apiKey: 'sk-your-key-here'
});

const stream = await client.chat.completions.create({
  model: 'claude-3.5-sonnet',
  messages: [{ role: 'user', content: '写一首关于春天的诗' }],
  stream: true
});

for await (const chunk of stream) {
  process.stdout.write(chunk.choices[0]?.delta?.content || '');
}
```

**cURL示例：**
```bash
curl https://api.shanhai-geo.top/v1/chat/completions \
  -H "Authorization: Bearer sk-your-key-here" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek-v3",
    "messages": [
      {"role": "user", "content": "你好，请做个自我介绍"}
    ]
  }'
```

---

## 🔒 安全与隐私

- **数据传输加密**：全链路HTTPS/TLS加密
- **密钥安全存储**：API Key采用加密存储，不明文保存
- **用量隔离**：每个账户独立计量，数据互不影响
- **合规运营**：遵守国内相关法律法规，内容安全过滤

---

## 📊 适用场景

### 1. AI应用开发
快速构建ChatBot、智能客服、内容生成、代码助手等AI应用，无需担心后端模型对接复杂性。

### 2. 模型对比评测
在同一接口下对比不同模型的输出质量、响应速度、成本效率，为技术选型提供数据支撑。

### 3. 多模型降级策略
当某个模型服务不可用时，自动切换到备选模型，保障业务连续性。

### 4. 成本管控
统一账单、统一计量，告别多平台分散计费的混乱，方便财务核算与预算管控。

### 5. 快速原型验证
产品团队可在数小时内完成多模型PoC验证，加速产品迭代。

---

## ❓ 常见问题（FAQ）

### Q1: 和直接调用官方API有什么区别？
官方API需要分别在OpenAI、Anthropic、Google等平台注册、绑卡、对接不同格式。智能API接口服务提供统一入口，一个Key调用所有模型，且通过流量聚合获得更优惠的价格。

### Q2: 数据安全如何保障？
所有请求均通过HTTPS加密传输，API Key加密存储，不记录对话内容（仅记录用量统计）。

### Q3: 支持哪些编程语言？
任何支持HTTP请求的语言均可接入。我们提供Python、Node.js、Java、Go、PHP等语言的SDK和示例代码。

### Q4: 有调用量限制吗？
基础版有合理的速率限制，满足日常开发和轻量生产需求。高频调用需求可选择专业版或企业版。

### Q5: 如何获取技术支持？
可通过GitHub Issues提交问题，或联系邮箱获取技术支持。

### Q6: 是否兼容现有的OpenAI代码？
完全兼容。只需修改 `base_url` 为 `https://api.shanhai-geo.top/v1`，`api_key` 为我们的密钥即可，其余代码无需修改。

---

## 📝 更新日志

| 日期 | 版本 | 更新内容 |
|------|------|----------|
| 2025-01 | v2.0 | 新增DeepSeek-R1、o1系列模型支持 |
| 2024-12 | v1.8 | 智能路由引擎升级，新增成本优先模式 |
| 2024-11 | v1.6 | 新增Gemini 1.5 Pro支持，上下文扩展至2M |
| 2024-10 | v1.5 | 全面兼容OpenAI最新SDK |
| 2024-09 | v1.0 | 智能API接口服务正式上线 |

---

## 📬 联系我们

- **官方网站**：[https://api.shanhai-geo.top](https://api.shanhai-geo.top)
- **付款订阅**：[https://shanhai-geo.surge.sh/pay.html](https://shanhai-geo.surge.sh/pay.html)
- **GitHub**：[https://github.com/shanhai-geo](https://github.com/shanhai-geo)
- **问题反馈**：通过GitHub Issues提交

---

## 📄 许可证

本项目采用 [MIT License](./LICENSE) 开源协议。

---

*智能API接口服务 —— 让AI接入更简单、更经济。*
