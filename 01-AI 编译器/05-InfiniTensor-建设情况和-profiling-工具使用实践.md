# InfiniTensor 建设情况和 profiling 工具使用实践

## InfiniTensor 整体建设

使用 c++ 开发的AI编译器项目，接受加载 ONNX 表示的模型执行推理，支持多种硬件加速，整体分为图层、算子层和运行时层。

### mlir 接入

开发仓库及分支：[https://github.com/bitzyz/Infini-mlir](https://github.com/bitzyz/Infini-mlir)

目前 mlir 作为 InfiniTensor 前端的一部分存在，其中完成了将 InfiniTensor 已支持的 onnx 格式的 resnet 模型导入为 mlir 格式的工作，并进行了形状推导和一部分的图优化功能。

### 统一算子库接入

算子库仓库及分支：https://github.com/PanZezhong1725/operators/tree/dev

统一算子库定义了一套算子的接口和使用流程，将硬件相关的信息在内部进行了封装使得用户无需考虑硬件算子库使用上的差异，而只需要关注统一算子库的通用接口即可。通过引入统一算子库，对 InfiniTensor 的算子层进行重构，InfiniTensor 重构分支名为 refactor_kernels。

## 性能分析实践

算子级性能分析：通常只执行单算子的计算，主要目的是判断算子的实现是否足够优，以及发现可能存在的优化空间（常用工具如 NVIDIA Nsight Compute）。

端到端性能分析：使用框架推理模型，并且对整体推理过程进行 profile，目的是为了发现框架存在的优化点，优化模型推理的整体性能。（常用工具如 NVIDIA Nsight Sytems）。
