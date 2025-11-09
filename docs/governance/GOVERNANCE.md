---
title: Decision Levels and Approval Rules
version: 0.1.0
status: Draft
author: Fortney, J.
last_reviewed: 2025-11-08
---

# Decision Levels and Approval Rules

This document defines how decisions are classified, approved, and recorded in AgOpenNext.  
The goal is to maintain clarity and accountability **without slowing development** — document what matters, skip what doesn’t.

## 1. Decision Levels

| Level | Scope | Examples | Approval |
|-------|--------|-----------|-----------|
| **L0 — Trivial** | Typos, comments, docs, or formatting | Fixing grammar, adjusting whitespace | Self-merge after CI passes |
| **L1 — Minor / Internal** | Non-functional updates or internal refactors | CI scripts, internal tooling, small logic cleanup | One Reviewer or Maintainer |
| **L2 — Domain Feature / Refactor** | Feature or refactor within a single area; no new public interfaces | UI change, module refactor, tuning an algorithm | Project Lead or Maintainer + one Reviewer |
| **L3 — Cross-Domain / Public Interface** | Impacts multiple areas, introduces or changes public APIs, or adds dependencies | New message format, new plugin interface | Two Maintainers or Systems Engineers |
| **L4 — Architecture / Governance** | Alters architecture, governance, or licensing | New subsystem, protocol definition, governance edits | Project Coordinator + one Systems Engineer or Maintainer (not the author) |

Notes:
- Levels indicate *impact*, not complexity.  
- The Project Coordinator may raise or lower a decision level if circumstances warrant.

## 2. Evidence and Documentation

Keep documentation proportional to impact.

- **L0–L1:** No extra documentation required beyond clear commit messages.  
- **L2:** Mention the related Issue or link to an ADR draft if one exists.  
- **L3–L4:** Must link to an ADR or Issue summarizing reasoning and trade-offs.  

No one should delay implementation waiting for documentation; capture details as part of the PR or immediately after merge.

## 3. Review Rules

- Every pull request must be reviewed by **at least one person who didn’t write it**.  
- Large or cross-domain changes (L3–L4) require review from someone familiar with affected areas.  
- Reviewers focus on correctness, clarity, and test coverage — not personal style.  
- The Project Coordinator breaks ties or resolves blocking disagreements.

## 4. Traceability (Efficient Model)

Traceability should enable understanding, not bureaucracy.

- For quick changes, a descriptive commit message is enough.  
- For impactful changes, link to an Issue or ADR so future contributors can see why something was done.  
- The Systems Engineer maintains an ADR index, but contributors don’t need to pause development waiting on it.  
- If a decision isn’t worth writing an ADR for, it’s probably not an L3 or L4 decision.

The intent is simple: **leave breadcrumbs, not paperwork.**

## 5. Escalation and Resolution

1. If reviewers can’t agree, escalate to the Project Coordinator.  
2. The Coordinator may request input from other Maintainers or Systems Engineers.  
3. The Coordinator’s ruling is final unless overturned by a subsequent ADR or governance amendment.

## 6. Amendments

Changes to this document follow the [Governance Amendment Process](./GOVERNANCE.md#7-amendment-process).
