# CUDA 入门编程

## CPU 和 GPU的对比

- CPU 控制单元强大，缓存大，ALU 少；
- GPU 控制单元简单，缓存小，ALU 多；

---

> - 异构计算：将应用程序的计算密集型部分卸载到 GPU 来提供更高的性能，而其余代码仍然在 CPU 上运行；

## CUDA 编程重要概念

1. 关键字 `__global__`；
2. 线程网格 grid_dim 和block_dim；
3. 核函数调用 `<<<...,...>>>`；
4. 全局同步 `cudaDeviceSynchronize()`；
5. 线程内同步 `__syncthreads()`；

## 异构编程模型

1. CPU 端准备数据；
2. 数据迁移到 GPU；
3. GPU 端执行计算过程；
4. 计算结果拷贝回 CPU；
5. 释放内存；

## CUDA 内存模型

- 寄存器内存（register）；
- 共享内存（share memory）；
- 全局内存（global memory）；

## 规约策略

- 交叉规约；
- 交错规约；
- shuffle warp 规约；
- blockReduce 规约；
