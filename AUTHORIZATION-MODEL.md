# ADE Human-Machine Framework

## ADE-IF — Authorization Model

**Status:** Foundational Draft  
**Repository:** ADE-IF  
**Version:** 0.1.0

---
## 1. Purpose

The ADE-IF Authorization Model defines the foundational concepts required to represent authorization within the ADE Human-Machine Framework.

The model establishes a common semantic structure for representing:

* Authority
* Authorization
* Permission
* Restriction
* Delegation
* Override
* Emergency Authority
* Authorization Conditions
* Authorization Context
* Authorization Decisions
* Authorization Sources
* Authorization Lifecycles

The purpose of the Authorization Model is to allow authorization-related information to be understood consistently by humans and machines while remaining compatible with the distributed and context-dependent principles established by ADE-Core and ADE-IF.

Authorization determines whether an Entity is permitted to perform, request, approve, modify, interrupt, cancel, delegate, or otherwise participate in an Action within a defined context.

The Authorization Model therefore focuses on what an Entity is permitted to do rather than who or what the Entity is.

Authorization should remain distinct from identity, verification, and authentication even when those concepts participate in authorization decisions.

---

## 2. Relationship to ADE-Core and ADE-IF

The ADE-IF Authorization Model builds upon the foundational concepts established by ADE-Core and the identity concepts established by ADE-IF.

Authorization commonly involves relationships between:

* Entity
* Action
* State
* Event
* Time
* Location
* Relationship
* Intent

as defined by ADE-Core.

Authorization also interacts with ADE-IF concepts such as:

* Identity
* Identity Reference
* Identity Claim
* Verification
* Authentication
* Authority

Conceptually:

```text
ADE-Core
    │
    ├── Entity
    ├── Action
    ├── State
    ├── Event
    ├── Time
    └── Location
            │
            ▼
        ADE-IF
            │
            ├── Identity
            ├── Verification
            ├── Authentication
            └── Authority
                    │
                    ▼
          Authorization Model
                    │
                    ├── Permission
                    ├── Restriction
                    ├── Delegation
                    ├── Override
                    ├── Conditions
                    └── Authorization Decision
---

## 3. Authority and Authorization

**Authority** and **Authorization** are related but distinct concepts within ADE-IF.

### Authority

**Authority** is the recognized capacity of an Entity, organization, system, or other Entity to establish, grant, modify, approve, restrict, or exercise control over a defined subject, Action, or area of responsibility within a particular context.

Authority may originate from:

* Law or regulation
* Organizational responsibility
* Contractual agreement
* Delegation
* Ownership or control
* System configuration
* Established governance
* Other recognized sources of authority

Authority is contextual.

An Entity may possess authority over one Action, system, resource, or area of responsibility without possessing authority over all other Actions or resources.

Conceptually:

```text
Authority
    │
    ├── Entity
    ├── Scope
    ├── Source
    ├── Context
    └── Conditions
```

For example:

```text
Government Authority
        │
        └── establishes ──> Legal Requirement

Organization
        │
        └── establishes ──> Operational Policy

System Administrator
        │
        └── controls ──> System Configuration

Human Operator
        │
        └── authorized to perform ──> Defined Operation
```

Authority should therefore not automatically be interpreted as permission to perform every Action.

---

### Authorization

**Authorization** is the determination that an Entity is permitted to perform, request, approve, modify, interrupt, cancel, delegate, or otherwise participate in a defined Action within a particular context.

Conceptually:

```text
Entity
   │
   ▼
Authorization
   │
   ├── Action
   ├── Scope
   ├── Context
   └── Conditions
```

For example:

```text
Entity
   │
   ▼
Authorization
   │
   └──► Pause Machine
```

The authorization may apply only to that specific Action and may be limited by additional conditions.

---

### Authority Does Not Equal Authorization

An Entity may possess authority without being authorized for a particular Action at a particular time.

For example:

```text
Organization
    │
    └── Authority over System
              │
              ▼
        Authorization Policy
              │
              ▼
        Authorized Operator
              │
              ▼
          Permitted Action
