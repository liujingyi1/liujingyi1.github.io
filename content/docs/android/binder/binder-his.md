---
title: "Binder 驱动"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
# bookHref: ''
# bookIcon: ''
---

Binder 被正式合入标准 Linux 内核主线（mainline）的时间点是 2017年9月3日，随 Linux 内核 4.14 版本 的合并窗口引入。
最初路径是放在drivers/staging/android/目录下，现在在任何 Linux 4.14 及以上版本 的官方内核源码中，都能在 drivers/android/（后期从 staging 目录移出）找到 Binder 驱动的源代码，可以通过配置选项 `CONFIG_ANDROID_BINDER_IPC` 来启用它。这也意味着Android 可以基于更接近纯净版的标准 Linux 内核运行，大大减少了维护成本和内核碎片化。是两大开源项目融合的关键一步。

然而在Binder合入Linux内核主线之前，经历一个近十年的"Google申请合入Linux内核，然后被Linux社区拒绝"的这样一个反复的过程，而Binder被Linux内核主线拒绝合入，根源在于两者在设计哲学、安全模型、架构理念等多方面的深刻冲突。


### 1. 设计哲学上的冲突

Binder是为移动设备优化的专用IPC，其在设计上追求的是“做一件事，做到极致”。而Linux 主流哲学是“机制与策略分离”，
提供基础原语，让用户空间决定策略。

除此还有Binder深度耦合Android框架,假设上层是Android框架,Linux内核要求保持内核简洁、通用，不假设任何特定用户空间。

Linux 内核维护者（特别是 Greg Kroah-Hartman、Arnd Bergmann 等）的观点：

> “内核应该提供基础构建块，而不是完整的解决方案。Binder 是一个完整的 RPC 系统，包含了太多策略决策。”

### 2. 安全模型冲突：能力 vs 传统权限

Binder 的安全模型：基于能力的细粒度控制

```c
// Binder 的安全检查（简化）
struct binder_transaction_data {
    uid_t sender_euid;      // 发送者UID
    pid_t sender_pid;       // 发送者PID
    // 额外的安全上下文
};
// 可以基于服务接口、方法名进行权限控制
```

Linux 传统安全模型：
- 基于 UID/GID 的 DAC（自主访问控制）
- 后来加入 capabilities（能力机制）
- SELinux/AppArmor 等 MAC（强制访问控制）

冲突点：Binder 在 IPC 层面内建了复杂的安全策略，这被视作“策略”而非“机制”。

### 3. 架构冲突：面向对象 vs 过程式

Binder 的面向对象设计
```text
进程A                进程B
  |                    |
  |-- 获取服务引用 --->|
  |                    |
  |-- 调用方法 ------->|
  |    (参数打包)      |
  |<-- 返回结果 -------|
```

Linux 传统 IPC 设计

```text
进程A                进程B
  |                    |
  |-- 管道/消息队列 -->|
  |-- 共享内存 ------->|
  |-- 信号量同步 ----->|
```

内核维护者的批评：

> “Binder 将面向对象的概念（对象引用、方法调用）带入内核，这与内核的 C 语言、过程式风格格格不入。”

