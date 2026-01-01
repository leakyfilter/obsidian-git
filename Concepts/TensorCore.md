---
title: TensorCore
tags: [concept, gpu, hardware, ai, key-concept]
created: 2024-12-29
---

# TensorCore

## Definition

TensorCore is specialized hardware within Nvidia GPUs designed to accelerate matrix multiplication operations, introduced in Volta (2017) and progressively scaled through Ampere, Hopper, and Blackwell generations.

## Explanation

TensorCores represent Nvidia's shift from pure SIMT (Single Instruction Multiple Thread) architecture toward specialized accelerators. They perform large-scale matrix multiplications more efficiently than traditional CUDA Cores by:

- **Increasing compute-to-memory ratio**: Larger matrices mean more computation per memory access
- **Supporting lower precision**: FP16, BFP16, INT8, FP8, FP4 for higher throughput
- **Scaling progressively**: 16x16 (Volta) → 256x128 (Blackwell) → predicted 256xNx256 (Rubin)

## Evolution Timeline

- **Volta (SM70)**: First generation, 16x16 matrices, reused CUDA Core registers
- **Ampere**: Larger scale, introduced cp.async to bypass L1 and reduce register pressure
- **Hopper**: Introduced TMA (Tensor Memory Accelerator), operands directly in SMEM, but Accumulator still in RMEM (WGMMA was a "temporary solution")
- **Blackwell**: [[TMEM]] fully separates TensorCore from CUDA Core, fully asynchronous via [[MBarrier]]
- **Rubin (predicted)**: 4-CTA MMA, further doubling M dimension

## Trade-offs

The aggressive scaling of TensorCore compute power created bottlenecks elsewhere:

- **B200 SFU problem**: Softmax operations in Attention couldn't keep up (fixed in B300)
- **Memory bandwidth**: Increasingly difficult to feed TensorCores with data
- **Programming complexity**: [[Asynchronous GPU Programming]] and [[Warp Specialization]] required to utilize efficiently

## Related Concepts

- [[TMEM]]
- [[Asynchronous GPU Programming]]
- [[Warp Specialization]]
- [[MBarrier]]

## Source Articles

- [[GPU Architecture Evolution - Volta to Rubin]]

## Questions & Thoughts

- How does the compute-to-memory ratio scaling affect algorithm design?
- At what point does TensorCore compute power become fully memory-bound?
