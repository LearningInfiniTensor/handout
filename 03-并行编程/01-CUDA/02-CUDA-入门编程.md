# CUDA 入门编程

## CPU和GPU的对比

> - CPU控制单元强大，缓存大，ALU少；
> - GPU控制单元简单，缓存小，ALU多；

---

> - 异构计算：将应用程序的计算密集型部分卸载到GPU来提供更高的性能，而其余代码仍然在CPU上运行；

## CUDA编程重要概念

1. 关键字__global__；
2. 线程网格grid_dim和block_dim；
3. 核函数调用<<<...,...>>>；
4. 全局同步cudaDeviceSynchronize()；
5. 线程内同步__syncthreads()；

## 异构编程模型

1. CPU端准备数据；
2. 数据迁移到GPU；
3. GPU端执行计算过程；
4. 计算结果拷贝回CPU；
5. 释放内存；

## CUDA内存模型

- 寄存器内存(register)；
- 共享内存(share memory)；
- 全局内存(global memory)；



## 规约策略

- 交叉规约
- 交错规约
- shuffle warp规约
- blockReduce规约