```

Similarly, an Entity may receive authorization through a delegation of authority without becoming the original source of that authority.

Therefore:

```text
Authority
    ≠
Authorization
```

---

### Authorization Is Contextual

Authorization should be evaluated within a defined context.

Relevant context may include:

* Entity
* Identity
* Authentication status
* Action
* Resource
* Role
* Relationship
* Time
* Location
* State
* Purpose
* Policy
* Authority
* Conditions
* Emergency status
* Other applicable requirements

Conceptually:

```text
Entity
   +
Identity / Authentication
   +
Action
   +
Context
   +
Conditions
   ↓
Authorization Decision
```

The same Entity may therefore be authorized for one Action while being unauthorized for another.

For example:

```text
Operator
   │
   ├──► Start Machine       = Authorized
   │
   ├──► Pause Machine       = Authorized
   │
   ├──► Modify Safety Rules = Not Authorized
   │
   └──► Delete System       = Not Authorized
```

Authorization must therefore describe what is permitted rather than simply assigning a general status of "authorized" to an Entity.

---

### Authorization as a Relationship

ADE-IF treats authorization as a relationship between an Entity and an Action within a defined context.

Conceptually:

```text
Entity
   │
   │ authorized for
   ▼
Action
```

The relationship may contain additional information:

```text
Authorization
      │
      ├── Subject Entity
      ├── Action
      ├── Scope
      ├── Authority
      ├── Conditions
      ├── Time
      ├── Location
      ├── Status
      └── Source
```

This allows authorization to be represented as a contextual relationship rather than as an inherent characteristic of an Entity.

---

### Authorization Is Not a Measure of Trustworthiness

Authorization should not automatically be interpreted as a measure of an Entity's general trustworthiness, identity certainty, capability, or value.

For example:

```text
Authorized to operate Machine A
```

does not necessarily mean:

```text
Authorized to operate Machine B
```

and:

```text
Authorized to perform Action A
```

does not necessarily mean:

```text
Trusted for every purpose
```

Authorization should remain limited to the scope for which it has been established.

---

### Authorization and Identity

Identity establishes which Entity is being referenced.

Authorization establishes whether that Entity is permitted to perform a defined Action.

Conceptually:

```text
Identity
    ↓
Which Entity?
    ↓
Verification / Authentication
    ↓
Can the Entity be associated with the claimed identity?
    ↓
Authorization
    ↓
Is the Entity permitted to perform this Action?
```

These concepts may participate in the same process but should remain semantically distinguishable.

---

### Foundational Distinction

ADE-IF therefore establishes the following distinction:

```text
Entity
   ↓
Identity
   ↓
Verification / Authentication
   ↓
Authority / Applicable Policy
   ↓
Authorization
   ↓
Permitted Action
```

The existence of an identity does not automatically create authority.

The existence of authority does not automatically create authorization for every Action.

Authorization must be established within the applicable scope, context, and conditions.
---
## 4. Permission

A **Permission** represents an allowed capability associated with an Entity within a defined authorization context.

Permission describes what an Entity is permitted to do, access, receive, modify, approve, interrupt, cancel, or otherwise participate in.

Conceptually:

```text
Authorization
      │
      ▼
Permission
      │
      ▼
Allowed Action
```

A Permission should not be interpreted as a general authorization to perform all Actions.

Instead, it should identify the specific capability or set of capabilities granted within a defined scope.

---

### 4.1 Permission and Action

A Permission is associated with one or more defined Actions.

For example:

```text
Entity
   │
   ▼
Permission
   │
   ├── Start Machine
   ├── Stop Machine
   └── Pause Machine
```

Another Entity may have a different permission set:

```text
Entity
   │
   ▼
Permission
   │
   └── Observe Machine
