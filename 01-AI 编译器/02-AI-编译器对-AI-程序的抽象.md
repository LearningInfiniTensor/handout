# AI 编译器对 AI 程序的抽象

## AI 程序的特征

1. 基于深度神经网络，强时序性/层序性，控制流少；
2. 操作大规模数据，以高维数组为基本数据类型；
3. 完全无副作用，仅使用函数调可表示整个过程；

---

> - 在 AI 程序中，高维数组被称为张量（Tensor）；
> - 在 AI 程序中，函数调用被称为算子（Operator）；

## 计算图

由于上述特征，AI 程序可以表示为以算子为节点，以张量为边的有向无环图（DAG）。

- 计算图本质是由函数调用组成的大型函数调用，因此具有输入输出；
- 计算图是递归的结构，即计算图的任何子图都满足计算图的定义；
- 计算图的输入输出可以视为入度或出度为零的节点，也可以视作没有源或目的的节点；
- 由于节点是算子，算子是函数调用，因此计算图中节点的入边和出边是有序的；

## InfiniTensor 和 RefactorGraph 中的计算图实现

### InfiniTensor

计算图的拓扑隐藏在对象指针指向关系中，操作复杂。

- 张量（[tensor_base.h](https://github.com/InfiniTensor/InfiniTensor/blob/master/include/core/tensor_base.h)/[tensor.h](https://github.com/InfiniTensor/InfiniTensor/blob/master/include/core/tensor.h)）；
- 算子（[operator.h](https://github.com/InfiniTensor/InfiniTensor/blob/master/include/core/operator.h)）；
- 计算图（[graph.h](https://github.com/InfiniTensor/InfiniTensor/blob/master/include/core/graph.h)）；

### RefactorGraph

计算图的拓扑和操作逻辑与张量和算子的定义解耦。

- 图拓扑类型（[container.h](https://github.com/InfiniTensor/RefactorGraph/blob/master/src/01graph_topo/include/graph_topo/container.h)）；
