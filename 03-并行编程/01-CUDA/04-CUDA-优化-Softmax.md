# CUDA 优化 Softmax

## 一维 softmax

- 为了避免数值溢出，每个元素需要减去该向量最大值；
- softmax 的核心在于两次 reduce 操作；

---

> - 先做 max 规约再做 sum 规约，然后做指数变换，这种做法造成两次重复读取数据；
> - 同时做 max 和 sum 规约可以提高访存效率；

## 高维向量 softmax

1. 操作维度 axis 和其他维度把数据重排为一个二维矩阵，变换过程可视为针对二维矩阵的每一行做 softmax；
2. blockReduce 的核心在于每个线程块处理一行数据；
3. warpReduce 的核心在于线程块内每个 warp 处理一行数据；
4. cudnn库 函数只能针对固定场景做 softmax，应用范围极其有限；