```

The Entities may therefore interact with the same system while possessing different permissions.

---

### 4.2 Permission Scope

A Permission may be limited to a defined scope.

Scope may include:

* A specific Action
* A group of Actions
* A specific resource
* A system
* A location
* A jurisdiction
* A role
* A relationship
* A defined purpose
* Other applicable boundaries

Conceptually:

```text
Permission
    │
    ├── Subject
    ├── Action
    ├── Resource
    ├── Scope
    └── Conditions
```

For example:

```text
Operator
   │
   └── Permission
          │
          ├── Action = Pause
          ├── Resource = Machine A
          └── Location = Facility A
```

The permission does not automatically extend to another machine or location.

---

### 4.3 Permission Conditions

A Permission may be subject to conditions.

Conditions may include:

* Time
* Location
* State
* Purpose
* Authorization level
* Required relationship
* Required number of authorized Entities
* Emergency status
* System condition
* Other defined requirements

For example:

```text
Permission
    │
    ├── Action = Override
    ├── Resource = System A
    ├── Time = Defined Period
    └── Condition = Emergency
```

A Permission may therefore exist while remaining inactive until its required conditions are satisfied.

---

### 4.4 Permission Does Not Guarantee Execution

Possessing a Permission does not necessarily mean that an Action will successfully execute.

For example:

```text
Entity
   │
   ▼
Permission
   │
   ▼
Authorization
   │
   ▼
Action Requested
   │
   ▼
System State
   │
   ├── Action Permitted
   │
   └── Action Cannot Execute
```

An Action may be authorized but prevented by:

* System state
* Safety requirements
* Technical limitations
* Conflicting conditions
* Resource availability
* Higher-priority restrictions
* Other applicable rules

Authorization and permission therefore establish whether an Action may be performed, not whether the Action will necessarily succeed.

---

### 4.5 Permission and Capability

Permission should be distinguished from capability.

An Entity may possess the technical capability to perform an Action without being authorized to do so.

For example:

```text
System Capability
       │
       └── Can execute Shutdown
```

does not necessarily mean:

```text
Entity
       │
       └── Authorized to execute Shutdown
```

Similarly, an Entity may be authorized to request an Action while lacking the technical capability to execute it directly.

Conceptually:

```text
Capability
    ≠
Permission
    ≠
Authorization
```

These concepts may interact but should remain distinguishable.

---

### 4.6 Permission and Delegation

A Permission may be granted directly to an Entity or may be obtained through an authorized delegation.

For example:

```text
Authority
    │
    ▼
Entity A
    │
    │ delegates
    ▼
Entity B
    │
    ▼
Permission
    │
    ▼
Allowed Action
```

Delegated permissions should remain subject to the scope and conditions established by the granting authority.

Delegation does not necessarily transfer the underlying authority itself.

---

### 4.7 Permission Status

A Permission may have a lifecycle or status.

Possible states include:

```text
Pending
Active
Suspended
Expired
Revoked
Cancelled
```

For example:

```text
Permission
    │
    ├── Status = Active
    ├── Valid From
    └── Valid Until
```

A Permission that has expired or been revoked should not be treated as an active permission.

The status of a Permission should remain distinguishable from the identity status of the Entity.

---

### 4.8 Permission for Human and Non-Human Entities

Permissions may apply to different classes of Entity.

Examples include:

```text
Human
   └── Permission to operate equipment

Organization
   └── Permission to access service

Device
   └── Permission to communicate with system

Software System
   └── Permission to execute defined process

Digital Agent
   └── Permission to perform defined Action
```

The semantic structure of the Permission may remain consistent while the applicable requirements differ according to the Entity type and context.

---

### 4.9 Permission Is Purpose-Bound

A Permission should be interpreted according to the purpose for which it was established.

For example:

```text
Permission
    │
    ├── Subject = Entity A
    ├── Action = Access
    ├── Resource = Service A
    └── Purpose = Service Delivery
```

This does not automatically establish permission to use the same information or access for an unrelated purpose.

Purpose may therefore form part of the authorization context.

---

### 4.10 Foundational Principle

ADE-IF treats Permission as a defined capability granted to an Entity within a particular authorization context.

Conceptually:

```text
Entity
   +
Authorization
   +
