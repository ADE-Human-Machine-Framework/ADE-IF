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

## AFW-001 — Permission vs Ability

**Status:** Open  
**Priority:** Medium  
**Related Area:** ADE-IF Authorization

### Architectural Question

How should Permission and Ability be formally distinguished?

### Why It Matters

An Entity or machine may possess the technical capability to perform an Action without being authorized to perform it.

Conversely, an Entity may be authorized to perform an Action while the actual technical capability is supplied by another system.

### Current Disposition

No change to the foundational model.

### Future Work

Define the relationship between Permission, Ability, Authorization, and Action in a future specification or terminology document.

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
```

A delegated authority may therefore pass through multiple Entities before an Action is performed.

Without clearly defined boundaries, it may become difficult to determine:

* where the original authority originated;
* whether each delegation remains within the original authority;
* who is accountable for the resulting Action;
* whether delegated authority can be delegated again;
* whether restrictions remain attached throughout the delegation chain;
* whether a delegation remains valid after an earlier delegation is revoked or expires.

### Challenge Concerns

Long or recursive delegation chains may introduce uncertainty concerning:

* authority origin;
* delegation scope;
* accountability;
* revocation;
* expiration;
* visibility;
* verification;
* chain validation;
* jurisdictional boundaries;
* inherited restrictions.

A delegation should not automatically create greater authority than the authority from which it originated.

Conceptually:

```text
Original Authority
       ↓
Delegated Authority
       ↓
