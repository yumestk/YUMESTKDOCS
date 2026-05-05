shift + f6给idea类改名字

MCP本质就是工具调用,只是我们通过MCP协议获取到了有哪些工具可以调用

CoT思维链,Chain of Thought
ReAct:Reasoning Act


Flux响应式编程,就是异步通知效果,不用一直卡着,你可以去干别的事,然后处理完给你一个信息,再回来处理

> [!NOTE]
> 定义：SSE = Server-Sent Events，基于 HTTP 单向长连接，只能服务端→客户端推流。
> 作用：实现 AI 大模型 / Agent流式逐字输出，打字机实时效果。
> 标识：响应头 Content-Type: text/event-stream，Spring 对应 MediaType.TEXT_EVENT_STREAM_VALUE。
> 和 WebSocket 区别：SSE单向、简单、浏览器原生支持；WebSocket 双向通信，适合聊天实时互动。
> Spring 三种 SSE 写法区别
> Flux<String>：WebFlux 最简，自动封装 SSE 格式，AI 流式首选；
> Flux<ServerSentEvent<String>>：可自定义事件名、消息 ID、重连时间，功能最全；
> SseEmitter：传统 Servlet/MVC 用，手动控制发流、结束、异常，代码繁琐。
> AI Agent 场景：用 SSE 实时推送思考过程、工具调用、最终回答，前端流式展示。

CompletableFuture = Java 异步工具
作用：慢任务后台跑，不卡主线程