Scope
   +
Conditions
   ↓
Permission
   ↓
Allowed Action
```

A Permission should therefore be specific enough to establish what is allowed while remaining distinct from identity, authority, capability, and the successful execution of an Action.

---
## 5. Restriction

A **Restriction** defines a boundary, limitation, condition, or prohibition that constrains what an Entity may perform, access, receive, modify, approve, interrupt, cancel, or otherwise participate in within a defined authorization context.

A Restriction may apply even when an Entity possesses an otherwise valid Permission.

Conceptually:

```text
Authorization
      │
      ├── Permission
      │      └── What is allowed
      │
      └── Restriction
             └── What is limited or prohibited
```

Restrictions therefore help establish the boundaries within which a Permission may be exercised.

---

### 5.1 Restriction and Permission

A Permission and a Restriction may apply to the same Entity and Action.

For example:

```text
Entity
   │
   ├── Permission
   │      └── Operate Machine A
   │
   └── Restriction
          └── Cannot modify safety controls
```

The Entity is authorized to operate the machine but remains restricted from modifying its safety controls.

Conceptually:

```text
Permission
    +
Restriction
    ↓
Effective Authorization
```

A Permission should therefore not automatically override a Restriction.

---

### 5.2 Types of Restriction

Restrictions may be established for different reasons.

Examples include:

* Safety
* Security
* Legal requirements
* Organizational policy
* Jurisdictional requirements
* Operational limitations
* Resource limitations
* Role limitations
* Time limitations
* Location limitations
* State-dependent limitations
* Emergency conditions
* Privacy requirements

Different restrictions may apply to the same Entity depending on the context.

---

### 5.3 Scope of a Restriction

A Restriction may apply to:

* An Entity
* An Action
* A Resource
* A System
* A Location
* A Time period
* A Jurisdiction
* A Purpose
* A Relationship
* A State
* A defined combination of these

Conceptually:

```text
Restriction
    │
    ├── Subject
    ├── Action
    ├── Resource
    ├── Scope
    └── Conditions
```

For example:

```text
Operator
   │
   └── Restriction
          │
          ├── Action = Modify
          ├── Resource = Safety System
          └── Location = Facility A
```

The restriction does not necessarily apply to every Action performed by the Operator.

---

### 5.4 Conditional Restrictions

A Restriction may become applicable only when defined conditions exist.

For example:

```text
Restriction
    │
    ├── Action = Override
    ├── Condition = Normal Operation
    └── Result = Prohibited
```

The same Action may become permitted under an emergency authorization process:

```text
Emergency Condition
       ↓
Additional Authorization
       ↓
Override Permitted
```

Restrictions may therefore be context-dependent rather than permanently attached to an Entity.

---

### 5.5 Time-Based Restrictions

A Restriction may apply during a defined period.

For example:

```text
Restriction
    │
    ├── Action = Access
    ├── Valid From
    └── Valid Until
```

An Entity may therefore have:

```text
09:00–17:00
    └── Access Permitted

17:00–09:00
    └── Access Restricted
```

Time-based restrictions should remain compatible with ADE-Core and ADE-HTF.

---

### 5.6 Location-Based Restrictions

A Restriction may apply to a defined Location.

For example:

```text
Entity
   │
   └── Permission
          │
          ├── Action = Operate
          ├── Resource = Machine A
          └── Location = Facility A
```

The Entity may be permitted to operate the machine at Facility A while being restricted from operating the same machine or equivalent system at another location.

Location-based restrictions should remain compatible with ADE-Core and ADE-LF.

---

### 5.7 State-Based Restrictions

Restrictions may depend upon the State of an Entity, Object, System, or other relevant ADE concept.

For example:

```text
Machine State = Maintenance
        ↓
Restriction
        ↓
Normal Operation Prohibited
```

Another example:

```text
System State = Emergency
        ↓
Normal Authorization Rules
        ↓