Further Delegated Authority
```

should remain constrained by the authority, scope, permissions, restrictions, and conditions applicable to the original delegation.

### Current Disposition

No change to the foundational model.

### Future Work

Determine whether ADE should define:

* maximum delegation depth;
* delegation inheritance rules;
* delegation boundaries;
* recursive delegation controls;
* delegation-chain visibility;
* delegation-chain validation;
* preservation of restrictions throughout a delegation chain;
* accountability across delegation chains;
* expiration propagation;
* revocation propagation.

Any resulting requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-007 — Delegation Revocation

**Status:** Open
**Priority:** High
**Related Area:** ADE-IF Authorization / Delegation

### Architectural Question

How should delegated authority and resulting authorization be revoked?

### Why It Matters

Delegated authority may need to be withdrawn before its original expiration.

When authority is delegated through multiple Entities, revocation may also need to affect downstream delegations and authorizations that depend upon the revoked authority.

Without clearly defined revocation behavior, it may become difficult to determine:

* whether downstream delegated authority remains valid;
* whether existing Permissions remain effective;
* whether active authorizations must be terminated;
* how quickly revocation must take effect;
* whether revocation applies to all delegated authority or only part of it;
* how revocation is represented and verified;
* who is responsible for propagating the revocation.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* revocation mechanisms;
* revocation propagation through delegation chains;
* partial revocation;
* emergency revocation;
* delegated-authority termination;
* effects of revocation on downstream delegations;
* effects of revocation on active authorization;
* revocation timing and effective state;
* verification of revoked authority;
* accountability for revocation propagation.

Revocation rules should preserve the distinction between **Authority, Permission, Authorization, and Execution**.

Revocation of delegated authority should not automatically imply that the underlying Identity is invalid or that the Entity no longer exists.

Any resulting requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-008 — Permission Precedence

**Status:** Open
**Priority:** High
**Related Area:** ADE-IF Authorization

### Architectural Question

When multiple Permissions and Restrictions apply simultaneously, how should precedence be determined?

### Why It Matters

An Entity may be subject to multiple Permissions, Restrictions, policies, authorities, or authorization conditions at the same time.

These may overlap or produce apparently conflicting outcomes.

Without defined precedence rules, different authorization systems may reach different decisions when evaluating the same Authorization Context.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* Permission precedence;
* Restriction precedence;
* conflict resolution mechanisms;
* interaction between Permissions and Restrictions;
* interaction between multiple applicable authorities;
* interaction between authorization conditions;
* rules for resolving conflicting authorization sources;
* whether more restrictive conditions take precedence when conflicts occur.

Precedence rules should remain contextual and should not change the fundamental distinction between:

**Ability → Permission → Authorization → Execution**

A Permission does not establish that an Entity possesses the Ability to perform an Action, and an Authorization decision does not guarantee execution.

Any resulting precedence requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-009 — Restriction Precedence

**Status:** Open
**Priority:** High
**Related Area:** ADE-IF Authorization

### Architectural Question

How should Restrictions interact when multiple Restrictions apply simultaneously?

### Why It Matters

An Entity may be subject to multiple Restrictions within the same Authorization Context.

Restrictions may overlap, conflict, differ in scope, or originate from different authorities or authorization sources.

Without defined precedence rules, different authorization systems may produce inconsistent outcomes when evaluating the same Action.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* restriction precedence;
* restriction evaluation order;
* interaction between overlapping Restrictions;
* conflict resolution between Restrictions;
* interaction between Restrictions and Permissions;
* interaction between Restrictions and authorization conditions;
* precedence across different authorities or authorization sources;
* how changes to a Restriction affect existing authorization decisions.

A Restriction may limit or prohibit an Action even when a Permission otherwise permits that Action.

Restriction evaluation should remain contextual and should not change the fundamental distinction between:

**Ability → Permission → Authorization → Execution**

A Restriction does not remove an Entity's Ability. It establishes a boundary on what may be authorized or performed within a defined context.

Any resulting precedence requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-010 — Override Authority

**Status:** Open
**Priority:** High
**Related Area:** ADE-IF Authorization / Override

### Architectural Question

Who may exercise an Override, and under what conditions?

### Why It Matters

An Override may allow an otherwise applicable Permission, Restriction, or Authorization condition to be temporarily changed or bypassed within a defined context.

Without clearly defined boundaries, Override authority could become unrestricted authority or allow an Entity to bypass established authorization controls without sufficient justification or accountability.

An Override should therefore remain subject to defined authority, scope, conditions, and duration.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* override eligibility;
* override authority;
* override scope;
* override duration;
* override conditions;
* override approval requirements;
* override evidence requirements;
* override accountability;
* interaction between Override and Restrictions;
* interaction between Override and Permissions;
* interaction between Override and delegated authority;
* termination and revocation of an Override;
* auditability of Override decisions.

An Override should not automatically create greater underlying Authority.

Conceptually:

**Authority → Override Authority → Override Decision → Action**

The authority to exercise an Override should itself be subject to the applicable Authorization Context and defined conditions.

An Override does not establish an Entity's Ability to perform an Action, and authorization through an Override does not guarantee execution.

Any resulting Override requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-011 — Emergency Authorization Lifecycle

**Status:** Open
**Priority:** High
**Related Area:** ADE-IF Authorization / Emergency Authorization

### Architectural Question

How should Emergency Authorization begin, operate, and terminate?

### Why It Matters

Emergency Authorization may be required when normal authorization processes cannot respond quickly enough to a defined emergency condition.

Emergency Authorization should remain distinguishable from normal authorization and should not become unrestricted authority.

Without clearly defined lifecycle rules, it may be difficult to determine when an emergency authorization becomes active, what conditions apply while it is active, and when it must end.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* emergency authorization activation conditions;
* emergency authorization lifecycle states;
* transition conditions between lifecycle states;
* emergency authorization scope;
* emergency authorization duration;
* applicable Permissions and Restrictions;
* approval or authority requirements;
* evidence requirements;
* monitoring requirements;
* expiration conditions;
* termination conditions;
* revocation mechanisms;
* post-emergency review and accountability.

Emergency Authorization should remain bounded by its defined **Authority, Authorization Context, scope, conditions, and duration**.

Conceptually:

**Emergency Condition → Emergency Authorization → Emergency Action → Termination**

The existence of an emergency should not automatically create unrestricted Authority.

Emergency Authorization also does not establish an Entity's Ability to perform an Action, and authorization does not guarantee execution.

Any resulting lifecycle requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-012 — Multi-Party Authorization

**Status:** Open
**Priority:** High
**Related Area:** ADE-IF Authorization

### Architectural Question

How should ADE represent authorization requiring multiple participating Entities?

### Why It Matters

Some Actions require approval, consent, or participation from multiple Entities.

The required participants may have different Authorities, Permissions, roles, or responsibilities within the same Authorization Context.

Without clearly defined multi-party authorization rules, it may be difficult to determine when the required authorization has been satisfied or how changes to participating Entities affect the authorization decision.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* quorum requirements;
* required participant roles;
* participant eligibility;
* required number or combination of approvals;
* approval sequencing;
* parallel versus sequential approval;
* participant replacement;
* participant withdrawal;
* participant failure handling;
* expiration of individual approvals;
* revocation of individual approvals;
* handling of conflicting participant decisions;
* evidence and audit requirements.

Multi-Party Authorization should distinguish between:

**participation → approval → authorization → execution**

Participation by an Entity does not necessarily mean that the Entity possesses Authority to authorize the Action.

Similarly, one participant's approval should not automatically create authorization when the defined requirements for the other participants have not been satisfied.

Multi-Party Authorization should remain subject to the applicable **Authority, Permission, Restriction, Authorization Context, and conditions**.

Any resulting multi-party authorization requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-013 — Authorization Lifecycle

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

Should ADE formally define lifecycle states for authorization-related structures and decisions?

### Why It Matters

Authorization relationships and authorization decisions may change over time.

An authorization may become active, remain valid for a defined period, be modified, suspended, expire, or be revoked.

Without defined lifecycle behavior, it may be difficult to determine the current state of an authorization or how state changes affect related Permissions, Restrictions, Delegations, and Actions.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* authorization lifecycle states;
* authorization state transitions;
* activation conditions;
* modification conditions;
* suspension conditions;
* expiration conditions;
* revocation conditions;
* restoration or reactivation conditions;
* effects of lifecycle changes on delegated authorization;
* effects of lifecycle changes on active Actions;
* representation of current authorization state;
* provenance and evidence for lifecycle transitions.

Authorization lifecycle states should remain distinct from **Identity lifecycle, Authentication state, Ability, Permission, and Execution state**.

A change in authorization state does not automatically mean that the underlying Entity, Identity, or Ability has changed.

Conceptually:

**Authorization Defined → Active → Modified / Suspended → Expired / Revoked**

The exact states and transitions should remain context-dependent until formally specified.

Any resulting lifecycle requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-014 — Authorization Scope Representation

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

How should authorization scope be represented consistently across ADE implementations?

### Why It Matters

Authorization scope defines the boundaries within which an Authorization applies.

Scope may involve the permitted Action, subject, resources, location, time, jurisdiction, organizational boundary, or other defined constraints.

Without reusable scope semantics, different systems may represent or interpret the same authorization boundaries differently, creating interoperability and authorization-evaluation problems.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* reusable authorization scope semantics;
* scope representation;
* scope boundaries;
* nested and hierarchical scopes;
* scope inheritance;
* scope expansion and restriction;
* interaction between scope and Authorization Context;
* interaction between scope and Restrictions;
* interaction between scope and Delegation;
* scope across jurisdictions and reference frames;
* interoperable representation of authorization scope.

Authorization scope should remain distinct from **Authorization Context**.

Conceptually:

**Scope = Where the Authorization applies**

**Context = The circumstances in which the Authorization is evaluated**

An Authorization should not be interpreted outside its defined scope unless an applicable authorization mechanism explicitly establishes that behavior.

Scope representation should support human and machine interpretation without requiring each implementation to invent its own meaning for equivalent authorization boundaries.

Any resulting scope requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-015 — Authorization Decision States

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

What decision states should ADE recognize when evaluating an Authorization?

### Why It Matters

Authorization evaluation may not always produce a simple authorized or denied result.

A decision may depend on incomplete information, unavailable evidence, unresolved conditions, deferred processing, or a change in authorization state.

Without defined decision semantics, different systems may interpret the same authorization outcome differently.

Possible decision states include:

```text
Authorized
Denied
Unknown
Unable To Determine
Deferred
Expired
Revoked
```

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* authorization decision states;
* decision-state semantics;
* conditions for each state;
* transitions between decision states;
* distinction between `Unknown` and `Denied`;
* distinction between `Unable To Determine` and `Denied`;
* distinction between `Deferred` and `Denied`;
* relationship between decision state and authorization lifecycle state;
* handling of expired or revoked authorization;
* representation of unresolved authorization conditions;
* machine-readable and human-readable decision outcomes.

An authorization decision state should not automatically be interpreted as a change to the underlying **Identity, Authority, Ability, Permission, or Authorization**.

For example:

**Unknown ≠ Denied**

**Unable To Determine ≠ Denied**

**Expired ≠ Revoked**

These distinctions are important because an authorization evaluation may fail to establish that an Action is authorized without establishing that the Action is explicitly prohibited.

Decision-state semantics should remain contextual and should support consistent interpretation across ADE implementations.

Any resulting decision-state requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-016 — Authorization Evidence

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

What evidence should accompany an authorization decision, and how should that evidence be represented and evaluated?

### Why It Matters

Authorization decisions may need supporting evidence to establish why a decision was reached and whether the information used during evaluation was valid and appropriate for the Authorization Context.

Evidence may be required for transparency, validation, auditability, dispute resolution, or later verification.

Without defined evidence semantics, different systems may collect, interpret, or retain authorization evidence differently.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* evidence requirements;
* evidence types;
* evidence structures;
* evidence provenance;
* evidence source identification;
* evidence validity;
* evidence freshness;
* evidence verification;
* evidence sufficiency;
* evidence retention;
* evidence disclosure requirements;
* evidence associated with delegated authorization;
* evidence associated with Override and Emergency Authorization;
* evidence required for audit and dispute resolution.

Authorization evidence should support a decision without being confused with the authorization itself.

Conceptually:

**Evidence → Evaluation → Authorization Decision**

Evidence does not itself create **Authority, Permission, or Authorization**.

The absence of available evidence should also remain distinct from evidence establishing that an Action is denied.

Evidence requirements should be evaluated within the applicable **Authorization Context**, including relevant time, location, jurisdiction, identity, authority, permissions, restrictions, and conditions.

Any resulting evidence requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-017 — Auditability

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

What authorization-related events should be auditable, and what information should an audit record contain?

### Why It Matters

Authorization processes may involve significant decisions and state changes that require accountability.

Override, delegation, emergency authorization, authorization decisions, Permission changes, Restriction changes, and revocation may all require an auditable record.

Without defined auditability requirements, it may be difficult to determine what authorization state existed at a particular point in time, who or what caused a change, or why an authorization decision was made.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* auditable authorization events;
* authorization decision records;
* delegation and delegation-revocation records;
* Override records;
* Emergency Authorization records;
* Permission changes;
* Restriction changes;
* authorization activation, suspension, expiration, and revocation;
* event timestamps;
* Entity and Authority references;
* Authorization Context;
* decision provenance;
* evidence references;
* change history;
* audit-record integrity;
* audit-record retention;
* access and disclosure controls;
* handling of distributed authorization records;
* cross-jurisdiction audit requirements.

Auditability should preserve the distinction between:

**Event → Evidence → Evaluation → Authorization Decision**

An audit record documents what occurred and the relevant context. It does not itself create **Authority, Permission, or Authorization**.

Audit records should support reconstruction of the authorization state and decision context that existed at the relevant time without requiring unnecessary disclosure of unrelated information.

Auditability requirements should also account for privacy and jurisdictional boundaries.

Any resulting auditability requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-018 — Authentication Relationship

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

What formal relationship should exist between Authentication and Authorization?

### Why It Matters

Authentication may provide assurance that an Entity is associated with a particular Identity or Identity Reference.

Authorization determines whether that Entity is permitted to perform a specific Action within a defined Authorization Context.

Authentication may therefore support an authorization decision, but Authentication and Authorization must remain distinct.

Without clearly defined boundaries, systems may incorrectly treat successful Authentication as automatic Authorization.

### Current Disposition

No change to the foundational model.

### Future Work

Define the relationship between:

```text
Identity
    ↓
