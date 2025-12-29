---
title: Systems of Agents
tags: [concept, ai, enterprise, key-concept]
created: 2024-12-29
---

# Systems of Agents

## Definition

Systems of agents are AI-native platforms where agents are first-class actors in workflows, sitting in the orchestration/execution path rather than bolted onto existing systems.

## Structural Advantage

Systems of agents startups have a key structural advantage: they're in the execution path at decision time.

When an agent triages an escalation, responds to an incident, or decides on a discount, it:
- Pulls context from multiple systems
- Evaluates rules
- Resolves conflicts
- Acts

Because it's executing the workflow, it can capture context at decision time as a first-class record - not after the fact via ETL.

## Three Paths for Startups

1. **Replace existing systems of record**: Rebuild CRM/ERP around agentic execution with event-sourced state and policy capture native to architecture (e.g., Regie for sales engagement)

2. **Replace modules/sub-workflows**: Target specific workflows where exceptions concentrate, become system of record for those decisions while syncing to incumbent (e.g., Maximor for finance workflows)

3. **Create new systems of record**: Start as orchestration layer but persist [[Decision Traces]], becoming authoritative source for "why did we do that?" (e.g., PlayerZero for production engineering)

## Related Concepts

- [[Context Graph]]
- [[Decision Traces]]
- [[Systems of Record]]

## Source Articles

- [[AI's Trillion-Dollar Opportunity - Context Graphs]]

## Questions & Thoughts

- Which "glue functions" (RevOps, DevOps, Security Ops) are ripest for systems of agents disruption?
- How do you bootstrap a context graph without full autonomy?

## Examples

- Regie (AI-native sales engagement)
- Maximor (finance workflow automation)
- PlayerZero (production engineering)
- Arize (agent observability)