Modified / Restricted
```

State-based restrictions allow authorization decisions to respond to changing conditions.

---

### 5.8 Safety Restrictions

Safety-related restrictions may prevent an otherwise authorized Action when required conditions are not satisfied.

For example:

```text
Operator
   │
   └── Permission = Start Machine
                    │
                    ▼
             Safety Conditions
                    │
             ┌──────┴──────┐
             ▼             ▼
          Satisfied     Not Satisfied
             │             │
             ▼             ▼
          Allowed       Restricted
```

The existence of a Permission does not eliminate safety requirements.

Safety restrictions may therefore take precedence over ordinary operational permissions where defined by the applicable authority or policy.

---

### 5.9 Jurisdictional Restrictions

A Restriction may arise because an Action or information request is subject to a particular jurisdiction.

For example:

```text
Request
   │
   ▼
Jurisdiction Check
   │
   ├── Permitted
   │
   └── Restricted
```

A system should not assume that authorization granted within one jurisdiction automatically establishes authorization within another.

Jurisdictional restrictions may therefore affect:

* Access
* Disclosure
* Processing
* Transfer
* Identity verification
* Credential use
* Authorization

---

### 5.10 Privacy Restrictions

Privacy requirements may restrict disclosure even when a requesting Entity is otherwise authorized to access a service or perform an Action.

For example:

```text
Entity
   │
   └── Authorized for Service
              │
              ▼
        Information Request
              │
              ▼
        Privacy Restriction
              │
              ▼
      Minimum Necessary Data
```

An Entity may therefore be authorized to receive a result without being authorized to receive the complete underlying identity information.

This supports the ADE-IF principle of minimum necessary disclosure.

---

### 5.11 Restriction and Delegation

A delegated Permission may remain subject to Restrictions imposed by the original authority.

For example:

```text
Authority
    │
    ▼
Entity A
    │
    │ Delegates
    ▼
Entity B
    │
    ▼
Permission
    │
    ▼
Restrictions
```

Delegation should not automatically remove or weaken applicable Restrictions.

A delegated authority may therefore be narrower than the authority held by the Entity providing the delegation.

---

### 5.12 Restriction and Override

Some systems may allow a Restriction to be overridden under specifically defined circumstances.

For example:

```text
Restriction
      │
      ▼
Normal Operation
      │
      └── Action Prohibited
```

An emergency process may establish:

```text
Emergency Condition
      │
      ▼
Additional Authorization
      │
      ▼
Override Authority
      │
      ▼
Restriction Temporarily Overridden
```

An override should itself be treated as an authorized Action subject to defined requirements.

The existence of an override capability should not imply unrestricted authority.

---

### 5.13 Multiple Restrictions

An Action may be subject to multiple Restrictions simultaneously.

For example:

```text
Action Request
      │
      ├── Safety Restriction
      ├── Time Restriction
      ├── Location Restriction
      ├── Role Restriction
      └── Jurisdiction Restriction
```

The effective authorization decision may therefore depend upon satisfying all applicable requirements.

Conceptually:

```text
Permission
     +
Applicable Restrictions
     +
Current Conditions
     ↓
Authorization Decision
```

The interaction between conflicting Restrictions and Permissions should be defined by the applicable authorization policy or future ADE specification.

---

### 5.14 Restriction Status

A Restriction may have its own lifecycle or status.

Possible states include:

```text
Pending
Active
Suspended
Expired
Revoked
Cancelled
```

A Restriction may therefore become applicable, cease to apply, or be replaced over Time.

The status of a Restriction should remain distinguishable from the identity or authorization status of the Entity.

---

### 5.15 Restriction Is Not Identity

A Restriction should not be interpreted as a statement about the identity, value, capability, or general trustworthiness of an Entity.

For example:

```text
Entity restricted from Action A
```

does not necessarily mean:

```text
Entity is untrusted
```

It may simply mean:

```text
Entity is not authorized for Action A
within this particular context.
```

Restrictions should therefore remain purpose-specific and contextual.

---

### 5.16 Foundational Principle

ADE-IF treats a Restriction as a defined boundary or limitation on the exercise of authority or Permission.

Conceptually:

```text
Entity
   +
