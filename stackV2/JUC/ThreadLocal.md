💾 一、 使用场景（挑最亮眼的 2 个说）
不用全背，面试时说出这两个最显水平：

用户身份信息/上下文透传（最常用）： 在拦截器（Interceptor）中解析 Token 得到用户信息，存入 ThreadLocal。后续的整个请求链路（Service/Mapper）可以直接获取，避免方法层层传参。

线程安全隔离（体现并发思维）： 像 SimpleDateFormat 这种非线程安全的工具类，或者数据库 Connection 会话，用 ThreadLocal 为每个线程单独复制一份，以空间换时间，免去加锁的性能损耗。

💡 进阶加分项： 顺口提一句“分布式链路追踪里的 traceId 也是这么透传的”，面试官会觉得你很有微服务经验。

⚙️ 二、 实现原理（认清这三层强弱引用关系）
面试官最看重你对底层源码的理解，回答时要像剥洋葱一样，层层递进：

第一层（Thread）： 每个线程对象内部都有一个成员变量叫 threadLocals，它的实际类型是 ThreadLocalMap。

第二层（ThreadLocalMap）： 这是一个特殊的 Map，其底层是 Entry 数组。

第三层（Entry 的关键点）： * Key 是 ThreadLocal 实例本身，而且是弱引用（WeakReference）。Value 是你真正存入的数据，它是强引用。

核心逻辑： set(V) 和 get() 的时候，都是以 this（当前 ThreadLocal 对象）作为 Key 去当前线程的 Map 里做哈希存取。

🚨 三、 内存泄漏（八股文的必杀技）
这一段是重中之重，必须连贯地把“为什么”和“怎么防”表达出来。

1. 为什么会泄漏？（两步递进法）
触发 GC 后： 由于 Entry 的 Key 是弱引用，当外部不再强引用 ThreadLocal 时，一旦发生 GC，Key 会被自动回收变成 null。

Value 成了孤儿： 此时 Key 没了，但 Value 是强引用。只要这个线程没有消亡（特别是线程池的核心线程，会反复复用，永远不死），这条引用链 Thread -> ThreadLocalMap -> Entry -> Value 就一直存在。Value 永远无法被回收，导致内存泄漏。

2. 解决方案（黄金法则）
怎么做： 用完之后，必须在 finally 块中显式调用 threadLocal.remove()。

为什么： remove() 会把当前 ThreadLocal 对应的整个 Entry 清理掉，切断强引用链，彻底避免内存泄漏。

🎯 面试官的“挖坑”反问预演
面试官： 既然弱引用会导致 Key 变成 null 进而引发内存泄漏，那为什么 JDK 源码还要把 Key 设计成弱引用？改成强引用不好吗？

你的必备标准反击：

“设计成弱引用其实是一种兜底保护机制。

如果 Key 用强引用：当程序员忘记调用 remove() 且代码里不再使用 ThreadLocal 时，Key 和 Value 就彻底都泄漏了，除非线程结束。

如果 Key 用弱引用：虽然会留下 Value 泄漏，但当 Key 变成 null 后，程序员下次调用 ThreadLocalMap 的 get()、set() 或 resize() 方法时，JDK 底层会顺便扫描并清理掉这些 Key 为 null 的 Value。

所以，弱引用是为了多一层被动清理的保障。当然，最稳妥的做法还是我们手动 remove()。”