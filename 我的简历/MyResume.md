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

- 项目引入多级缓存、分布式限流、异步处理、重试机制等方案，保障系统高并发下的性能与稳定性
- 基于时间游标实现分页对话历史查询，规避传统深分页性能瓶颈，配合复合索引将查询性能优化 3 倍
- 整合 Selenium 与 WebDriverManager 实现自动化网页截图，通过压缩算法减少 70% 存储空间占用
- 基于 LangGraph4j 编排多节点自动化工作流，将素材搜集、代码生成、质量校验、项目构建流程化、标准化
- 通过 AI 自主规划图片搜集任务，基于 CompletableFuture + 自定义线程池并发执行，任务整体耗时缩短 300%
- 支持原生站点、Vue 工程等多类型网站生成模式，运用门面模式统一 AI 调用入口，策略模式+模板方法模式适配多类代码解析与存储逻辑，大幅提升业务可扩展性