Verification
    ↓
Authentication
    ↓
Authorization
    ↓
Action
```

Define:

* when Authentication is required for Authorization;
* when existing Authentication assurance may be reused;
* how authentication strength affects authorization decisions;
* how Authentication context relates to Authorization Context;
* how Authentication expiration affects existing authorization;
* how Authentication revocation affects existing authorization;
* whether different Actions require different levels of authentication assurance;
* how delegated authorization interacts with Authentication;
* how non-human Entities are authenticated;
* how authentication failures are distinguished from authorization denial.

Authentication should establish or provide assurance regarding Identity. It should not itself grant Permission or Authorization.

Verification should remain distinct from Authentication. Verification may establish or assess the validity of information, while Authentication establishes identity assurance for an Entity within a defined context.

Similarly:

**Authentication ≠ Authorization**

**Verification ≠ Authentication**

**Identity ≠ Authentication**

A successful Authentication does not automatically mean that an Entity is authorized to perform an Action.

An authorization decision may also depend on other factors, including **Authority, Ability, Permission, Restriction, Authorization Context, time, location, jurisdiction, and applicable conditions**.

Any resulting authentication-authorization requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---
## AFW-019 — Verification Relationship

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

How should Verification influence Authorization?

### Why It Matters

Verification results may contribute information or assurance used during an authorization decision.

Verification may establish whether an identity-related claim, attribute, credential, authority, or other relevant information satisfies defined requirements.

However, Verification should remain distinct from Authorization.

Without clearly defined boundaries, a verified Entity, claim, credential, or authority could incorrectly be treated as automatically authorized to perform an Action.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* verification-authority relationships;
* verification requirements for authorization;
* verification sources;
* verification status and confidence;
* verification freshness;
* verification validity periods;
* how verification results are used during authorization evaluation;
* how failed or unavailable verification affects authorization decisions;
* how verification results are represented;
* how verification evidence is associated with authorization decisions;
* how verification requirements differ across Actions and Authorization Contexts.

Verification should support the evaluation of information relevant to an authorization decision without itself creating **Permission or Authorization**.

Conceptually:

```text
Identity / Claim / Credential / Authority Information
                       ↓
                  Verification
                       ↓
              Authorization Evaluation
                       ↓
             Authorization Decision
