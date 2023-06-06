# llama.cpp

纯C/C++实现的LLaMA模型推理。
cpp的主要目标是在MacBook上使用4位整数量化运算运行LLaMA模型

* 纯C/C++实现，没有其它依赖
* Apple silicon优先支持，通过ARM NEON, Accelerate和Metal框架优化
* AVX, AVX2和AVX512支持x86架构
* 混合F16 / F32精度
* 支持4位、5位和8位整数量化运算
* 支持OpenBLAS/Apple BLAS/ARM性能，Lib/ATLAS/BLIS/Intel MKL/NVHPC/ACML/SCSL/SGIMATH等更多的BLAS
* cuBLAS and CLBlast 支持

github: [https://github.com/ggerganov/llama.cpp](https://github.com/ggerganov/llama.cpp)