# OpenCL 概述及运行时

## OpenCL 发展史

2008 年由苹果公司提出，并移交给 Khronos Group，以开放规范方式推进。目前最新大版本为 3.0。

## OpenCL 概述

OpenCL，全称为 Open Computing Language 开放计算语言，是一种开放、无版税、适用于跨平台并行编程的异构计算编程模型。

[规范文档](https://registry.khronos.org/OpenCL/specs/3.0-unified/html/OpenCL_API.html)可任意使用。

## 异构计算架构

### 平台

- 定义：一个主机连接到一个或多个 OpenCL 设备；
- 平台层的必要性来自 OpenCL 的异构通用性；
- CUDA 无对应物；

### 设备

- 定义：指定和查询 OpenCL 设备；

### 上下文

- 定义：设备资源分配和交互的空间；

### 存储

- 异构计算设备通常需要自己的存储器（至少是逻辑上的存储器）以达到较好的性能；
- OpenCL 2.0 新增共享虚拟存储（SVM）抽象；
- 共享虚拟存储的操作除分配外全异步；

### 队列

- 定义：异构计算设备的工作流；
- 主处理器与协处理器的交互通过与任务队列的交互完成，主要操作是排队和同步；

### 事件

- 在不同步的情况下获取队列状态信息；
- 可实现多个任务队列之间的同步；
- 本次训练营用不到；

### 核函数

- 使用 [OpenCL C](https://registry.khronos.org/OpenCL/specs/3.0-unified/html/OpenCL_C.html) 编程；
- 在主机完成源码编译，并发射（Launch）到任务队列上执行；
