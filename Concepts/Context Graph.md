---
title: Context Graph
tags: [concept, ai, enterprise, key-concept]
created: 2024-12-29
---

# Context Graph

## Definition

A context graph is a living, queryable record of [[Decision Traces]] stitched across entities and time, making precedent searchable. It captures not just what happened, but *why* it was allowed to happen.

## Explanation

Unlike traditional [[Systems of Record]] that store current state (e.g., "discount = 20%"), a context graph preserves the full decision context: what inputs were gathered, what policies applied, what exceptions were granted, who approved, and why.

The context graph emerges when [[Systems of Agents]] persist decision traces on every run. Over time, these traces connect entities the business cares about (accounts, tickets, policies, approvers) via decision events and "why" links.

## Key Properties

- **Queryable precedent**: Past decisions become searchable for similar future cases
- **Replayable**: Can reconstruct the state of the world at decision time
- **Accumulating**: Every automated or human-approved decision adds to the graph
- **Cross-system**: Captures context that spans multiple tools and systems

## Examples

- A renewal agent captures: discount requested, policy evaluated, incidents pulled from PagerDuty, escalation from Zendesk, VP approval from last quarter's similar case, final Finance approval
- Over time, similar renewal exceptions become searchable precedent instead of being re-learned in Slack every quarter

## Related Concepts

- [[Decision Traces]]
- [[Systems of Agents]]
- [[Systems of Record]]
- [[Exception Logic]]
- [[Tribal Knowledge]]

## Source Articles

- [[AI's Trillion-Dollar Opportunity - Context Graphs]]

## Questions & Thoughts

- How does this relate to personal knowledge management? Is a Zettelkasten a personal context graph?
- What's the relationship between context graphs and knowledge graphs?
- Could context graphs enable "organizational memory" that survives employee turnover?

## Applications

- Enterprise decision auditing and compliance
- Agent training and improvement via historical precedent
- Reducing "tribal knowledge" dependency
- Automating exception-heavy workflows over time
