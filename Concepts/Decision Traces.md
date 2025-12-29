---
title: Decision Traces
tags: [concept, ai, enterprise]
created: 2024-12-29
---

# Decision Traces

## Definition

Decision traces are structured records capturing what happened in a specific case: which definition was used, under what policy version, with what exceptions, based on which precedents, and what was changed.

## Explanation

While rules tell an agent what *should* happen in general, decision traces capture what *actually* happened in specific cases. They preserve the reasoning that connects data to action - something enterprises almost never systematically store.

Decision traces differ from audit logs: they don't just record actions, but the *context* and *rationale* behind them.

## What Decision Traces Capture

- Inputs gathered from across systems at decision time
- Policies and rules evaluated
- Exceptions invoked and why
- Who approved deviations
- Precedents that influenced the decision
- Final state written to systems

## Why They're Currently Missing

Most enterprises don't treat reasoning as data. The synthesis happens in people's heads:
- The support lead checks ARR in Salesforce, sees escalations in Zendesk, reads a Slack thread - but the ticket just says "escalated to Tier 3"
- A VP approves a discount on Zoom - the CRM shows final price, not who approved the deviation or why

## Related Concepts

- [[Context Graph]]
- [[Systems of Agents]]
- [[Exception Logic]]
- [[Tribal Knowledge]]

## Source Articles

- [[AI's Trillion-Dollar Opportunity - Context Graphs]]

## Questions & Thoughts

- What's the right granularity for decision traces? Every micro-decision or just significant ones?
- How do you balance decision trace capture with privacy/compliance?
