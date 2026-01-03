---
title: "Binder原理"
weight: 10
bookCollapseSection: true
bookFlatSection: false
bookHidden: false
bookComments: true
bookSearchExclude: false
---

## Binder系列：Android进程通信的核心机制


Binder是Android系统中最核心的进程间通信（IPC）框架。整个Android的应用组件模型（四大组件）与系统服务架构都构建在Binder之上。

本系列将系统剖析Binder的设计与实现，重点关注以下层面：

1. **设计动机** 

为什么Android需要自建Binder？传统IPC（管道、Socket、共享内存）在效率、安全性或易用性上无法满足移动系统高频率、结构化、受管控的跨进程通信需求。

2. 核心模型

  - 面向对象：将IPC抽象为对象的方法调用（代理模式）。

  - 一次拷贝：通过内存映射（mmap）实现仅需一次数据拷贝的高效传输。

  - 内核驱动：作为唯一的数据中转与调度中心，负责线程管理、引用计数和安全管理。

3. **关键实现**

  - 驱动层：binder_thread、binder_node、binder_ref等核心数据结构与事务流。

  - Native层：IBinder、BBinder、BpBinder构成的C++对象模型。

  - Java层：Binder、BinderProxy、AIDL等对上的接口暴露。

4. **高级话题**

  - 死亡通知机制

  - 同步/异步调用与Binder线程池管理

  - 权限校验（UID/PID）如何嵌入通信流程

本系列将从驱动出发，逐层向上解析，最终形成一个从内核到应用、从原理到实践的完整知识图景。

旨在构建一个完整、深入且连贯的Binder知识体系。我们将避免陷入枯燥的代码罗列，力求在清晰的脉络中阐释原理，在关键的节点上深挖细节。