```

A successful Verification does not automatically establish that an Entity is authorized to perform an Action.

Similarly, failure to verify information should remain distinguishable from an explicit authorization denial.

Verification should also remain distinct from Authentication.

**Verification ≠ Authentication**

**Verification ≠ Authorization**

Verification may contribute to Authentication or Authorization depending on the defined context and requirements.

Any resulting verification requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-020 — Privacy-Preserving Authorization

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

How can authorization occur while minimizing unnecessary disclosure of identity information?

### Why It Matters

Authorization should not necessarily require full identity disclosure.

An Entity may need to demonstrate that it satisfies specific authorization requirements without revealing unrelated identity attributes or information.

Without defined privacy-preserving authorization approaches, systems may disclose more identity information than is necessary to establish that an Action is authorized.

### Current Disposition

No change to the foundational model.

### Future Work

Examine:

* selective disclosure;
* attribute-based authorization;
* privacy-preserving authorization approaches;
* minimum necessary disclosure;
* proof of authorization requirements without unnecessary identity disclosure;
* separation of Identity information from authorization information;
* privacy-preserving verification;
* handling of delegated authorization;
* privacy requirements across jurisdictions;
* retention and disclosure of authorization evidence.

Privacy-preserving authorization should preserve the distinction between:

**Identity → Verification → Authentication → Authorization**

An authorization decision should disclose only the information necessary to support the decision, subject to applicable requirements and context.

An Entity should not be required to disclose its complete Identity merely because a particular attribute, credential, Permission, or authorization condition must be established.

Privacy preservation should not prevent a system from establishing the Authority, Permission, Restriction, or other conditions required for an authorization decision.

Any resulting privacy-preserving authorization requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-021 — Cross-Jurisdiction Authorization

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

How should ADE represent and evaluate authorization across multiple jurisdictions?

### Why It Matters

Different jurisdictions may establish different authorization requirements, Authorities, Permissions, Restrictions, or conditions for the same Action.

An Entity may also move between jurisdictions while an existing authorization remains active.

Without clearly defined cross-jurisdiction semantics, authorization established in one jurisdiction may be incorrectly assumed to remain valid in another.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* jurisdictional authorization relationships;
* recognition of authorization across jurisdictions;
* jurisdiction-specific Authority;
* jurisdiction-specific Permissions;
* jurisdiction-specific Restrictions;
* jurisdictional scope;
* conflict resolution between jurisdictional requirements;
* transfer or transition between jurisdictions;
* recognition of delegated authority across jurisdictions;
* authorization validity when jurisdiction changes;
* cross-jurisdiction verification and evidence;
* privacy and disclosure requirements across jurisdictions;
* representation of jurisdictional boundaries.

Cross-jurisdiction authorization should preserve the distinction between:

**Jurisdiction → Authority → Permission → Restriction → Authorization**

Authorization established within one jurisdiction should not automatically be assumed to establish authorization within another jurisdiction unless the applicable rules or Authorities recognize that authorization.

A change in jurisdiction does not automatically invalidate an Entity's Identity or Ability. It may, however, change whether a particular Action can be authorized within the new Authorization Context.

Cross-jurisdiction authorization should also support cases where multiple jurisdictions apply simultaneously rather than assuming that only one jurisdiction can govern an Action.

Any resulting cross-jurisdiction requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---

## AFW-022 — Authorization vs. Execution

**Status:** Open
**Priority:** Medium
**Related Area:** ADE-IF Authorization

### Architectural Question

How should authorization remain distinguishable from the execution and outcome of an Action?

### Why It Matters

An Entity may be authorized to perform an Action while the Action itself fails, is interrupted, is prevented by technical limitations, or produces an unexpected outcome.

Authorization therefore cannot be treated as proof that an Action was executed or successfully completed.

Without a clear distinction, systems may incorrectly interpret an authorization decision as evidence that the corresponding Action occurred.

### Current Disposition

No change to the foundational model.

### Future Work

Define:

* execution-independent authorization semantics;
* distinction between authorization and execution;
* distinction between authorization and Action outcome;
* representation of execution state;
* representation of execution failure;
* representation of partial execution;
* representation of successful completion;
* relationship between authorization decisions and execution records;
* handling of Actions that are authorized but never executed;
* handling of Actions that begin with authorization but fail during execution;
* audit and evidence requirements for execution outcomes.

The relationship should remain conceptually distinct:

```text
Ability
   ↓
