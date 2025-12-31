
使用Perfetto命令方式
=====

### 示例命令

```shell
adb shell perfetto -o /data/misc/perfetto-traces/trace_file.perfetto-trace1 -t 10s  am wm gfx view ss
```

其中 `-t` 指定时间，可以使用 `--config [path(/data/misc/perfetto-configs/)]` 制定配置文件路径， `-b 32mb` 增加缓存大小。


### 支持的atrace类别标签列表

- 系统核心

> sched    - CPU 调度器（任务切换、唤醒）
freq     - CPU 频率变化
idle     - CPU 空闲状态
disk     - 磁盘 I/O
load     - 系统负载
sync     - 文件同步
workq    - 工作队列
memreclaim - 内存回收

- 内存相关

> mmc      - eMMC 存储操作
memtrack - 内存追踪
memory   - 内存管理
pagecache - 页面缓存
vmscan   - 虚拟内存扫描

- 硬件相关

> regulators - 电压调节器
binder_driver - Binder 驱动
binder_lock - Binder 锁
irq       - 中断处理
i2c       - I2C 总线
power     - 电源管理
thermal   - 温度管理

- 显示和图形

> gfx       - 图形系统（包含 HWUI 和 SurfaceFlinger）
hwui      - 硬件加速 UI 渲染
sf        - SurfaceFlinger（合成器）
rs        - RenderScript

- 应用框架

> am        - Activity Manager（活动生命周期）
wm        - Window Manager（窗口管理）
view      - View 系统（测量、布局、绘制）
app       - 应用程序事件
input     - 输入事件（触摸、按键）
database  - 数据库操作
network   - 网络操作
webview   - WebView 组件

- 多媒体

> audio     - 音频系统
video     - 视频编解码
camera    - 相机
hal       - 硬件抽象层

- 特定服务

> ss        - System Server（系统服务核心）
res       - 资源管理
dalvik    - Dalvik 虚拟机（ART）
dex2oat   - 应用编译
pdx       - Parcel Delivery System
rro       - 运行时资源覆盖

- 性能分析

> benchmark - 基准测试
perfetto  - Perfetto 自身
adb       - ADB 命令
systrace  - Systrace 兼容
_以下需要 root 权限_
binder    - Binder 事务（更详细）
binder_exception - Binder 异常
aidl      - AIDL 调用

- 厂商特定

> gms       - Google 移动服务
gsf       - Google 服务框架
wm_shell  - 窗口管理器 Shell（Android 10+）
transactions - SurfaceFlinger 事务

### 常用组合示例

1. 全面系统分析

```bash
adb shell perfetto -o /data/misc/perfetto-traces/trace.perfetto-trace \
  -t 10s \
  sched freq idle disk am wm gfx view ss input
```

2. 性能问题分析

```bash 
adb shell perfetto -o /data/misc/perfetto-traces/trace.perfetto-trace \
  -t 10s \
  sched gfx view wm am ss memory
```

3. 应用启动分析

```bash
adb shell perfetto -o /data/misc/perfetto-traces/trace.perfetto-trace \
  -t 5s \
  am wm view gfx input
```

4. 内存问题分析

```bash
adb shell perfetto -o /data/misc/perfetto-traces/trace.perfetto-trace \
  -t 10s \
  memory mmc disk sched
```

### 查看设备支持的所有标签

```bash
# 查看所有可用的 atrace 类别
adb shell atrace --list_categories

# 或者使用 perfetto 查看
adb shell perfetto --query-raw
```

### 说明

1. 标签分组

一些标签是分组的，例如：

- gfx 包含：hwui（应用渲染）、sf（SurfaceFlinger）
- view 包含：viewdraw、viewmeasure、viewlayout
- wm 包含：窗口动画、状态栏、导航栏

2. 使用限制

某些标签需要 root 权限

```bash
adb root
adb shell perfetto ... binder binder_exception aidl

# 某些标签需要开发人员选项启用
# "启用跟踪" 或 "启用 Perfetto 追踪"
```