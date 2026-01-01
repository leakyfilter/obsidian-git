---
title: GPU Architecture Evolution - From Volta to Rubin
url: https://x.com/jukan05/article/1992531045485531164
author: Zarbot (translated)
date_found: 2024-12-29
date_published: 2024-11-15
tags: [gpu, nvidia, hardware, architecture, ai, processed]
status: processed
---

# GPU Architecture Evolution: From Volta to Rubin

## Metadata
- **Source**: https://x.com/jukan05/article/1992531045485531164
- **Author**: Zarbot (Chinese blogger, English translation)
- **Original**: https://mp.weixin.qq.com/s?__biz=MzUxNzQ5MTExNw==&mid=2247496740&idx=1&sn=c9403138fa59d126fe6cfda19d9b2f76
- **Published**: ~2024-11-15
- **Found**: 2024-12-29

## Summary

A comprehensive technical analysis of Nvidia GPU architecture evolution from Volta (2017) to Blackwell (2024) and predictions for Vera Rubin (2026). The author argues that Nvidia's true moat isn't CUDA or SIMT, but their ability to handle architectural "dirty work" cleanly while balancing ease of use with performance. The 10-year journey from Volta's TensorCore introduction to Blackwell's TMEM represents a careful, incremental migration from traditional SIMT to fully asynchronous architectures.

## Key Points

### Evolution Highlights (Volta → Blackwell)

- **TensorCore scaling**: From 16x16 matrices (Volta) to 256x128 (Blackwell), increasing compute-to-memory ratio
- **Asynchronous progression**:
  - Volta: Independent PC per thread enabled async potential
  - Ampere: cp.async for data path asynchrony
  - Hopper: MBarrier + Warp Specialization + TMA (Tensor Memory Accelerator)
  - Blackwell: TMEM fully separates TensorCore from CUDA Core
- **Data path evolution**: RMEM → cp.async (bypass L1) → TMA (direct to SMEM) → TMEM (fully async)
- **CuTe Layout**: Software abstraction hiding Swizzle complexity and solving boundary calculations algebraically

### Blackwell's Shortcomings

1. **B200 SFU Problem**: TensorCore scaled massively but SFU (Special Function Unit) didn't, creating Softmax bottlenecks in Attention (fixed in B300)
2. **Complex instruction structure**: Mix of sync/async, thread/warp granularity instructions increases programming complexity
3. **Grace CPU issues**:
   - 1MB L2 Cache (vs 2MB in ARM Neoverse V2 spec and AWS Graviton 4)
   - Killer Microsecond problem: Kernel launch overhead significant for μs-level kernels
   - NOC (Network on Chip) latency issues when RDMA traffic traverses Grace before reaching Blackwell
4. **Dual-die memory latency**: Cross-die GMEM access brings latency penalties

### Vera Rubin Predictions

- **CPU (Vera)**:
  - 88 cores (likely Neoverse V3)
  - 8-channel memory (2x Grace bandwidth)
  - PCIe Gen6, 80 lanes
  - Uncertainty: Will L2 Cache finally be 3MB or stay at 1MB?

- **GPU (Rubin)**:
  - TensorCore: 256xNx256 (2x M dimension from Blackwell)
  - 4-CTA MMA (from Blackwell's 2-CTA)
  - **Predicted: Scalar core per SM** for descriptor generation, TMA/MMA scheduling, reducing RMEM pressure and ICache usage
  - Private SMEM (2-4KB) for MBarrier, enabling cleaner async decoupling
  - Separate I/O Die to manage area constraints

### Philosophical Insights

- **"Leading one step makes you a pioneer; leading half a step makes you a god"**: Nvidia's success is slow ecosystem evolution over 10 years, not radical leaps
- **Ease of use vs performance**: True moat is balancing these without causing "performance avalanche cases"
- **Full-stack capability**: Understanding algorithms → systems → chips enables correct architectural predictions (e.g., keeping Softmax/SFU strong because Linear Attention doesn't solve memory bottlenecks)
- **The devil is in the details**: MBarrier design, Async Proxy, CuTe abstractions, TMEM alloc/dealloc - all require deep trade-off understanding

## Key Concepts

- [[TensorCore]]
- [[Asynchronous GPU Programming]]
- [[TMEM]]
- [[Warp Specialization]]
- [[MBarrier]]
- [[CuTe Layout]]
- [[Sparse Attention]]
- [[Network on Chip]]
- [[SIMT vs SIMD]]

## Quotes

> "Nvidia's greatest moat isn't something that can be explained in just a sentence or two... its true moat lies precisely in having handled a lot of the 'dirty work' cleanly within the entire architecture, combined with full-stack capabilities from algorithms to systems to chips."

> "Being one step ahead makes you a pioneer; being half a step ahead makes you a god."

> "Linear Attn does not solve the memory access bottleneck very well. Computation itself is easy to scale, but memory access is difficult. Therefore, choosing Sparse Attn is the correct path."

> "An architect needs to ensure that customers don't fall into a performance avalanche case due to programming difficulties."

> "So-called 'overtaking on a curve' has a high probability of 'crashing on the curve'."

## My Thoughts

The Softmax/SFU insight is particularly compelling - by analyzing SDPA through Optimal Transport theory, the author concludes Softmax is mathematically optimal, therefore Linear Attention is a wrong turn. This shows how theoretical understanding drives architectural decisions. The prediction about adding scalar cores to Rubin SMs feels inevitable given the async complexity trend.

The cultural commentary about Chinese chip development and "leading half a step" is fascinating context for understanding tech adoption timelines.
## Action Items

- [ ] Research CuTe Layout algebra in more depth
- [ ] Understand MBarrier implementation details
- [ ] Read papers on Sparse Attention (DeepSeek-V3's DSA/NSA)
- [ ] Study Optimal Transport perspective on SDPA
- [ ] Compare Nvidia vs Huawei Ascend architectural choices
