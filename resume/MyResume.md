# 彭锦宣
- 电话：19173923795
- 邮箱：2231754412@qq.com
- GitHub：https://github.com/yumestk

---

## 求职意向
Java 后端开发（具备 AI Agent 全栈开发经验）

---

## 教育经历
**湖南科技大学** | 信息安全 本科  
2024-09 ~ 2028-06  

- 英语 CET-6，具备英文技术文档阅读能力

---

## 专业技能

### 后端开发
- **编程语言**：熟练 Java 常用集合、面向对象思想，了解并发编程、JVM 底层原理
- **开发框架**：熟练 SpringBoot、Spring、SpringMVC，掌握 IoC、AOP 核心思想
- **数据库与中间件**：熟悉 MySQL 事务、索引、MVCC 机制；掌握 Redis 五大核心数据结构、分布式锁、缓存应用
- **开发运维**：熟练 Git，了解 Linux 常用命令、Docker 基础使用
- **设计模式**：熟悉门面、模板方法、工厂等常见设计模式，并在实际项目中落地优化代码架构

### AI 应用开发
- **AI 框架**：熟练 SpringAI、LangChain4j，落地过 RAG、Tool Calling、MCP 协议相关 AI 智能体项目
- **向量与检索**：掌握 Prompt 工程与调优技巧，可基于 PGvector 向量数据库搭建 RAG 知识库
- **编程工具**：熟练使用 Cursor、Claude Code、OpenCode 等 AI 编程工具提升开发效率
- **编程理念**：了解 Vibe Coding、Harness Engineering 等主流 AI 编程开发模式

---

## 项目经历

### YumeManus | 基于 RAG 与 ReAct 的情感分析分步推理智能体
项目基于 Spring AI、RAG、Tool Calling、MCP 协议开发，支持多轮对话与记忆持久化。采用 ReAct 模式，可自主调用网页搜索、资源下载、PDF 生成等工具，实现约会计划制定与文档自动输出。

- 基于 Agent Loop 实现自主多步骤任务执行，通过步骤限制、状态管理、死循环检测机制，规避智能体无限循环问题
- 参考 OpenManus 分层智能体架构（BaseAgent/ReActAgent/ToolCallAgent），提升项目可维护性与扩展性
- 自定义 VectorStore 适配 PGvector 向量数据库，实现语义相似度检索与多维度过滤，提升知识库检索精准度
- 依托 Spring AI MessageChatMemoryAdvisor、ChatMemory 实现对话上下文记忆，保证多轮对话语境连贯
- 自研基于文件系统的对话记忆方案，结合 Kryo 高性能序列化库持久化对话历史，解决服务重启后记忆丢失问题，提升系统稳定性

---

### Yume No Code | AI 零代码应用生成平台
基于 Spring Boot 3 + LangChain4j + LangGraph4j 搭建 AI 零代码应用平台。用户输入自然语言描述，AI Agent 自动完成素材搜集、代码生成、质量检查、项目构建全流程，一键生成可直接访问的 Web 应用。

- 基于时间游标实现分页对话历史查询，规避传统深分页性能瓶颈，配合复合索引将查询性能优化 3 倍
- 整合 Selenium 与 WebDriverManager 实现自动化网页截图，通过压缩算法减少 70% 存储空间占用
- 基于 LangGraph4j 编排多节点自动化工作流，将素材搜集、代码生成、质量校验、项目构建流程化、标准化
- 通过 AI 自主规划图片搜集任务，基于 CompletableFuture + 自定义线程池并发执行，任务整体耗时缩短 300%
- 支持原生站点、Vue 工程等多类型网站生成模式，运用门面模式统一 AI 调用入口，策略模式+模板方法模式适配多类代码解析与存储逻辑，大幅提升业务可扩展性

面试官您好，我叫彭锦宣，目前就读湖南科技大学信息安全本科大二。技术上以 Java 后端为基础，同时深耕 AI Agent 应用开发，熟练掌握 SpringBoot、MySQL、Redis，也会 SpringAI、LangChain4j，做过 RAG、ReAct 智能体和向量数据库落地项目。个人独立开发了两个完整项目，一个是基于 RAG 与 ReAct 的情感分析分步推理智能体，参考 OpenManus 架构实现多轮对话、工具调用和记忆持久化；另一个是 AI 零代码生成平台，参考美团 NoCode 思路，实现自然语言一键生成 Web 应用，并有可视化修改，用到多级缓存、异步并发、限流和工作流编排，也在项目中实际应用过常见设计模式优化架构。平时习惯用 AI 编程工具提效，有开源项目沉淀，学习和落地能力比较强，希望能应聘 Java 后端或 AI 应用开发实习岗位，谢谢面试官。


**你第一个项目提到参考 OpenManus 分层智能体架构，你说下你项目里拆了哪几层？每层各自负责什么职责？**
我参考 OpenManus 把它拆成了四层继承，每一层只做一件事：

  第一层 BaseAgent —— 这是最底层的抽象，只负责三件事：管理 Agent 的状态机（IDLE → Running → Finished/Error），控制执行循环的最大步数，以及自己维护一个 messageList
   做会话上下文。它不关心怎么思考、怎么执行，只定义框架。

  第二层 ReActAgent —— 继承 BaseAgent，把单步执行拆成两个模板方法：think() 和 act()。step() 的实现就是先 think 再 act，think 返回 true 才执行
  act。这层也不实现具体逻辑，只是把"思考-行动"这个模式定下来。

  第三层 ToolCallAgent —— 这层才是真正干活的地方。think() 里做了三件事：拼接 next-step 提示词、调用大模型拿到 ChatResponse、从响应里解析出模型想调哪些工具。act()
  里通过 ToolCallingManager 执行工具，把结果写回上下文，并且判断有没有调用终止工具来决定要不要结束。还有一个关键点是我禁用了 Spring AI
  内置的工具自动执行，改由应用侧显式控制，这样我能看到每一步模型选了什么工具、为什么选。

  第四层 YumeManus —— 最上层，就是一个配置好的具体实例。设了系统提示词让它知道自己是通用助手，设了 next-step 提示词引导它主动规划工具，最大步数设成 20
  防止死循环，注入工具列表和 ChatClient 就能直接用。

  这样拆的好处是我想加新 Agent 的时候不用从头写，比如要做一个只对话不调工具的 Agent，直接从 ReActAgent 继承就行，不用碰 ToolCallAgent 的逻辑。