# ADE-IF Authorization Future Work

## Purpose

This document tracks unresolved architectural and specification questions identified during the repository-level challenge of Sections 1–26 of the ADE-IF Authorization Model.

The items recorded here **do not indicate defects in the ADE foundational model**.

The completed challenge identified:

- **0 foundational defects**
- **22 future specification / clarification questions**
- **0 immediate changes required to the foundational Authorization Model**

These items therefore form a **future work queue** rather than a list of required corrections to `AUTHORIZATION-MODEL.md`.

No foundational model change should be made solely because an item appears in this queue. Changes should occur only after the question has been sufficiently analyzed, discussed, and resolved through the appropriate ADE specification or governance process.

---

# Status Definitions

| Status | Meaning |
|---|---|
| **Open** | Question has been identified but has not yet been resolved. |
| **Investigating** | Architectural analysis is underway. |
| **Discussion** | The question is being considered through architectural or community discussion. |
| **Proposed** | A potential resolution has been developed but not yet accepted. |
| **Accepted** | A resolution has been formally accepted. |
| **Implemented** | The resolution has been incorporated into the appropriate specification or artifact. |
| **Deferred** | The question has intentionally been postponed. |
| **Closed** | No further action is required. |

---

# Future Work Queue

## AFW-001 — Permission vs. Capability

**Status:** Open  
**Priority:** Medium  
**Related Area:** ADE-IF Authorization

### Architectural Question

How should Permission and technical Capability be formally distinguished?

### Why It Matters

An Entity or machine may possess the technical capability to perform an Action without being authorized to perform it.

Conversely, an Entity may be authorized to perform an Action while the actual technical capability is supplied by another system.

### Current Disposition

No change to the foundational model.

### Future Work

Define the relationship between Permission, Capability, Authorization, and Action in a future specification or terminology document.

---

## AFW-002 — Policy vs. Authorization Decision

**Status:** Open  
**Priority:** High  
**Related Area:** ADE-IF Authorization

### Architectural Question

How should Policy be formally distinguished from an Authorization Decision?

### Why It Matters

A Policy may establish rules used during authorization evaluation, while an Authorization Decision represents the result of applying applicable rules and context.

### Current Disposition

No change to the foundational model.

### Future Work

Define the relationship among Policy, Rules, Evaluation, and Authorization Decision.

---

## AFW-003 — Scope vs. Context

**Status:** Open  
**Priority:** High  
**Related Area:** ADE-IF Authorization

### Architectural Question

How should Scope and Context be formally distinguished when they contain overlapping dimensions such as Time, Location, Purpose, or Entity state?

### Why It Matters

Scope represents boundaries imposed by an authorization, while Context represents circumstances used to evaluate that authorization.

### Current Disposition

No change to the foundational model.

### Future Work

Develop formal definitions and examples distinguishing authorization boundaries from evaluation circumstances.

---

## AFW-004 — Time vs. Validity

**Status:** Open  
**Priority:** Medium  
**Related Area:** ADE-IF Authorization / ADE-HTF

### Architectural Question

How should Time be distinguished from an authorization's Validity Period?

### Why It Matters

Current Time is contextual information used during evaluation, while a Validity Period is a constraint imposed on an authorization.

### Current Disposition

No change to the foundational model.

### Future Work

Define temporal relationships and coordinate terminology with the appropriate ADE time framework.

---

## AFW-005 — Location vs. Scope / Context

**Status:** Open  
**Priority:** High  
**Related Area:** ADE-IF Authorization / ADE-LF

### Architectural Question

When Location appears in authorization, when does it represent Scope and when does it represent Context?

### Why It Matters

A geographic boundary may restrict where an Action is authorized, while an Entity's current Location may simply be contextual information used during evaluation.

### Current Disposition

No change to the foundational model.

### Future Work

Coordinate with ADE-LF and establish a consistent semantic distinction.

---

## AFW-006 — Delegation Chain Limits

**Status:** Open  
**Priority:** Medium  
**Related Area:** ADE-IF Authorization / Delegation

### Architectural Question

Are there limits on how authority may be delegated through multiple Entities?

### Why It Matters

Delegation may form chains:

```text
Authority A
    ↓
Entity B
    ↓
Entity C
    ↓
Action
