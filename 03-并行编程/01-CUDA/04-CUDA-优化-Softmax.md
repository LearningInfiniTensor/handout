# CUDA 优化 Softmax

## 一维softmax

> - 为了避免数值溢出，每个元素需要减去该向量最大值；
> - softmax的核心在于两次reduce操作；

---

> - 先做max规约再做sum规约，然后做指数变换，这种做法造成两次重复读取数据；
> - 同时做max和sum规约可以提高访存效率；

## 高维向量softmax

1. 操作维度axis和其他维度把数据重排为一个二维矩阵，变换过程可视为针对二维矩阵的每一行做softmax；
2. blockReduce的核心在于每个线程块处理一行数据；
3. warpReduce的核心在于线程块内每个warp处理一行数据；
4. cudnn库函数只能针对固定场景做softmax，应用范围极其有限；
