---
title: AI's Trillion-Dollar Opportunity - Context Graphs
url: https://x.com/JayaGup10/article/2003525933534179480
author: Jaya Gupta, Ashu Garg
date_found: 2024-12-29
date_published: 2024-12-22
tags: [ai, enterprise-software, agents, systems-of-record, processed]
status: processed
---

# AI's Trillion-Dollar Opportunity: Context Graphs

## Metadata
- **Source**: https://x.com/JayaGup10/article/2003525933534179480
- **Author**: Jaya Gupta (@JayaGup10), Ashu Garg - Foundation Capital
- **Published**: 2024-12-22
- **Found**: 2024-12-29

## Summary

The article argues that the next trillion-dollar enterprise platforms won't come from adding AI to existing systems of record (Salesforce, Workday, SAP), but from capturing **decision traces** - the reasoning, exceptions, precedents, and cross-system context that currently live in Slack threads, meetings, and people's heads. These traces accumulate into what the authors call a **context graph**: a queryable record of how decisions were made, not just what happened.

## Key Points

- Traditional systems of record store *what* happened (current state), not *why* decisions were made
- Agents need both rules AND decision traces (how rules were applied, exceptions granted, precedents set)
- The missing layer in enterprises: exception logic, precedent from past decisions, cross-system synthesis, approval chains outside systems
- **Systems of agents startups** have structural advantage: they sit in the execution path and see full context at decision time
- Incumbents (Salesforce, Snowflake, Databricks) can't easily build context graphs because:
  - Operational systems are siloed and store current state only
  - Warehouses are in the read path, not the write path (receive data via ETL after decisions made)
- Three paths for startups:
  1. Replace existing systems of record (e.g., Regie for sales engagement)
  2. Replace modules/sub-workflows (e.g., Maximor for finance)
  3. Create entirely new systems of record for decisions (e.g., PlayerZero for production engineering)

## Key Concepts

- [[Context Graph]]
- [[Decision Traces]]
- [[Systems of Record]]
- [[Systems of Agents]]
- [[Exception Logic]]
- [[Tribal Knowledge]]

## Quotes

> "Rules tell an agent what should happen in general. Decision traces capture what happened in this specific case."

> "The context graph is the single most valuable asset for companies in the era of AI."

> "Capturing decision traces requires being in the execution path at commit time, not bolting on governance after the fact."

> "These 'glue' functions emerge precisely because no single system of record owns the cross-functional workflow."

## My Thoughts

This reframes the AI agent debate from "will agents replace systems of record?" to "what new categories of truth become capturable when agents sit in the workflow?" The insight that RevOps, DevOps, and Security Ops exist *because* software doesn't capture cross-functional context is particularly compelling - it suggests where new systems of record might emerge.

## Related Articles
- [[]]

## Action Items
- [ ] Explore PlayerZero, Maximor, Regie as examples of context graph builders
- [ ] Research Arize for agent observability
- [ ] Consider how this applies to personal knowledge management (is this vault a personal context graph?)
