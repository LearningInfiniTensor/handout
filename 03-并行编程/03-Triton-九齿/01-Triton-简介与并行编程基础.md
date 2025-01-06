# Triton 简介与并行编程基础

## 什么是 [Triton](https://triton-lang.org/)？

* 一门并行编程语言及其编译器；
* 专注于高效地实现高性能计算内核；
* 编程环境基于 Python。

## 串行编程与并行编程

* 串行：按顺序执行
* 并行：同时执行

## 实际上的并行编程更为复杂

### 使用 CUDA 时所需要进行的考虑

* 内存合并（memory coalescing）

* 共享内存管理（shared memory management）

* 流式多处理器内部的调度（scheduling within SMs）

* 流式多处理器之间的调度（scheduling across SMs）

### 使用 Triton 时所需要进行的考虑

* ~~内存合并（memory coalescing）~~

* ~~共享内存管理（shared memory management）~~

* ~~流式多处理器内部的调度（scheduling within SMs）~~

* 流式多处理器之间的调度（scheduling across SMs）

## 使用 Triton 实现向量加法

请看 Triton 官方网站中的[向量加法](https://triton-lang.org/main/getting-started/tutorials/01-vector-add.html)教程。

## Triton 的 Python API

* [`triton.language.program_id`](https://triton-lang.org/main/python-api/generated/triton.language.program_id.html#triton.language.program_id)
* [`triton.language.arange`](https://triton-lang.org/main/python-api/generated/triton.language.arange.html#triton.language.arange)
* [`triton.language.load`](https://triton-lang.org/main/python-api/generated/triton.language.load.html#triton.language.load)
* [`triton.language.store`](https://triton-lang.org/main/python-api/generated/triton.language.store.html#triton.language.store)

## 使用 PyTorch 模拟 `arange` 相关计算

```python
>>> import torch
>>> x = torch.arange(4)
>>> x
tensor([0, 1, 2, 3])
>>> x + 4
tensor([4, 5, 6, 7])
>>> x + 8
tensor([ 8,  9, 10, 11])
>>> x + 12
tensor([12, 13, 14, 15])
```