Authority
   +
Permission
   +
Restrictions
   +
Context
   ↓
Effective Authorization
```

A Restriction may limit, condition, suspend, or prohibit an otherwise possible Action.

The purpose of representing Restrictions explicitly is to ensure that authorization does not become a simple binary condition of "authorized" or "not authorized."

Authorization may instead depend upon the interaction of permissions, restrictions, conditions, context, and applicable authority.

---

## 6. Authorization Context

An **Authorization Context** defines the circumstances within which an authorization decision is evaluated.

Authorization should not be interpreted independently of its context.

The same Entity may be authorized to perform an Action in one context and restricted from performing the same Action in another.

Conceptually:

```text
Entity
   +
Action
   +
Authorization Context
   ↓
Authorization Decision
```

An Authorization Context may include:

* Entity
* Identity
* Authentication status
* Action
* Resource
* Authority
* Permission
* Restriction
* Time
* Location
* State
* Purpose
* Relationship
* Jurisdiction
* Emergency conditions
* Other applicable conditions

---

### 6.1 Contextual Authorization

Authorization is contextual rather than an inherent property of an Entity.

For example:

```text
Operator
   │
   ├──► Start Machine A
   │       └── Authorized
   │
   ├──► Start Machine B
   │       └── Not Authorized
   │
   └──► Modify Safety Configuration
           └── Not Authorized
```

The Entity remains the same, but the authorization context changes.

---

### 6.2 Subject of Authorization

The **Subject** identifies the Entity to which the authorization applies.

The subject may be:

* A Human
* An Organization
* A Device
* A Machine
* A Software System
* A Service
* A Digital Agent
* Another Entity

Conceptually:

```text
Authorization
      │
      └── Subject
              │
              └── Entity
```

The Subject should be distinguishable from the Authority that establishes or grants the authorization.

For example:

```text
Authority
    │
    └── authorizes ──> Subject
```

---

### 6.3 Action

The **Action** identifies what the Subject is authorized or restricted to perform.

Examples include:

```text
Access
Read
Write
Start
Stop
Pause
Cancel
Approve
Modify
Delete
Transfer
Override
```

An authorization should not be considered complete without establishing the Action or category of Action to which it applies.

Conceptually:

```text
Subject
   +
Action
   ↓
Authorization
```

---

### 6.4 Resource

An authorization may apply to a specific Resource or group of Resources.

Examples include:

```text
System A
Machine B
Database C
Facility D
Identity Record E
Service F
```

Conceptually:

```text
Subject
   +
Action
   +
Resource
   ↓
Authorization
```

A Permission to access one Resource does not automatically establish permission to access another Resource.

---

### 6.5 Time

Authorization may be limited by Time.

For example:

```text
Authorization
    │
    ├── Valid From
    └── Valid Until
```

An authorization may therefore be:

```text
Active during defined period
```

while being:

```text
Inactive outside that period
```

Time-based authorization should remain compatible with ADE-Core and ADE-HTF.

---

### 6.6 Location

Authorization may depend upon Location.

For example:

```text
Authorization
    │
    ├── Action = Operate
    ├── Resource = Machine A
    └── Location = Facility A
```

The same Entity may not possess the same authorization at another Location.

Location-based authorization should remain compatible with ADE-Core and ADE-LF.

---

### 6.7 State

Authorization may depend upon the current or defined State of an Entity, Object, System, or other relevant ADE concept.

For example:

```text
Machine State = Maintenance
        │
        ▼
Authorization Context
        │
        ▼
Normal Operation Restricted
```

Another example:

```text
System State = Emergency
        │
        ▼
Emergency Authorization Rules
```

State may therefore alter the applicable permissions, restrictions, or authorization requirements.

---

### 6.8 Purpose

Authorization may depend upon the Purpose for which an Action is being performed.

For example:

```text
Entity
   │
   └── Permission = Access Information
                      │
                      ├── Purpose = Service Delivery
                      │      └── Permitted
                      │
                      └── Purpose = Unrelated Activity
                             └── Restricted
