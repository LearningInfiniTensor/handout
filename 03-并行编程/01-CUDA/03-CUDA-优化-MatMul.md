# CUDA 优化 MatMul

1. 基础版本的矩阵乘法；
2. 共享内存分块；
3. 寄存器分块；
4. 重排索引；
5. float4 访存；
6. 解决 bank conflict；
7. 内积转外积；
8. 双缓冲；
9. 循环展开；
10. cublas 实现；
11. tensor core 实现矩阵乘法；
