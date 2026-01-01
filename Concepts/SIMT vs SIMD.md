---
title: SIMT vs SIMD
tags: [concept, gpu, architecture, programming]
created: 2024-12-29
---

# SIMT vs SIMD

## Definition

SIMT (Single Instruction, Multiple Thread) is a GPU execution model where many lightweight threads execute the same instruction stream in lockstep within a warp. SIMD (Single Instruction, Multiple Data) is a CPU vector model where one instruction operates on multiple data lanes within a single thread.

## Explanation

Both models exploit data parallelism, but they differ in how parallelism is expressed and scheduled:

- **SIMT**: Programmers write scalar thread code; the hardware groups threads into warps and issues one instruction for the group.
- **SIMD**: Programmers use vector instructions (explicit or compiler-generated) that operate on vector registers.

SIMT offers a familiar programming model with many threads, while SIMD focuses on fewer threads with wider vectors. Divergence handling also differs: SIMT masks lanes when threads diverge, while SIMD typically relies on predication or separate control flow.

## Practical Implications

- **Control flow**: Divergence is a first-class consideration in SIMT; SIMD often prefers branchless code.
- **Memory access**: SIMT emphasizes coalescing across threads; SIMD emphasizes aligned vector loads.
- **Abstractions**: SIMT makes it easier to map irregular workloads, while SIMD can deliver tighter, predictable performance for regular loops.

## Related Concepts

- [[Asynchronous GPU Programming]]
- [[Warp Specialization]]
- [[TensorCore]]

## Source Articles

- [[GPU Architecture Evolution - Volta to Rubin]]

## Questions & Thoughts

- Where does modern GPU async execution blur the line between SIMT and SIMD?
- How do compilers choose between vectorization vs spawning more threads?

