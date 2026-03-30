# 🛡️ Hyrule Strategic Command (海拉鲁战略指挥部) V13.7

> **“以左纳乌之名，重铸跨境电商视觉工作流。”**

Hyrule Strategic Command 是一个基于前端隔离架构的 AI 电商视觉协同工作台。它通过模拟《塞尔达传说：王国之泪》中“普尔亚平板 (Purah Pad)”的沉浸式 UI，将后端的 **大语言模型 (n8n Agent)** 与 **图像扩散模型 (KIE Node)** 完美串联，实现从“产品理解 -> 场景规划 -> 自动化排版 -> 高保真渲染”的全链路闭环。

## ✨ 核心特性 (Core Features)

* **🌍 战区本土化雷达 (Global Localization):** 内置北美、欧洲、日韩、中东等多个主流电商市场的预设指令。前端一键切换，Agent 自动根据当地文化语境和语言（如英语、日语、阿拉伯语）生成极其地道的营销文案与视觉排版方案。
* **🧠 幽灵重连与记忆重载 (Ghost Reconnection & Rehydration):** 基于 `localStorage` 打造的状态持久化系统。防呆防断网，即使在云端算图的漫长等待中关闭网页，再次打开时系统将自动读取 `Task ID` 并向 Firebase 重新挂载监听器，实现任务的无缝接驳与结果弹显。
* **🎯 局部精准微调舱 (Targeted Prompt Override):** 打破“全局重绘”的算力浪费。针对生成的 7 张分镜图（成功或失败），均可单独唤出“微调舱”，对该图的专属 Prompt 进行外科手术式修改（如修改排版位置、替换违规词），并一键触发单图重绘。
* **🔐 终端接入访问控制 (Terminal Auth Wall):** 高等级安全屏障。底层 Webhook 接口 URL 采用 `SECRET` 硬编码分离。新设备首次访问必须输入“接入密码”解除全屏封锁，验证通过后系统才会在底层动态注入通信地址。
* **🛑 物理逃生舱 (Manual Override):** 针对远端 Agent 节点可能出现的 10 分钟级超长思考或死机卡死，配备了带有“核弹密码”验证的手动切断开关，一键清理本地死锁记忆，强制退回安全大厅。
* **📦 究极手打包提取 (Batch Extract):** 集成 `JSZip` 引擎，一键将散落在各个槽位的渲染成品打包为 `.zip` 压缩包，完美绕过跨域限制 (CORS) 极速下载。
* **🎶 沉浸式听觉反馈 (Tone.js Audio):** 内置塞尔达原生 UI 音效逻辑，从按键点击、错误警告到最终的“通关胜利”，提供全方位的操作情绪价值。

## ⚙️ 系统架构 (Architecture)

本系统采用 **前端 (Vanilla JS) + 实时数据库 (Firebase) + 自动化工作流 (n8n)** 的三层分离架构：

1.  **前端 (Client):** 纯 HTML/CSS (Tailwind)/JS 驱动，零服务器部署成本。
2.  **通信层 (Middleware):** 使用 Firebase Realtime Database 作为异步任务的监听隧道。解决长耗时 AI 任务导致 HTTP 请求超时的痛点。
3.  **计算层 (Backend):** * `AGENT NODE`: 挂载 Gemini 大模型，负责读取产品信息、分析受众并生成 7 步分镜的排版神谕 (SOP)。
    * `KIE NODE`: 挂载 Nano Banana Pro 等顶级生图/排版模型，接收 SOP 和参考底图，执行图文融合与光影渲染。

## 🚀 部署指南 (Deployment)

1.  **Clone 仓库:** (私有仓库保护)
2.  **配置 Firebase:** 在 `index.html` 的 `firebaseConfig` 中填入你的项目参数。
3.  **注入私钥:** 找到代码底部的 **“底层机密常量区”**，替换你自己的 n8n Production Webhook：
    ```javascript
    const SECRET_AGENT_URL = "https://your-n8n-instance/webhook/agent";
    const SECRET_KIE_URL = "https://your-n8n-instance/webhook/kie";
    const SYSTEM_PWD = "你的接入密码";
    ```
4.  **运行:** 直接在浏览器中打开 `index.html`，输入密码，开始你的跨次元设计之旅。

---
*Created by [你的名字/代号] | Classified Internal Tool*
