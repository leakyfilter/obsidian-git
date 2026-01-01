---
title: Network on Chip
tags: [concept, gpu, hardware, architecture]
created: 2024-12-29
---

# Network on Chip

## Definition

Network on Chip (NoC) is the on-die interconnect fabric that moves data between GPU components (SMs, caches, memory controllers, I/O) with defined bandwidth and latency characteristics.

## Explanation

As GPUs grow in complexity and adopt multi-die packaging, the NoC becomes a major determinant of end-to-end performance:

- **Traffic routing**: Controls how reads, writes, and coherence messages traverse the chip
- **Contention hotspots**: Shared links can become bottlenecks under heavy RDMA or memory traffic
- **Topology sensitivity**: Ring, mesh, or hierarchical designs trade off latency vs bandwidth

In Blackwell and beyond, cross-die traffic increases the importance of NoC latency and routing decisions, especially when memory access must traverse a neighboring die.

## Key Properties

- **Bandwidth vs latency**: Wider links improve throughput but don't always reduce tail latency
- **Arbitration**: Priority and fairness policies decide which packets move first under contention
- **Virtual channels**: Separate traffic classes can reduce head-of-line blocking
- **Locality**: Access patterns that stay within a die or cluster reduce cross-chip hops

## Bottlenecks & Signals

- **Congestion spikes**: Bursty collective operations can saturate shared links
- **Tail latency**: A small fraction of requests experience large delays under load
- **Routing detours**: Suboptimal paths introduce extra hops even when links are free

## Examples

- RDMA traffic that routes through a CPU die (Grace) before reaching GPU memory can add microseconds of latency.
- Cross-die global memory access incurs extra hops across the NoC compared to local die access.

## Developer Impact

- **Kernel placement**: Work partitioning that keeps producer/consumer on the same die can reduce NoC pressure
- **Batching**: Larger, fewer transfers can be easier on the NoC than many small messages
- **Overlapping**: Async pipelines hide NoC latency but can worsen contention if not balanced

## Related Concepts

- [[TMEM]]
- [[Asynchronous GPU Programming]]
- [[TensorCore]]

## Source Articles

- [[GPU Architecture Evolution - Volta to Rubin]]

## Questions & Thoughts

- How does NoC topology evolve with multi-die GPUs?
- What are practical ways to model NoC bottlenecks when optimizing kernels?