```

A Permission granted for one purpose should not automatically establish permission for unrelated purposes.

Purpose may therefore form part of the Authorization Context.

---

### 6.9 Relationship

Authorization may depend upon an established Relationship between Entities.

Examples include:

```text
Employee
   │
   └── employed by ──> Organization

Guardian
   │
   └── responsible for ──> Child

Operator
   │
   └── assigned to ──> Machine

Administrator
   │
   └── responsible for ──> System
```

A Relationship may establish or contribute to authorization without itself being equivalent to authorization.

For example:

```text
Employee
    ≠
Automatically Authorized for Every Organization System
```

The applicable relationship must be interpreted within the defined authorization context.

---

### 6.10 Jurisdiction

Authorization may be affected by the jurisdiction in which an Action occurs or in which the applicable authority operates.

For example:

```text
Authorization Request
        │
        ▼
Jurisdiction
        │
        ├── Applicable Rules
        ├── Authority
        └── Restrictions
```

An authorization established in one jurisdiction should not automatically be assumed to apply in another jurisdiction.

Jurisdictional context should therefore remain explicit where relevant.

---

### 6.11 Emergency Context

An emergency may change the authorization context.

For example:

```text
Normal State
     │
     ▼
Normal Authorization
```

may become:

```text
Emergency State
     │
     ▼
Emergency Authorization
     │
     ├── Additional Authority
     ├── Additional Conditions
     └── Additional Restrictions
```

Emergency status should not automatically grant unrestricted authority.

Emergency authorization should remain subject to defined rules and conditions.

---

### 6.12 Multiple Subjects

Some Actions may require more than one authorized Entity.

For example:

```text
Entity A
    +
Entity B
    ↓
Required Authorization
    ↓
Action
```

The Authorization Context may therefore define:

* Required number of Entities
* Required Entity types
* Required authorization levels
* Required relationships
* Required approvals
* Required sequence of actions

This allows ADE-IF to represent multi-party authorization.

---

### 6.13 Authorization Context as a Composite

An Authorization Context may combine multiple contextual elements.

For example:

```text
Subject
   +
Action
   +
Resource
   +
Time
   +
Location
   +
State
   +
Purpose
   +
Authority
   +
Conditions
   ↓
Authorization Decision
```

This allows authorization to be evaluated against the circumstances that actually exist rather than against identity alone.

---

### 6.14 Context Can Change

Authorization Context may change over Time.

For example:

```text
09:00
Normal Operation
    ↓
Normal Authorization

10:30
Emergency Detected
    ↓
Emergency Authorization

11:15
Emergency Resolved
    ↓
Normal Authorization Restored
```

A change in context may therefore cause an authorization decision to change without changing the identity of the Entity.

---

### 6.15 Context and Authorization Decisions

The Authorization Context provides the information necessary to evaluate an authorization request.

Conceptually:

```text
Authorization Request
        │
        ▼
Authorization Context
        │
        ├── Subject
        ├── Action
        ├── Resource
        ├── Time
        ├── Location
        ├── State
        ├── Purpose
        ├── Authority
        └── Conditions
        │
        ▼
Authorization Decision
```

The resulting decision may be:

```text
Permitted
Denied
Restricted
Pending
Unknown
Unable to Determine
```

The distinction between these results should be maintained.

For example:

```text
Unable to Determine
       ≠
Denied
```

A system may be unable to evaluate an authorization request because required information or an authoritative source is unavailable.

---

### 6.16 Foundational Principle

ADE-IF treats Authorization Context as the collection of relevant circumstances used to determine whether an Entity may perform a defined Action.

Conceptually:

```text
Entity
   +
Action
   +
Context
   ↓
Authorization Decision
```

Authorization should therefore be evaluated against the context in which an Action is requested rather than treated as a permanent or universal property of an Entity.

The Authorization Context provides the foundation for representing time-dependent, location-dependent, state-dependent, purpose-dependent, jurisdiction-dependent, and emergency authorization.

---
