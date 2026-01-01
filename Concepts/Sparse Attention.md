---
title: Sparse Attention
tags: [concept, ai, transformers, optimization, key-concept]
created: 2024-12-29
---

# Sparse Attention

## Definition

Sparse Attention is an optimization technique for Transformer attention mechanisms that computes attention only for a subset of token pairs rather than all pairs, reducing computational complexity from O(n²) while maintaining model quality.

## Explanation

Standard attention computes relationships between all token pairs (dense attention). Sparse attention selectively attends to subsets based on patterns like:
- Local windows (nearby tokens)
- Global tokens (special positions like CLS)
- Strided patterns (every k-th token)
- Learned sparsity patterns

## The Attention Optimization Debate

The article presents three paths for scaling attention:

### 1. Linear Attention (Rejected Path)
- Reformulates attention to avoid Softmax, reducing complexity to O(n)
- Examples: Qwen-Next's GDN, Kimi Linear's KDA
- **Problem**: "Linear Attn does not solve the memory access bottleneck very well. Computation itself is easy to scale, but memory access is difficult."
- Counter-example: minmax M2 abandoned Linear Attention

### 2. Sparse Attention (Recommended Path)
- Keeps Softmax but applies it selectively
- Examples: DeepSeek-V3's DSA, NSA (Sparse Attention variants)
- **Rationale**: From Optimal Transport perspective, Softmax is the exact solution to Entropic Optimal Transport problem, mathematically optimal and unavoidable
- Computation is easy to scale; memory is the real bottleneck

### 3. Enhanced Standard Attention
- Google/DeepMind's MoR (Mixture of Ranks)
- Rumored Universal Transformer in GPT-5
- Doubles down on compute power in attention blocks

## Architectural Implications

The choice between Linear vs Sparse Attention directly influenced Nvidia's hardware decisions:

- **B200 mistake**: Cut SFU (Special Function Unit) power, creating Softmax bottlenecks
- **B300 fix**: Restored SFU capability after realizing Softmax is unavoidable
- **Lesson**: Full-stack understanding (math → algorithms → architecture) prevents costly errors

## Theoretical Foundation

SDPA (Scaled Dot-Product Attention) forward pass via Softmax is equivalent to the exact solution of a One-Sided Entropic Optimal Transport (EOT) problem. Therefore, removing Softmax means abandoning an optimal solution.

## Related Concepts

- [[TensorCore]]

## Source Articles

- [[GPU Architecture Evolution - Volta to Rubin]]

## Questions & Thoughts

- How does sparsity pattern affect model quality vs speed trade-off?
- Can learned sparsity patterns adapt during inference?
- What's the relationship between attention sparsity and model interpretability?

## Applications

- Long-context language models (handling 100K+ tokens)
- Efficient inference for resource-constrained deployment
- Real-time applications requiring low latency