Permission
   ↓
Authorization Decision
   ↓
Action Execution
   ↓
Action Outcome
```

Authorization establishes whether an Action is permitted within a defined Authorization Context.

Execution determines whether the Action is actually attempted or performed.

The Action Outcome determines what resulted from the execution.

An Entity may therefore be:

* authorized but unable to execute an Action;
* authorized but never execute the Action;
* authorized and partially execute the Action;
* authorized and successfully execute the Action;
* authorized and execute the Action unsuccessfully.

Conversely, an Entity may be technically capable of executing an Action without being authorized to do so.

**Authorization ≠ Execution**

**Authorization ≠ Action Outcome**

**Ability ≠ Authorization**

Execution failure should not automatically be interpreted as authorization failure, and successful execution should not by itself establish that the Action was properly authorized.

Any resulting execution-related requirements should be established through a future authorization specification rather than added prematurely to the foundational Authorization Model.

---


# Queue Summary

| ID      | Future Work                        | Priority | Status |
| ------- | ---------------------------------- | -------- | ------ |
| AFW-001 | Permission vs Ability              | Medium   | Open   |
| AFW-002 | Policy vs Authorization Decision   | High     | Open   |
| AFW-003 | Scope vs Context                   | High     | Open   |
| AFW-004 | Time vs Validity                   | Medium   | Open   |
| AFW-005 | Location vs Scope / Context        | High     | Open   |
| AFW-006 | Delegation Chain Limits            | Medium   | Open   |
| AFW-007 | Delegation Revocation              | High     | Open   |
| AFW-008 | Permission Precedence              | High     | Open   |
| AFW-009 | Restriction Precedence             | High     | Open   |
| AFW-010 | Override Authority                 | High     | Open   |
| AFW-011 | Emergency Authorization Lifecycle  | High     | Open   |
| AFW-012 | Multi-Party Authorization          | High     | Open   |
| AFW-013 | Authorization Lifecycle            | Medium   | Open   |
| AFW-014 | Authorization Scope Representation | Medium   | Open   |
| AFW-015 | Authorization Decision States      | Medium   | Open   |
| AFW-016 | Authorization Evidence             | Medium   | Open   |
| AFW-017 | Auditability                       | Medium   | Open   |
| AFW-018 | Authentication Relationship        | Medium   | Open   |
| AFW-019 | Verification Relationship          | Medium   | Open   |
| AFW-020 | Privacy-Preserving Authorization   | Medium   | Open   |
| AFW-021 | Cross-Jurisdiction Authorization   | Medium   | Open   |
| AFW-022 | Authorization vs Execution         | Medium   | Open   |

---

# Foundational Principle

> Future work records unresolved questions and specification areas. It does not automatically modify the foundational ADE Authorization Model.

---

**ADE Human-Machine Framework**

*An open architecture for human and machine understanding.*
