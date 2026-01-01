---
title: TMEM
tags: [concept, gpu, hardware, memory]
created: 2024-12-29
---

# TMEM (Tensor Memory)

## Definition

TMEM (Tensor Memory) is a dedicated memory space introduced in Nvidia's Blackwell architecture that stores [[TensorCore]] operands and results independently from CUDA Core registers (RMEM), enabling fully asynchronous tensor operations.

## Explanation

TMEM represents the culmination of a 10-year evolution in how TensorCores access data:

**Before TMEM**:
- Volta: TensorCore reused CUDA Core registers
- Ampere: cp.async bypassed L1 to reduce register pressure
- Hopper: TMA placed operands in SMEM, but Accumulators still in RMEM, requiring waitgroup barriers (WGMMA was explicitly marked as temporary)

**With TMEM (Blackwell)**:
- TensorCore and CUDA Core fully separated
- Operands and results stored in dedicated TMEM
- Reuses [[MBarrier]] mechanism from TMA
- TMA and tcgen05.mma can be issued at Thread level
- Memory management via alloc/dealloc reduces multi-thread parallelism complexity

## Architectural Impact

TMEM consumed significant die area on Blackwell, contributing to:
- Reduction to 80 SMs per die (from previous generations)
- Trade-offs in other functional units (e.g., SFU on B200)

Future (Rubin): Expected to increase TMEM capacity to handle doubled TensorCore scale.

## Programming Model

TMEM introduces both synchronous and asynchronous instructions in tcgen05 instruction set:
- Thread-granularity operations (issue TMA/MMA)
- Warp-granularity operations (memory allocation/copying)
- Requires careful barrier management to avoid synchronization errors

The col-based alloc/dealloc design simplifies managing TMEM under multi-thread scenarios.

## Related Concepts

- [[TensorCore]]
- [[Asynchronous GPU Programming]]
- [[MBarrier]]
- [[Warp Specialization]]

## Source Articles

- [[GPU Architecture Evolution - Volta to Rubin]]

## Questions & Thoughts

- How does TMEM capacity scale with die size constraints?
- Could TMEM architecture influence future 3D-DRAM designs?
