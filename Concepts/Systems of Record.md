---
title: Systems of Record
tags: [concept, enterprise, software]
created: 2024-12-29
---

# Systems of Record

## Definition

Systems of record are enterprise software platforms that serve as the canonical, authoritative source for specific business data. They own the data, own the workflow, and create lock-in.

## Explanation

The last generation of enterprise software created a trillion-dollar ecosystem by becoming systems of record:
- **Salesforce** for customers
- **Workday** for employees
- **SAP** for operations

These systems store *current state* - what the data looks like now. They're optimized for being the single source of truth for their domain.

## Limitations in the AI Era

Systems of record face structural challenges with AI agents:

1. **Current state only**: They know what an opportunity looks like now, not what it looked like when a decision was made
2. **Siloed**: A support escalation depends on CRM data, billing SLAs, PagerDuty outages, and Slack threads - no single system sees this
3. **No decision context**: When a discount is approved, the justifying context isn't preserved

## The Agent Question

The debate: do systems of record survive the shift to agents?

- **One view**: Agents don't replace SoRs, they raise the bar for what a good one looks like
- **Counter-view**: New systems of record for *decisions* (not just objects) may emerge as the next trillion-dollar platforms

## Related Concepts

- [[Systems of Agents]]
- [[Context Graph]]
- [[Decision Traces]]

## Source Articles

- [[AI's Trillion-Dollar Opportunity - Context Graphs]]

## Examples

- Salesforce (CRM)
- Workday (HCM)
- SAP (ERP)
- ServiceNow (ITSM)
