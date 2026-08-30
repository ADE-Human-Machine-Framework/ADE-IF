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
## 7. Delegation

A **Delegation** is the authorized assignment of one or more permissions, responsibilities, approvals, authorities, or authorization capabilities from one Entity to another Entity within a defined scope and context.

Delegation allows an Entity that possesses authority or authorization to permit another Entity to act on its behalf for specified purposes.

Delegation does not necessarily transfer the original authority itself.

Conceptually:

```text
Authority
    │
    ▼
Delegating Entity
    │
    │ delegates
    ▼
Receiving Entity
    │
    ▼
Delegated Authorization
```

Delegation should remain subject to the scope, conditions, and limitations established by the applicable authority.

---

### 7.1 Delegation and Authority

Authority and Delegation are related but distinct concepts.

For example:

```text
Authority
    │
    ▼
Entity A
```

may permit:

```text
Entity A
    │
    │ delegates
    ▼
Entity B
```

without transferring the original source of authority.

Conceptually:

```text
Authority
      │
      ▼
Entity A
      │
      └── Delegates Authorization
                  │
                  ▼
               Entity B
```

Entity B may receive authorization to perform defined Actions while Entity A remains the original holder of the authority.

---

### 7.2 Delegation Scope

A Delegation should define the scope within which delegated authorization may be exercised.

Scope may include:

* Specific Actions
* Categories of Actions
* Resources
* Systems
* Locations
* Jurisdictions
* Relationships
* Purposes
* Time periods
* Other defined boundaries

For example:

```text
Entity A
    │
    └── Delegates
            │
            ├── Action = Approve
            ├── Resource = System A
            └── Time = Defined Period
```

The delegation does not automatically apply outside the defined scope.

---

### 7.3 Delegation Conditions

A Delegation may include conditions.

Examples include:

* Time requirements
* Location requirements
* State requirements
* Emergency conditions
* Approval requirements
* Relationship requirements
* Authorization level requirements
* Other applicable conditions

Conceptually:

```text
Delegation
      │
      ├── Scope
      ├── Conditions
      └── Restrictions
```

Delegated authorization may therefore exist while remaining inactive until the required conditions are satisfied.

---

### 7.4 Delegation and Permission

A Delegation may grant one or more Permissions.

For example:

```text
Entity A
    │
    └── Delegates
            │
            ▼
       Permission
            │
            ├── Read
            ├── Approve
            └── Access
```

The delegated permissions should remain distinguishable from permissions independently granted to the receiving Entity.

---

### 7.5 Delegation and Restriction

Delegated authorization may remain subject to Restrictions established by the original authority or delegating Entity.

For example:

```text
Delegated Permission
        │
        ├── Approve Requests
        │
        └── Restriction
               └── Cannot Approve Own Requests
```

Delegation should not automatically remove existing restrictions.

Restrictions may continue to apply throughout the delegation lifecycle.

---

### 7.6 Delegation Duration

A Delegation may be temporary or ongoing.

Examples include:

```text
Temporary Delegation
      │
      └── Valid Until Defined Time
```

or:

```text
Ongoing Delegation
      │
      └── Remains Active Until Revoked
```

Delegation duration should be explicitly represented where relevant.

---

### 7.7 Delegation Status

A Delegation may have a lifecycle or status.

Possible states include:

```text
Pending
Active
Suspended
Expired
Revoked
Cancelled
Completed
```

For example:

```text
Delegation
      │
      ├── Status = Active
      ├── Valid From
      └── Valid Until
```

A Delegation that is no longer active should not be treated as providing valid authorization.

---

### 7.8 Delegation Chains

Some environments may permit delegated authorization to be further delegated.

Conceptually:

```text
Entity A
    │
    ▼
Entity B
    │
    ▼
Entity C
```

Such delegation chains may require explicit authorization.

For example:

```text
Entity A
      │
      └── May Delegate
                  │
                  ▼
               Entity B
```

while:

```text
Entity B
      │
      └── Further Delegation Prohibited
```

The ability to create delegation chains should therefore be governed by applicable authority and policy.

---

### 7.9 Delegation and Accountability

Delegation does not necessarily remove accountability.

For example:

```text
Authority Holder
       │
       └── Delegates
                 │
                 ▼
            Authorized Action
```

The applicable governance model may determine whether accountability remains with:

* The delegating Entity
* The receiving Entity
* Both Entities
* Other responsible parties

ADE-IF should therefore distinguish delegation from accountability.

---

### 7.10 Delegation and Human / Non-Human Entities

Delegation may occur between different Entity types.

Examples include:

```text
Human
   └── Delegates to Human
```

```text
Organization
   └── Delegates to Human
```

```text
Human
   └── Delegates to System
```

```text
Organization
   └── Delegates to Service
```

```text
System
   └── Delegates to Digital Agent
```

The semantic structure of delegation may remain consistent regardless of Entity classification.

---

### 7.11 Delegation and Multi-Party Authorization

Delegation may participate in multi-party authorization processes.

For example:

```text
Entity A
    +
Entity B
    ↓
Required Approval
```

where one or more approvals are provided through delegated authorization.

Conceptually:

```text
Delegation
      │
      ▼
Authorized Approval
      │
      ▼
Multi-Party Decision
```

Delegated participation should remain distinguishable from direct participation.

---

### 7.12 Delegation and Jurisdiction

Delegation may be affected by jurisdictional requirements.

For example:

```text
Jurisdiction A
      │
      └── Delegation Permitted
```

while:

```text
Jurisdiction B
      │
      └── Delegation Restricted
```

A delegation valid within one jurisdiction should not automatically be assumed valid within another.

---

### 7.13 Delegation and Emergency Context

Emergency conditions may affect delegation.

For example:

```text
Emergency State
       │
       ▼
Temporary Delegation
       │
       ▼
Emergency Authorization
```

Emergency delegation should remain subject to defined authority, scope, conditions, and accountability requirements.

The existence of an emergency should not automatically establish unrestricted delegation rights.

---

### 7.14 Delegation Is Not Identity

Delegation should not be interpreted as transferring identity.

For example:

```text
Entity A
      │
      └── Delegates Approval Authority
                  │
                  ▼
               Entity B
```

does not mean:

```text
Entity B
      =
Entity A
```

The receiving Entity remains a separate Entity acting under delegated authorization.

Identity and delegation should remain distinct concepts.

---

### 7.15 Foundational Principle

ADE-IF treats Delegation as the authorized assignment of permissions, responsibilities, approvals, or authorization capabilities from one Entity to another within a defined scope and context.

Conceptually:

```text
Authority
   +
Delegating Entity
   +
Receiving Entity
   +
Scope
   +
Conditions
   ↓
Delegated Authorization
```

Delegation should therefore enable authorized participation by another Entity without requiring transfer of identity, unrestricted authority, or permanent control.

Delegated authorization remains subject to applicable scope, restrictions, conditions, accountability requirements, and governance rules.

---
## 8. Override

An **Override** is an authorized Action that temporarily or permanently supersedes, suspends, modifies, or bypasses an existing Permission, Restriction, authorization condition, or authorization decision within a defined context.

An Override should not be interpreted as unrestricted authority.

An Override must itself be established through an applicable Authority, Authorization, or defined governance mechanism.

Conceptually:

```text
Existing Authorization
        │
        ├── Permission
        ├── Restriction
        └── Conditions
                │
                ▼
             Override
                │
                ▼
      Modified Authorization
                │
                ▼
             Action
```

An Override may be required when circumstances make the ordinary authorization conditions inappropriate or insufficient for the situation.

---

### 8.1 Override and Authorization

An Override is itself an authorization relationship.

For example:

```text
Entity
    │
    └── Authorization
            │
            └── Override
                    │
                    └── Restricted Action
```

The Entity exercising an Override must therefore possess the authority or authorization required to perform the Override.

The ability to perform an ordinary Action does not automatically establish the ability to override restrictions governing that Action.

Conceptually:

```text
Permission to Perform Action
          ≠
Permission to Override Restriction
```

---

### 8.2 Override Authority

An Override should identify the Authority under which the Override is permitted.

For example:

```text
Authority
    │
    ▼
Override Authorization
    │
    ├── Subject
    ├── Action
    ├── Scope
    └── Conditions
```

The Authority may originate from:

* Law or regulation
* Organizational governance
* Safety requirements
* Emergency procedures
* System governance
* Delegated authority
* Contractual arrangements
* Other recognized sources

The source of Override authority should remain distinguishable from the Entity exercising the Override.

---

### 8.3 Override Scope

An Override should define what is being overridden.

The scope may include:

* A Permission
* A Restriction
* An Authorization Condition
* An Authorization Decision
* A Policy
* A System Rule
* A Defined Action
* A Resource
* A Location
* A Time period
* A defined combination of these

For example:

```text
Override
    │
    ├── Target = Safety Restriction
    ├── Action = Shutdown
    ├── Resource = System A
    └── Duration = 10 Minutes
```

An Override should not automatically extend beyond its defined scope.

---

### 8.4 Override Conditions

An Override may require specific conditions before it can be exercised.

Examples include:

* Emergency status
* Failure of an automated process
* Safety condition
* System malfunction
* Required approval
* Required number of authorized Entities
* Defined authorization level
* Time condition
* Location condition
* State condition
* Other defined requirements

Conceptually:

```text
Override Request
       │
       ▼
Required Conditions
       │
   ┌───┴────┐
   ▼        ▼
Satisfied  Not Satisfied
   │        │
   ▼        ▼
Override   Override
Allowed    Not Allowed
```

The existence of an Override capability does not necessarily mean that the Override may be exercised at any time.

---

### 8.5 Override and Restriction

An Override may temporarily supersede a Restriction.

For example:

```text
Restriction
      │
      └── Action Prohibited
```

may become:

```text
Defined Override
      │
      ▼
Restriction Temporarily Superseded
      │
      ▼
Action Permitted
```

The original Restriction should not necessarily be considered deleted or invalid.

Instead, the Override may establish a temporary authorization condition under which the Restriction does not prevent the defined Action.

---

### 8.6 Temporary Override

An Override may be limited to a defined period.

For example:

```text
Override
    │
    ├── Valid From
    └── Valid Until
```

Conceptually:

```text
Normal Authorization
       │
       ▼
Override Activated
       │
       ▼
Temporary Authorization
       │
       ▼
Override Ends
       │
       ▼
Normal Authorization Restored
```

A temporary Override should cease to apply when its defined duration expires unless another valid authorization establishes otherwise.

---

### 8.7 Permanent Override

Some governance systems may permit a permanent or ongoing Override.

For example:

```text
Existing Rule
      │
      ▼
Authorized Override
      │
      ▼
New Rule / Authorization
```

A permanent Override should require an appropriate Authority and governance process.

A temporary operational Override should not automatically become permanent merely because it has been repeatedly exercised.

---

### 8.8 Override and Permission

An Override may modify how an existing Permission is exercised.

For example:

```text
Permission
    │
    └── Access System
             │
             ▼
        Restriction
             │
             └── Access Limited
```

An authorized Override may establish:

```text
Override
    │
    └── Temporary Expanded Access
```

The Override should define the additional scope rather than creating an assumption of unrestricted access.

---

### 8.9 Override and Delegation

Override authority may be delegated where the applicable Authority permits delegation.

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
Override Authorization
```

The delegation should identify whether Override authority is included within the delegated scope.

For example:

```text
Delegated Authority
    │
    ├── Start System
    ├── Stop System
    └── Override Restrictions
```

The ability to perform ordinary Actions does not automatically establish the ability to exercise an Override.

---

### 8.10 Override Restrictions

An Override may itself be subject to Restrictions.

For example:

```text
Override Authority
      │
      └── Restriction
             │
             ├── Maximum Duration
             ├── Required Approval
             └── Defined Resource
```

This establishes that an Override is not necessarily unrestricted.

Conceptually:

```text
Override
    +
Override Restrictions
    +
Override Conditions
    ↓
Effective Override
```

---

### 8.11 Override and Multiple Authorities

Some Overrides may require multiple authorized Entities.

For example:

```text
Human A
   +
Human B
   ↓
Required Approval
   ↓
Override Authorization
```

The Authorization Context may specify:

* Required number of Entities
* Required Entity types
* Required authorization levels
* Required roles
* Required relationships
* Required sequence of approvals

This allows ADE-IF to represent controlled Overrides for higher-risk Actions.

---

### 8.12 Override and Emergency Conditions

An emergency may provide a defined condition under which an Override becomes available.

For example:

```text
Normal Operation
      │
      ▼
Restriction Active
      │
      ▼
Emergency Detected
      │
      ▼
Override Conditions Evaluated
      │
      ▼
Authorized Override
      │
      ▼
Restricted Action Permitted
```

Emergency conditions should not automatically establish an Override.

The applicable emergency authorization rules must determine:

* Who may exercise the Override
* What may be overridden
* Under what conditions
* For how long
* What approvals are required
* What restrictions remain in effect
* What records must be maintained

---

### 8.13 Override and Safety

Safety-related Overrides require particular care.

An Override may be necessary to prevent a greater hazard, but an authorization to override one safety condition should not automatically establish authorization to disregard all safety requirements.

For example:

```text
Safety Restriction A
       │
       ▼
Override Authorized
       │
       ▼
Action Permitted
```

does not necessarily mean:

```text
All Safety Restrictions
       │
       ▼
Overridden
```

Overrides should therefore remain limited to the specific safety condition and Action for which authority has been established.

---

### 8.14 Override and System State

The ability to exercise an Override may depend upon the current State of a System or other Entity.

For example:

```text
System State = Normal
       │
       ▼
Override Not Available
```

while:

```text
System State = Emergency
       │
       ▼
Override Available
```

The State may therefore form part of the Authorization Context used to determine whether an Override is permitted.

---

### 8.15 Override and Time

Time may affect the validity of an Override.

For example:

```text
Override
    │
    ├── Valid From
    ├── Valid Until
    └── Maximum Duration
```

An Override may therefore be:

```text
Not Yet Active
Active
Expired
```

The passage of Time may automatically terminate an Override where the applicable authorization rules define such behavior.

Time-based Override should remain compatible with ADE-Core and ADE-HTF.

---

### 8.16 Override and Location

An Override may be limited to a defined Location.

For example:

```text
Override
    │
    ├── Action = Emergency Shutdown
    ├── Resource = Machine A
    └── Location = Facility A
```

The same Entity may possess Override authority at one Location without possessing it at another.

Location-based Override should remain compatible with ADE-Core and ADE-LF.

---

### 8.17 Override and Jurisdiction

An Override may be subject to jurisdictional requirements.

For example:

```text
Jurisdiction A
      │
      └── Override Permitted
```

while:

```text
Jurisdiction B
      │
      └── Override Restricted
```

An Override established under one jurisdiction should not automatically be assumed to have authority in another jurisdiction.

Jurisdiction should therefore remain explicit where it affects the validity of an Override.

---

### 8.18 Override and Authorization Decision

An Override may change the result of an Authorization Decision.

For example:

```text
Authorization Request
       │
       ▼
Normal Evaluation
       │
       ▼
Denied
       │
       ▼
Authorized Override
       │
       ▼
New Authorization Evaluation
       │
       ▼
Permitted
```

The original decision should remain distinguishable from the subsequent Override.

Conceptually:

```text
Original Decision
       +
Override
       ↓
Effective Decision
```

This allows systems to maintain a record of both the ordinary authorization state and the exceptional authorization state.

---

### 8.19 Override Does Not Change Identity

An Override does not change the identity of the Entity exercising it.

For example:

```text
Entity A
    │
    └── Exercises Override
```

does not mean:

```text
Entity A
    =
Authority
```

The Entity remains the same Entity.

The Override represents a defined authorization relationship established under an applicable Authority.

Identity and Override should therefore remain semantically separate.

---

### 8.20 Override Does Not Create General Authority

An Override for one Action does not automatically establish authority for unrelated Actions.

For example:

```text
Override Authority
    │
    └── Emergency Shutdown
```

does not automatically establish:

```text
Modify System
Delete System
Change Ownership
Transfer Resources
```

unless those Actions are explicitly included within the applicable authorization.

Override should therefore remain specific to its defined scope.

---

### 8.21 Override Record

Where an Override affects a significant Action, the system may need to maintain information describing the Override.

Possible information includes:

* Override identifier
* Subject Entity
* Authority
* Authorization source
* Target Permission or Restriction
* Action
* Resource
* Scope
* Conditions
* Reason
* Time
* Location
* Jurisdiction
* Status
* Approvals
* Delegation information
* Resulting Authorization Decision

Conceptually:

```text
Override Record
      │
      ├── Subject
      ├── Authority
      ├── Target
      ├── Action
      ├── Scope
      ├── Conditions
      ├── Time
      ├── Location
      ├── Approvals
      ├── Status
      └── Result
```

The exact data requirements should be defined by the applicable ADE specification or implementation.

---

### 8.22 Override Accountability

An Override should remain attributable to the Entity, Authority, or process responsible for establishing or exercising it.

For example:

```text
Authority
    │
    ▼
Override Authorization
    │
    ▼
Authorized Entity
    │
    ▼
Override Exercised
    │
    ▼
Action
```

Where appropriate, systems should be able to determine:

* Who authorized the Override
* Who exercised the Override
* What was overridden
* Why it was overridden
* When it occurred
* Under what conditions it occurred
* What Action resulted

Accountability requirements may vary according to the applicable governance environment.

---

### 8.23 Override Lifecycle

An Override may have a defined lifecycle.

For example:

```text
Requested
    ↓
Evaluated
    ↓
Authorized
    ↓
Active
    ↓
Completed / Expired / Revoked
```

Possible states include:

```text
Requested
Pending
Authorized
Active
Suspended
Completed
Expired
Revoked
Cancelled
Denied
```

The lifecycle state of an Override should remain distinguishable from the identity status of the Entity and from the status of the underlying Permission or Restriction.

---

### 8.24 Override Failure

An Override request may fail or may be unable to proceed.

Possible outcomes include:

```text
Override Authorized
Override Denied
Override Conditions Not Satisfied
Override Authority Unavailable
Override Information Unknown
Override Expired
Override Revoked
```

For example:

```text
Required Authority Unavailable
       ≠
Override Denied
```

The system should preserve the distinction between an Override that has been explicitly denied and one that cannot currently be evaluated.

---

### 8.25 Override and Auditability

Where appropriate, Overrides should support traceability.

A system may need to establish:

```text
Original Authorization
       │
       ▼
Restriction
       │
       ▼
Override Authority
       │
       ▼
Override Decision
       │
       ▼
Action
       │
       ▼
Result
```

This allows the system to distinguish normal authorization activity from exceptional authorization activity.

Audit requirements should be determined by the applicable governance, legal, safety, or operational context.

---

### 8.26 Foundational Principle

ADE-IF treats an Override as a defined authorization mechanism through which an authorized Entity may temporarily or otherwise supersede, suspend, modify, or bypass an existing Permission, Restriction, authorization condition, or authorization decision within a defined scope and context.

Conceptually:

```text
Existing Authorization
        +
Override Authority
        +
Defined Conditions
        +
Defined Scope
        ↓
Override
        ↓
Modified Authorization
        ↓
Permitted Action
```

An Override should therefore:

* Have an identifiable source of authority
* Have a defined scope
* Remain subject to applicable conditions
* Remain distinguishable from ordinary authorization
* Not automatically create unrestricted authority
* Not change the identity of the Entity exercising it
* Remain compatible with Delegation where applicable
* Support accountability where required
* Have a defined lifecycle where appropriate
* Preserve the distinction between normal and exceptional authorization

The purpose of representing Override explicitly is to allow ADE-IF to describe exceptional authorization without treating exceptions as undefined or unrestricted authority.

---
## 9. Emergency Authorization

**Emergency Authorization** defines the authorization conditions and authority that may apply when an Emergency Condition requires an Action that cannot be adequately addressed through normal authorization procedures.

Emergency Authorization allows ADE-IF to represent situations in which normal Permissions, Restrictions, approval requirements, or operational procedures may need to be modified, suspended, or overridden according to predefined authority and conditions.

Emergency Authorization does not automatically grant unrestricted authority.

An Emergency Condition establishes a context in which specific emergency authorization rules may become applicable.

Conceptually:

```text
Normal Conditions
       │
       ▼
Normal Authorization
       │
       ▼
Emergency Condition
       │
       ▼
Emergency Authorization Rules
       │
       ▼
Emergency Authorization
       │
       ▼
Permitted Emergency Action
```

Emergency Authorization should remain limited to the Actions, Resources, Entities, Locations, Time periods, and conditions for which authority has been established.

---

### 9.1 Emergency Condition

An **Emergency Condition** is a defined State or circumstance in which normal operational conditions are insufficient to address an immediate or significant risk, threat, failure, or other exceptional situation.

Examples may include:

* Threat to human safety
* Critical system failure
* Security incident
* Environmental hazard
* Loss of critical infrastructure
* Imminent operational failure
* Emergency maintenance requirement
* Other formally defined emergency conditions

Conceptually:

```text
Normal State
      │
      ▼
Emergency Condition Detected
      │
      ▼
Emergency Authorization Context
```

The definition of an Emergency Condition should be established by the applicable authority, policy, regulation, or operational framework.

---

### 9.2 Emergency Authorization and Normal Authorization

Emergency Authorization should remain distinguishable from normal authorization.

For example:

```text
Normal Authorization
    │
    └── Start Machine
```

may differ from:

```text
Emergency Authorization
    │
    └── Emergency Shutdown
```

An Entity authorized for normal operation is not automatically authorized to perform every emergency Action.

Similarly, an Entity with emergency authority should not automatically possess unrestricted authority during normal operation.

Conceptually:

```text
Normal Context
      ≠
Emergency Context
```

---

### 9.3 Emergency Authority

Emergency Authorization should identify the Authority under which emergency Actions may be performed.

For example:

```text
Emergency Authority
      │
      ├── Scope
      ├── Conditions
      ├── Authorized Entities
      └── Emergency Actions
```

Emergency Authority may originate from:

* Law or regulation
* Organizational governance
* Safety procedures
* System governance
* Emergency response procedures
* Delegated authority
* Other recognized sources

Emergency Authority should remain distinguishable from the Entity exercising the emergency authorization.

---

### 9.4 Emergency Authorization Scope

Emergency Authorization should define the scope of Actions that may be performed.

Scope may include:

* Specific Actions
* Specific Resources
* Specific Systems
* Specific Locations
* Specific Entity types
* Defined emergency conditions
* Defined Time periods
* Defined jurisdictions
* Other applicable boundaries

For example:

```text
Emergency Authorization
      │
      ├── Action = Emergency Shutdown
      ├── Resource = System A
      ├── Location = Facility A
      └── Condition = Critical Failure
```

Emergency authority should not automatically extend beyond the defined scope.

---

### 9.5 Emergency Authorization Conditions

Emergency Authorization may depend upon one or more conditions.

Examples include:

* Emergency declared
* Emergency detected
* Immediate danger
* System failure
* Required authority available
* Required number of authorized Entities
* Defined authorization level
* Required communication unavailable
* Defined Time period
* Defined Location
* Other applicable conditions

Conceptually:

```text
Emergency Request
       │
       ▼
Emergency Conditions
       │
   ┌───┴────┐
   ▼        ▼
Satisfied  Not Satisfied
   │        │
   ▼        ▼
Emergency  Emergency
Authorization  Authorization
Available      Not Available
```

The existence of an emergency process does not automatically establish that every emergency Action is authorized.

---

### 9.6 Emergency Authorization Levels

Different emergency Actions may require different levels of authority.

For example:

```text
Emergency Level 1
    │
    └── Limited Emergency Action

Emergency Level 2
    │
    └── Significant Emergency Action

Emergency Level 3
    │
    └── Critical Override Action
```

These levels are conceptual examples only.

The specific meanings, requirements, and governance of emergency authorization levels should be defined by the applicable organization, authority, or ADE specification.

An emergency authorization level should describe the scope of permitted emergency Actions.

It should not be interpreted as a measure of the value, identity certainty, capability, or general trustworthiness of an Entity.

---

### 9.7 Emergency Authorization and Override

Emergency Authorization may provide the authority required to exercise an Override.

For example:

```text
Emergency Condition
       │
       ▼
Emergency Authorization
       │
       ▼
Override Authority
       │
       ▼
Restriction Temporarily Superseded
       │
       ▼
Emergency Action
```

However, Emergency Authorization and Override remain distinct concepts.

Emergency Authorization describes the authorization applicable during an emergency.

Override describes the specific mechanism through which an existing Permission, Restriction, condition, or decision may be superseded or modified.

Conceptually:

```text
Emergency Authorization
        ≠
Override
```

An emergency authorization may exist without requiring an Override.

An Override may also exist outside an emergency context where explicitly authorized.

---

### 9.8 Emergency Authorization and Delegation

Emergency authority may be delegated where the applicable Authority permits delegation.

For example:

```text
Authority
    │
    ▼
Entity A
    │
    │ delegates emergency authority
    ▼
Entity B
    │
    ▼
Emergency Action
```

The delegation should establish:

* Scope
* Conditions
* Duration
* Restrictions
* Applicable Actions
* Accountability requirements

Delegation of emergency authority should not automatically create unrestricted emergency authority.

---

### 9.9 Emergency Authorization and Multiple Entities

Some emergency Actions may require multiple authorized Entities.

For example:

```text
Human A
    +
Human B
    ↓
Required Emergency Approval
    ↓
Emergency Authorization
    ↓
Critical Action
```

The Authorization Context may specify:

* Required number of Entities
* Required Entity types
* Required authorization levels
* Required roles
* Required relationships
* Required approval sequence

This allows ADE-IF to represent multi-party emergency authorization.

---

### 9.10 Emergency Authorization and Single-Entity Action

Some emergencies may require immediate action and may not allow time for multiple approvals.

For example:

```text
Emergency Detected
       │
       ▼
Immediate Threat
       │
       ▼
Authorized Emergency Operator
       │
       ▼
Immediate Action
```

The applicable emergency rules may therefore permit a single authorized Entity to perform a defined Action.

Such authority should remain limited to the circumstances and scope established by the applicable emergency policy.

The inability to obtain additional approval should not automatically create unrestricted authority.

---

### 9.11 Emergency Authorization and Safety

Emergency Authorization may permit Actions that would normally be restricted where necessary to address a defined emergency.

For example:

```text
Normal Operation
       │
       ▼
Safety Restriction
       │
       ▼
Action Prohibited
```

may become:

```text
Emergency Condition
       │
       ▼
Emergency Authorization
       │
       ▼
Defined Safety Override
       │
       ▼
Emergency Action
```

An emergency authorization to bypass one safety restriction should not automatically establish authority to disregard all safety requirements.

Emergency Actions should therefore remain limited to what is necessary and authorized for the defined emergency.

---

### 9.12 Emergency Authorization and Minimum Necessary Action

Emergency authorization should, where applicable, support the principle of performing only the Action necessary to address the emergency.

For example:

```text
Emergency
    │
    ▼
Required Action
    │
    ▼
Minimum Necessary Intervention
```

An authorization to stop a dangerous process does not automatically establish authorization to modify unrelated systems.

Conceptually:

```text
Emergency Need
      +
Defined Authority
      +
Minimum Necessary Action
      ↓
Emergency Authorization
```

The applicable emergency policy should determine the appropriate scope.

---

### 9.13 Emergency Authorization and Time

Emergency Authorization may be limited by Time.

For example:

```text
Emergency Authorization
      │
      ├── Activated
      ├── Valid From
      └── Valid Until
```

Emergency authority may therefore be:

```text
Not Yet Active
Active
Expired
```

An emergency authorization should normally cease to apply when its defined conditions or duration end unless another valid authorization establishes otherwise.

Time-based emergency authorization should remain compatible with ADE-Core and ADE-HTF.

---

### 9.14 Emergency Authorization and Location

Emergency Authorization may be limited to a defined Location.

For example:

```text
Emergency Authorization
      │
      ├── Action = Shutdown
      ├── Resource = System A
      └── Location = Facility A
```

The same Entity may therefore possess emergency authority at one Location without possessing the same authority elsewhere.

Location-based emergency authorization should remain compatible with ADE-Core and ADE-LF.

---

### 9.15 Emergency Authorization and State

Emergency Authorization may depend upon the State of an Entity, Object, System, or other ADE concept.

For example:

```text
System State = Normal
       │
       ▼
Normal Authorization
```

may become:

```text
System State = Emergency
       │
       ▼
Emergency Authorization Rules
```

When the State changes, the applicable authorization may also change.

Conceptually:

```text
State Change
      ↓
Authorization Context Change
      ↓
Authorization Decision Change
```

---

### 9.16 Emergency Authorization and Jurisdiction

Emergency Authorization may be subject to jurisdictional requirements.

For example:

```text
Jurisdiction A
      │
      └── Emergency Authority Defined
```

while:

```text
Jurisdiction B
      │
      └── Different Emergency Authority
```

An emergency authorization established under one jurisdiction should not automatically be assumed to have the same legal or operational effect in another jurisdiction.

Jurisdiction should therefore remain explicit where relevant.

---

### 9.17 Emergency Authorization and Information Availability

Emergency conditions may occur when one or more authoritative information sources are unavailable.

For example:

```text
Emergency
    │
    ▼
Authority Information Unavailable
    │
    ▼
Emergency Procedure
```

The applicable emergency rules may define whether an Entity may act using previously established authorization, local emergency procedures, fallback authority, or another defined mechanism.

However:

```text
Information Unavailable
       ≠
Authorization Automatically Granted
```

The distinction between unavailable information and valid emergency authorization should remain explicit.

---

### 9.18 Emergency Authorization and Authentication

Emergency procedures may require authentication where practical.

For example:

```text
Emergency Entity
       │
       ▼
Authentication
       │
       ▼
Emergency Authorization
       │
       ▼
Emergency Action
```

In circumstances where normal authentication mechanisms are unavailable, an emergency process may define alternative mechanisms.

Such mechanisms should be explicitly governed.

Failure of a normal authentication mechanism should not automatically establish emergency authority.

---

### 9.19 Emergency Authorization and Identity

Emergency Authorization does not change the identity of the Entity exercising the authorization.

For example:

```text
Entity A
    │
    ▼
Emergency Authorization
    │
    ▼
Emergency Action
```

does not mean:

```text
Entity A
    =
Emergency Authority
```

The Entity remains the same Entity.

Emergency Authorization represents a contextual authorization relationship associated with that Entity.

---

### 9.20 Emergency Authorization and Authorization Decision

An emergency condition may result in a different Authorization Decision from the decision that would apply during normal operation.

For example:

```text
Normal Context
      │
      ▼
Authorization Decision
      │
      └── Denied
```

may become:

```text
Emergency Context
      │
      ▼
Emergency Authorization Evaluation
      │
      └── Permitted
```

The original decision should remain distinguishable from the emergency decision.

Conceptually:

```text
Normal Authorization Decision
              +
Emergency Authorization Context
              ↓
Emergency Authorization Decision
```

This allows systems to preserve the distinction between normal and emergency authorization.

---

### 9.21 Emergency Authorization Outcomes

An Emergency Authorization evaluation may produce different outcomes.

Possible results include:

```text
Permitted
Denied
Restricted
Pending
Unknown
Unable to Determine
```

For example:

```text
Emergency Authorization
       │
       ├── Permitted
       ├── Restricted
       └── Denied
```

Where required information is unavailable:

```text
Unable to Determine
       ≠
Denied
```

The distinction should be preserved where the authorization system cannot establish whether an emergency Action is permitted.

---

### 9.22 Emergency Authorization Record

Where an emergency Action has significant operational, safety, legal, or governance consequences, the system may need to maintain an Emergency Authorization Record.

Possible information includes:

* Emergency authorization identifier
* Emergency condition
* Subject Entity
* Authority
* Authorization source
* Action
* Resource
* Scope
* Conditions
* Reason
* Time
* Location
* Jurisdiction
* Approvals
* Delegation information
* Override information
* Authorization decision
* Result
* Status

Conceptually:

```text
Emergency Authorization Record
        │
        ├── Emergency Condition
        ├── Subject
        ├── Authority
        ├── Action
        ├── Scope
        ├── Conditions
        ├── Time
        ├── Location
        ├── Approvals
        ├── Override
        ├── Status
        └── Result
```

The exact record requirements should be defined by the applicable governance or ADE specification.

---

### 9.23 Emergency Authorization Lifecycle

Emergency Authorization may have a defined lifecycle.

For example:

```text
Emergency Detected
       ↓
Emergency Declared
       ↓
Authorization Evaluated
       ↓
Authorization Granted
       ↓
Emergency Action
       ↓
Emergency Resolved
       ↓
Authorization Terminated
```

Possible states include:

```text
Detected
Declared
Pending
Authorized
Active
Suspended
Completed
Expired
Revoked
Cancelled
Denied
```

The lifecycle state should remain distinguishable from the identity status of the Entity and from the status of any underlying Permission or Restriction.

---

### 9.24 Emergency Resolution

When the emergency condition ends, emergency authorization should normally be terminated or returned to its defined inactive state.

For example:

```text
Emergency Condition
       │
       ▼
Emergency Authorization
       │
       ▼
Emergency Action
       │
       ▼
Emergency Resolved
       │
       ▼
Emergency Authorization Ends
       │
       ▼
Normal Authorization Restored
```

Termination of Emergency Authorization should not automatically modify the underlying identity, authority, or normal permissions of the Entity.

---

### 9.25 Emergency Authorization Accountability

Emergency Actions should remain attributable to the Entities and authorities responsible for establishing and exercising emergency authorization where appropriate.

A system may need to determine:

* Who declared the emergency
* Who established the emergency authority
* Who received the authorization
* Who exercised the authorization
* What Action was performed
* What was overridden
* When the Action occurred
* Where the Action occurred
* Under what conditions the Action occurred
* What result occurred

Accountability requirements should be determined by the applicable governance, legal, safety, and operational environment.

---

### 9.26 Emergency Authorization and Auditability

Emergency Actions may require enhanced traceability because they can involve exceptional authority.

Conceptually:

```text
Emergency Condition
       │
       ▼
Emergency Authority
       │
       ▼
Authorization Decision
       │
       ▼
Emergency Action
       │
       ▼
Result
```

Where appropriate, systems should preserve enough information to distinguish:

```text
Normal Action
       ≠
Emergency Action
```

and:

```text
Normal Authorization
       ≠
Emergency Authorization
```

Audit requirements should remain appropriate to the sensitivity and consequences of the Action.

---

### 9.27 Emergency Authorization Does Not Create Permanent Authority

Emergency Authorization should not automatically create permanent authority.

For example:

```text
Emergency Authorization
       │
       ▼
Temporary Emergency Permission
```

does not necessarily establish:

```text
Permanent Authorization
```

The end of the emergency should not automatically result in permanent expansion of the Entity's normal authority or permissions.

---

### 9.28 Emergency Authorization Does Not Change Entity Classification

Emergency Authorization does not change the classification of an Entity.

For example:

```text
Human
   │
   └── Emergency Authorization
```

does not change the Entity into an Authority as an inherent identity characteristic.

Similarly:

```text
System
   │
   └── Emergency Authorization
```

does not automatically establish that the System possesses unrestricted authority.

Entity classification and emergency authorization remain separate semantic concepts.

---

### 9.29 Foundational Principle

ADE-IF treats Emergency Authorization as a contextual authorization mechanism that permits defined Actions under defined emergency conditions and authority.

Conceptually:

```text
Emergency Condition
        +
Emergency Authority
        +
Subject Entity
        +
Defined Action
        +
Defined Scope
        +
Defined Conditions
        ↓
Emergency Authorization
        ↓
Emergency Action
```

Emergency Authorization should therefore:

* Be based on a defined Emergency Condition
* Identify the applicable Authority
* Identify the authorized Entity or Entities
* Define the permitted Action
* Define the applicable Scope
* Remain subject to Conditions and Restrictions
* Support Override where explicitly authorized
* Support Delegation where explicitly authorized
* Support single-Entity or multi-Entity authorization where applicable
* Remain limited in Time and Location where required
* Preserve jurisdictional requirements
* Maintain the distinction between emergency and normal authorization
* Support accountability and traceability where required
* Terminate or change state when the emergency condition ends

Emergency conditions should therefore provide a defined change in Authorization Context rather than becoming a general exception to the authorization model.

## 10. Emergency Authority

**Emergency Authority** represents authority that may be exercised under defined emergency conditions when normal authorization procedures are insufficient, unavailable, or inappropriate for the circumstances.

Emergency Authority does not represent unrestricted authority.

It should be explicitly defined by the applicable authority, policy, governance framework, or authorization model and should remain subject to the conditions under which it may be exercised.

Conceptually:

```text
Normal Conditions
       │
       ▼
Normal Authorization
       │
       ▼
Emergency Condition
       │
       ▼
Emergency Authority
       │
       ▼
Emergency Authorization
       │
       ▼
Defined Emergency Action
```

### 10.1 Emergency Condition

An **Emergency Condition** identifies a state in which emergency authorization procedures may become applicable.

Examples may include:

* Threat to human life
* Safety-critical failure
* Security incident
* System failure
* Environmental danger
* Loss of normal control
* Imminent operational hazard
* Other formally defined emergency conditions

An emergency condition should be established according to applicable rules or authority.

The existence of an unusual or unexpected event does not automatically establish Emergency Authority unless the applicable framework defines it as such.

---

### 10.2 Emergency Authority Scope

Emergency Authority should define the scope within which it may be exercised.

The scope may include:

* Authorized Entity
* Action
* Resource
* Location
* Time
* Emergency condition
* Purpose
* Required approvals
* Applicable restrictions
* Reporting requirements

Conceptually:

```text
Emergency Authority
    │
    ├── Subject
    ├── Action
    ├── Resource
    ├── Condition
    ├── Scope
    ├── Time
    └── Restrictions
```

Emergency Authority should therefore remain limited to the circumstances for which it was established.

---

### 10.3 Emergency Authorization

An Emergency Authorization is an authorization decision made under an Emergency Context.

For example:

```text
Emergency Condition
       │
       ▼
Emergency Authority
       │
       ▼
Emergency Authorization
       │
       ▼
Override / Pause / Cancel
```

Emergency Authorization may permit Actions that would normally be restricted.

However, the authorization should remain subject to the defined emergency rules.

---

### 10.4 Emergency Override

An emergency may require an authorized Entity to temporarily override an ordinary restriction.

For example:

```text
Normal Operation
       │
       ▼
Restriction
       │
       └── Action Prohibited

Emergency Condition
       │
       ▼
Emergency Authority
       │
       ▼
Emergency Authorization
       │
       ▼
Temporary Override
```

An emergency override should identify:

* The restriction being overridden
* The Action being authorized
* The Entity exercising the authority
* The emergency condition
* The duration of the override
* Any additional conditions
* Any required recording or reporting

An emergency override should not automatically remove unrelated restrictions.

---

### 10.5 Multiple Human Authorization

Some emergency Actions may require multiple authorized humans.

For example:

```text
Human A
   │
   └── Authorization Level 3
             +
Human B
   │
   └── Authorization Level 3
             │
             ▼
      Required Approval
             │
             ▼
      Emergency Action
```

The applicable authorization policy may require:

* Two or more authorized humans
* Specific authorization levels
* Different organizational roles
* Independent approval
* A defined approval sequence

This allows high-risk emergency Actions to require multiple authorities rather than relying upon a single Entity.

---

### 10.6 Emergency Authority and Automation

Automated systems may participate in emergency processes.

For example:

```text
System
   │
   ├── Detect Emergency
   │
   ▼
Emergency State
   │
   ▼
Defined Emergency Action
```

An automated system may be authorized to perform predefined emergency Actions without requiring human intervention where such authority has been established.

However, automated capability should not itself be interpreted as Emergency Authority.

Conceptually:

```text
Automation Capability
        ≠
Emergency Authority
        ≠
Emergency Authorization
```

Each concept should remain distinguishable.

---

### 10.7 Emergency Authority and Human Intervention

An emergency system may require designated human intervention.

For example:

```text
Automated System
       │
       ▼
Emergency Detected
       │
       ▼
Automatic Protective Action
       │
       ▼
Human Authority
       │
       ├── Continue
       ├── Modify
       ├── Pause
       └── Override
```

The authority to intervene should be explicitly defined.

A human being present within a system does not automatically establish emergency authority.

---

### 10.8 Emergency Duration

Emergency Authority may be limited to a defined period.

For example:

```text
Emergency Begins
       │
       ▼
Emergency Authority Active
       │
       ▼
Emergency Resolved
       │
       ▼
Emergency Authority Ends
```

The end of an emergency should cause emergency-specific authorization to expire, unless another authorization mechanism establishes continued authority.

This prevents emergency permissions from unintentionally becoming permanent permissions.

---

### 10.9 Emergency Restrictions

Emergency Authority may remain subject to restrictions.

For example:

```text
Emergency Authority
       │
       ├── Authorized Action
       │
       ├── Time Limit
       │
       ├── Geographic Limit
       │
       ├── Resource Limit
       │
       └── Safety Requirements
```

Emergency conditions may modify some restrictions without eliminating all restrictions.

---

### 10.10 Emergency Recording and Accountability

Emergency Actions may require additional recording or accountability.

Depending on the applicable governance model, information may include:

* Emergency condition
* Acting Entity
* Authority source
* Authorization decision
* Action performed
* Time
* Location
* Resources affected
* Restrictions overridden
* Other required information

The specific recording requirements should be established by the applicable authority or future ADE specification.

---

### 10.11 Emergency Authority Does Not Equal General Authority

Emergency Authority should remain distinct from general authority.

For example:

```text
Emergency Authority
    │
    └── Authorized to Override Machine Safety Lock
```

does not necessarily mean:

```text
Authorized to Modify All Safety Systems
```

Emergency Authority should therefore remain:

* Contextual
* Purpose-bound
* Scope-bound
* Time-bound where applicable
* Subject to defined conditions

---

### 10.12 Foundational Principle

ADE-IF treats Emergency Authority as a defined form of authority that may become applicable under formally recognized emergency conditions.

Conceptually:

```text
Emergency Condition
       +
Emergency Authority
       +
Authorization Context
       +
Applicable Conditions
       ↓
Emergency Authorization
       ↓
Defined Emergency Action
```

Emergency Authority should provide a controlled mechanism for responding to exceptional circumstances without becoming an unrestricted or permanent source of authority.

---
## 11. Authorization Conditions

**Authorization Conditions** define the requirements that must be satisfied before an Authorization or Permission may be exercised.

Conditions provide a mechanism for representing circumstances that affect whether an otherwise valid authorization may be used.

Conceptually:

```text
Authorization
      │
      +
Conditions
      │
      ▼
Authorization Evaluation
      │
      ▼
Permitted / Restricted / Denied / Unable to Determine
```

Authorization Conditions may be based on:

* Time
* Location
* State
* Purpose
* Identity
* Authentication
* Relationship
* Jurisdiction
* Authority
* Required approvals
* Required number of Entities
* Emergency status
* Resource availability
* Safety requirements
* Other defined requirements

---

### 11.1 Condition and Authorization

A condition does not necessarily create an authorization.

Instead, a condition establishes a requirement that may determine whether an existing authorization can be exercised.

For example:

```text
Permission
    │
    └── Start Machine
            │
            ▼
       Safety Condition
            │
       ┌────┴────┐
       ▼         ▼
   Satisfied   Not Satisfied
       │         │
       ▼         ▼
    Permitted  Restricted
```

The existence of the Permission alone is therefore insufficient when required conditions have not been satisfied.

---

### 11.2 Conditional Authorization

An authorization may be established with conditions attached to it.

For example:

```text
Authorization
    │
    ├── Subject = Operator A
    ├── Action = Start
    ├── Resource = Machine A
    └── Condition = Safety Check Complete
```

The authorization may therefore become effective only when the required condition is satisfied.

---

### 11.3 Time Conditions

Authorization may depend upon a specific time or time interval.

For example:

```text
Authorization
    │
    ├── Action = Access
    └── Time = 09:00–17:00
```

The authorization may be:

```text
09:00–17:00
    └── Permitted

17:00–09:00
    └── Restricted
```

Time conditions should remain compatible with ADE-Core and ADE-HTF.

---

### 11.4 Location Conditions

Authorization may depend upon the Location in which an Action is performed.

For example:

```text
Authorization
    │
    ├── Action = Operate
    ├── Resource = Machine A
    └── Location = Facility A
```

The same authorization may not apply at another Location.

Location conditions should remain compatible with ADE-Core and ADE-LF.

---

### 11.5 State Conditions

Authorization may depend upon the State of an Entity, Resource, System, or other relevant ADE concept.

For example:

```text
Machine State = Operational
        │
        ▼
Start Authorization
        │
        ▼
Permitted
```

Where:

```text
Machine State = Maintenance
        │
        ▼
Start Authorization
        │
        ▼
Restricted
```

A change in State may therefore change the outcome of an authorization decision without changing the identity of the Entity.

---

### 11.6 Purpose Conditions

An authorization may be limited to a defined Purpose.

For example:

```text
Authorization
    │
    ├── Action = Access Information
    └── Purpose = Service Delivery
```

The same access may not be authorized for an unrelated purpose.

Conceptually:

```text
Defined Purpose
      │
      ▼
Authorization
      │
      ├── Purpose Matches
      │      └── Permitted
      │
      └── Purpose Does Not Match
             └── Restricted
```

Purpose conditions support purpose-bound authorization and minimum necessary disclosure.

---

### 11.7 Identity and Authentication Conditions

An authorization may require that an Entity be associated with a defined identity or satisfy an authentication requirement.

For example:

```text
Authorization
      │
      ├── Subject = Entity A
      └── Condition = Authentication Required
```

Authentication may establish that an Entity has successfully demonstrated control of an applicable authentication factor or mechanism.

Authentication should not itself be treated as authorization.

Conceptually:

```text
Identity
    +
Authentication
    +
Authorization Conditions
    ↓
Authorization Decision
```

---

### 11.8 Relationship Conditions

An authorization may depend upon an established Relationship.

For example:

```text
Entity A
    │
    └── assigned to ──> Machine A
```

A policy may establish:

```text
Relationship Confirmed
       +
Required Authorization
       ↓
Action Permitted
```

A Relationship should not automatically be interpreted as authorization.

Instead, it may satisfy one condition contributing to an authorization decision.

---

### 11.9 Jurisdiction Conditions

Authorization may depend upon applicable jurisdictional requirements.

For example:

```text
Authorization Request
       │
       ▼
Jurisdiction
       │
       ├── Applicable Authority
       ├── Applicable Rules
       └── Applicable Restrictions
       │
       ▼
Authorization Evaluation
```

An authorization established under one jurisdiction should not automatically be assumed to satisfy the requirements of another jurisdiction.

Jurisdictional conditions may affect:

* Access
* Disclosure
* Processing
* Transfer
* Identity verification
* Credential use
* Authorization
* Delegation

---

### 11.10 Required Number of Entities

Some Actions may require multiple authorized Entities.

For example:

```text
Authorization Condition
       │
       └── Required Entities = 2
                    │
             ┌──────┴──────┐
             ▼             ▼
          Entity A      Entity B
             │             │
             └──────┬──────┘
                    ▼
             Authorization
                    │
                    ▼
                  Action
```

The condition may additionally require specific Entity types, roles, authorization levels, or independent approvals.

---

### 11.11 Sequence Conditions

Some authorization processes may require Actions to occur in a defined sequence.

For example:

```text
Step 1
Identity Verified
    │
    ▼
Step 2
Authorization Approved
    │
    ▼
Step 3
Safety Check Completed
    │
    ▼
Step 4
Action Permitted
```

An Action may therefore remain restricted until preceding conditions have been satisfied.

The sequence itself may form part of the Authorization Context.

---

### 11.12 Emergency Conditions

Emergency conditions may alter normal authorization requirements.

For example:

```text
Normal Condition
      │
      ▼
Normal Authorization Rules
```

may become:

```text
Emergency Condition
      │
      ▼
Emergency Authorization Rules
      │
      ├── Additional Authority
      ├── Additional Conditions
      └── Modified Restrictions
```

Emergency conditions should not automatically establish unrestricted authorization.

They should activate only the emergency mechanisms defined by the applicable authority or policy.

---

### 11.13 Safety Conditions

Safety conditions may be required before an Action can be authorized or executed.

For example:

```text
Start Machine
      │
      ▼
Safety Conditions
      │
      ├── Area Clear
      ├── Guards Closed
      ├── Maintenance Complete
      └── Safety System Active
      │
      ▼
Authorization Evaluation
```

Failure of a required safety condition may result in:

```text
Restricted
```

or:

```text
Denied
```

depending upon the applicable authorization policy.

---

### 11.14 Resource Conditions

Authorization may depend upon the availability or state of a Resource.

For example:

```text
Authorization
      │
      └── Action = Allocate Resource
                    │
                    ▼
             Resource Available?
                    │
              ┌─────┴─────┐
              ▼           ▼
             Yes          No
              │           │
              ▼           ▼
          Permitted    Restricted
```

A valid authorization does not necessarily imply that the required Resource is available.

---

### 11.15 Conditions May Be Combined

Multiple conditions may apply simultaneously.

For example:

```text
Authorization Request
        │
        ├── Identity Verified
        ├── Authentication Valid
        ├── Time Within Allowed Period
        ├── Location Permitted
        ├── Required Relationship Exists
        ├── Safety Requirements Satisfied
        └── Required Approval Obtained
        │
        ▼
Authorization Decision
```

The applicable policy should determine whether all conditions are required or whether alternative conditions may satisfy the authorization requirement.

---

### 11.16 Condition Failure

Failure to satisfy a condition should remain distinguishable from other authorization outcomes.

For example:

```text
Condition Failed
      ≠
Identity Invalid
      ≠
Authorization Revoked
      ≠
Authority Unavailable
```

A system should preserve the semantic reason for an authorization outcome where disclosure of that reason is appropriate.

---

### 11.17 Condition Unknown

A required condition may be unknown because the information necessary to evaluate it is unavailable.

For example:

```text
Required Condition
      │
      ▼
Information Source
      │
      └── Unavailable
             │
             ▼
      Condition Unknown
             │
             ▼
     Unable to Determine
```

Unknown should not automatically be interpreted as false.

The applicable authorization policy should determine whether an unknown condition results in:

* Permitted
* Denied
* Restricted
* Pending
* Unable to Determine

---

### 11.18 Condition Lifecycle

Authorization Conditions may have their own lifecycle.

Possible states include:

```text
Pending
Active
Satisfied
Unsatisfied
Suspended
Expired
Revoked
Cancelled
Unknown
```

The applicable state should be evaluated within the Authorization Context.

---

### 11.19 Conditions and Delegation

Delegated authorization may inherit or introduce additional conditions.

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
Delegated Authorization
    │
    ├── Original Conditions
    └── Delegation Conditions
```

A delegation should not automatically remove conditions imposed by the original authority.

Additional conditions may make delegated authorization narrower than the original authorization.

---

### 11.20 Conditions and Override

An override may change which conditions apply, but the override itself should have defined conditions.

For example:

```text
Normal Condition
       │
       ▼
Action Restricted
       │
       ▼
Emergency Condition
       │
       ▼
Override Authorization
       │
       ▼
Defined Action
```

The override may itself require:

* Emergency status
* Authorized Entity
* Required authorization level
* Multiple approvals
* Time limitation
* Defined scope
* Recording or reporting

---

### 11.21 Conditions and Authorization Decisions

Authorization Conditions contribute to the final Authorization Decision.

Conceptually:

```text
Subject
   +
Action
   +
Context
   +
Conditions
   +
Authority
   +
Permissions
   +
Restrictions
   ↓
Authorization Evaluation
   ↓
Authorization Decision
```

The decision may be:

```text
Permitted
Denied
Restricted
Pending
Unknown
Unable to Determine
```

The applicable policy should define how conditions are evaluated and how conflicting conditions are resolved.

---

### 11.22 Foundational Principle

ADE-IF treats Authorization Conditions as explicit requirements that determine when and under what circumstances an authorization may be exercised.

Conceptually:

```text
Authorization
      +
Conditions
      +
Context
      ↓
Authorization Evaluation
      ↓
Authorization Decision
```

Conditions allow ADE-IF to represent authorization that depends upon time, location, state, purpose, jurisdiction, relationships, safety, emergency circumstances, multiple authorities, and other defined requirements.

Authorization Conditions should remain distinguishable from identity, authority, permission, restriction, capability, and successful execution of an Action.

---
## 12. Authorization Decisions

An **Authorization Decision** represents the determined outcome of evaluating whether an Entity is permitted to perform a defined Action within a particular Authorization Context.

The Authorization Decision is the result of evaluating applicable:

* Identity
* Authentication
* Authority
* Permissions
* Restrictions
* Conditions
* Context
* Policies
* Relationships
* Time
* Location
* State
* Purpose
* Jurisdiction
* Emergency conditions
* Other applicable requirements

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
        ├── Authority
        ├── Permission
        ├── Restriction
        ├── Conditions
        ├── Time
        ├── Location
        ├── State
        └── Purpose
        │
        ▼
Authorization Evaluation
        │
        ▼
Authorization Decision
```

An Authorization Decision should describe the outcome of the evaluation rather than becoming an inherent property of the Entity.

---

### 12.1 Decision Outcomes

An Authorization Decision may produce different outcomes.

Conceptual outcomes include:

```text
Permitted
Denied
Restricted
Pending
Unknown
Unable to Determine
```

The specific vocabulary and semantics should be defined by the applicable ADE specification or authorization policy.

These outcomes should remain semantically distinguishable.

---

### 12.2 Permitted

**Permitted** indicates that the applicable authorization requirements have been satisfied and the requested Action is authorized within the evaluated context.

For example:

```text
Subject = Operator A
Action = Start Machine A
Context = Facility A
Conditions = Satisfied
        │
        ▼
Authorization Decision
        │
        ▼
Permitted
```

Permitted does not necessarily mean that the Action will successfully execute.

The system may still prevent execution because of technical, operational, safety, or other conditions.

---

### 12.3 Denied

**Denied** indicates that the applicable authorization rules do not permit the requested Action within the evaluated context.

For example:

```text
Subject = Operator A
Action = Modify Safety Configuration
        │
        ▼
Authorization Evaluation
        │
        ▼
Denied
```

A Denied decision may result from:

* Insufficient authority
* Missing permission
* Failed condition
* Active restriction
* Invalid relationship
* Jurisdictional limitation
* Expired authorization
* Other applicable policy

Denied should describe the authorization outcome rather than making a general statement about the Entity.

---

### 12.4 Restricted

**Restricted** indicates that an Action may be subject to limitations or that only a constrained form of the Action is permitted.

For example:

```text
Permission
    │
    └── Access System
            │
            ▼
       Restriction
            │
            └── Read Only
                    │
                    ▼
               Restricted
```

A Restricted decision may therefore permit a narrower Action than originally requested.

For example:

```text
Requested:
Modify Record

Decision:
Restricted

Permitted:
Read Record
```

The exact meaning of Restricted should be defined by the applicable authorization policy.

---

### 12.5 Pending

**Pending** indicates that an authorization decision has not yet reached a final state.

For example:

```text
Authorization Request
        │
        ▼
Additional Approval Required
        │
        ▼
Pending
```

Pending may occur when:

* Additional approval is required
* A required condition has not yet been satisfied
* A delegated authority is awaiting confirmation
* A required verification process is incomplete
* A required Entity has not yet approved the Action
* An external authority has not yet responded

Pending should not automatically be interpreted as Denied.

---

### 12.6 Unknown

**Unknown** indicates that the authorization state cannot currently be established from the available information.

For example:

```text
Authorization Request
        │
        ▼
Required Information
        │
        └── Unknown
                │
                ▼
             Unknown
```

Unknown may occur when the applicable information exists but its state cannot currently be established.

Unknown should remain distinguishable from Denied.

---

### 12.7 Unable to Determine

**Unable to Determine** indicates that the authorization decision cannot be evaluated because required information, authority, system functionality, or another necessary component is unavailable.

For example:

```text
Authorization Request
        │
        ▼
Required Authority
        │
        └── Unavailable
                │
                ▼
       Unable to Determine
```

Conceptually:

```text
Unable to Determine
        ≠
Denied
```

A system should not necessarily interpret the inability to obtain a decision as evidence that the requested Action is unauthorized.

The applicable policy may nevertheless define a safe default response.

---

### 12.8 Decision Basis

An Authorization Decision should be based upon identifiable elements of the Authorization Context.

Conceptually:

```text
Authorization Decision
        │
        ├── Subject
        ├── Action
        ├── Resource
        ├── Authority
        ├── Permission
        ├── Restrictions
        ├── Conditions
        ├── Context
        └── Policy
```

Where appropriate, the decision may include a reference to the source or policy used to reach the decision.

Detailed decision evidence requirements should be defined by the applicable ADE specification.

---

### 12.9 Decision and Identity

An Authorization Decision should not change the identity of the Subject.

For example:

```text
Identity
    │
    ▼
Entity A
    │
    ├── Action A → Permitted
    │
    ├── Action B → Denied
    │
    └── Action C → Pending
```

The Entity remains the same while the authorization outcome changes according to the Action and Context.

---

### 12.10 Decision and Authentication

Authentication may contribute to an Authorization Decision but should not be treated as the decision itself.

For example:

```text
Identity
    │
    ▼
Authentication
    │
    ▼
Authorization Evaluation
    │
    ▼
Authorization Decision
```

Successful authentication does not automatically establish authorization.

Similarly, an authorization decision may depend upon information other than authentication.

---

### 12.11 Decision and Authority

Authority may establish the basis upon which authorization is granted or denied.

For example:

```text
Authority
    │
    ▼
Policy / Rule
    │
    ▼
Authorization Evaluation
    │
    ▼
Authorization Decision
```

The Authority itself should remain distinguishable from the resulting decision.

For example:

```text
Authority
    ≠
Authorization Decision
```

---

### 12.12 Decision and Permission

A Permission may provide an allowed capability that contributes to an Authorization Decision.

For example:

```text
Permission
    │
    └── Start Machine
            │
            ▼
      Authorization Evaluation
            │
            ▼
         Permitted
```

However, a Permission may be limited by Restrictions or Conditions.

Therefore:

```text
Permission
      +
Restrictions
      +
Conditions
      +
Context
      ↓
Authorization Decision
```

---

### 12.13 Decision and Restriction

A Restriction may prevent or limit an Action even when a Permission exists.

For example:

```text
Permission
    │
    └── Operate Machine
            │
            ▼
       Restriction
            │
            └── Maintenance State
                    │
                    ▼
                Restricted
```

Restrictions should therefore be considered during authorization evaluation.

---

### 12.14 Decision and Conditions

Authorization Conditions may determine whether an authorization can be exercised.

For example:

```text
Authorization
      │
      ├── Permission = Override
      │
      └── Condition = Emergency
                    │
                    ▼
             Condition Check
                    │
             ┌──────┴──────┐
             ▼             ▼
          Satisfied      Failed
             │             │
             ▼             ▼
         Permitted       Denied
```

The applicable policy should determine how condition failures affect the final decision.

---

### 12.15 Multi-Party Decisions

An Authorization Decision may require approval from multiple Entities.

For example:

```text
Entity A
    │
    └── Approval
          +
Entity B
    │
    └── Approval
          │
          ▼
    Required Approvals
          │
          ▼
Authorization Decision
```

The authorization policy may require:

* A minimum number of approvals
* Specific authorization levels
* Specific Entity types
* Independent approvals
* A defined approval sequence

The decision should therefore be capable of representing multi-party authorization.

---

### 12.16 Emergency Decisions

An Authorization Decision may be made within an Emergency Context.

For example:

```text
Emergency Condition
        │
        ▼
Emergency Authority
        │
        ▼
Emergency Authorization Evaluation
        │
        ▼
Authorization Decision
        │
        ├── Permitted
        ├── Restricted
        └── Denied
```

Emergency status should remain part of the Authorization Context.

An emergency decision should not automatically become a permanent authorization after the emergency ends.

---

### 12.17 Time-Dependent Decisions

Authorization Decisions may change over Time.

For example:

```text
09:00
Authorization = Permitted

17:00
Authorization = Restricted
```

The change may result from:

* Expiration
* Activation of a restriction
* Change in policy
* Change in State
* Change in Location
* Change in Emergency status
* Other contextual changes

A previous decision should therefore not automatically be interpreted as a current decision.

---

### 12.18 Location-Dependent Decisions

An Authorization Decision may depend upon Location.

For example:

```text
Facility A
    │
    └── Operate Machine A
            └── Permitted

Facility B
    │
    └── Operate Machine A
            └── Denied
```

The Entity may remain the same while the Location changes the authorization outcome.

---

### 12.19 State-Dependent Decisions

A change in State may change an Authorization Decision.

For example:

```text
Machine State = Operational
        │
        ▼
Start Action
        │
        ▼
Permitted
```

while:

```text
Machine State = Maintenance
        │
        ▼
Start Action
        │
        ▼
Restricted
```

The change in decision does not necessarily indicate a change in identity or authority.

---

### 12.20 Purpose-Dependent Decisions

An Authorization Decision may depend upon the Purpose of an Action.

For example:

```text
Purpose = Service Delivery
        │
        ▼
Access Information
        │
        ▼
Permitted
```

while:

```text
Purpose = Unrelated Activity
        │
        ▼
Access Information
        │
        ▼
Denied
```

Purpose-bound decisions support data minimization and contextual authorization.

---

### 12.21 Decision Changes

An Authorization Decision may change when the underlying Authorization Context changes.

Conceptually:

```text
Authorization Context
        │
        ▼
Decision A
        │
        ▼
Context Changes
        │
        ▼
Decision B
```

The change may result from:

* Time
* Location
* State
* Policy
* Permission
* Restriction
* Authority
* Condition
* Emergency status
* Relationship
* Revocation
* Expiration

A changed decision should not necessarily be interpreted as an error or contradiction.

It may represent the correct response to a changed context.

---

### 12.22 Decision Lifecycle

Authorization Decisions may have a lifecycle.

Possible states include:

```text
Requested
Evaluating
Pending
Determined
Active
Expired
Superseded
Revoked
Cancelled
```

The applicable lifecycle vocabulary should be defined by the relevant ADE specification.

A decision lifecycle should remain distinguishable from the lifecycle of the underlying Entity or identity.

---

### 12.23 Decision Integrity

Where authorization decisions are used for consequential Actions, systems may require mechanisms to establish that the decision has not been altered improperly.

Such mechanisms may include:

* Authority references
* Policy references
* Decision identifiers
* Time information
* Source information
* Integrity mechanisms
* Audit information
* Other applicable controls

ADE-IF does not require a particular technical mechanism for establishing decision integrity.

Specific mechanisms should remain implementation- and technology-independent unless defined by a future ADE specification.

---

### 12.24 Decision Explanation

Where appropriate, an Authorization Decision may provide a reason or reference explaining the basis of the decision.

For example:

```text
Decision = Denied
Reason = Required Authorization Level Not Present
```

or:

```text
Decision = Unable to Determine
Reason = Authoritative Source Unavailable
```

The amount of information disclosed with a decision should itself remain subject to applicable privacy, security, and authorization requirements.

A decision explanation should not unnecessarily disclose protected information.

---

### 12.25 Decision Is Not Action Execution

An Authorization Decision establishes whether an Action is permitted within the evaluated context.

It does not establish that the Action was actually performed.

For example:

```text
Authorization Decision
        │
        ▼
Permitted
        │
        ▼
Action Requested
        │
        ▼
Action Execution
        │
        ├── Successful
        └── Failed
```

Therefore:

```text
Authorization
      ≠
Execution
```

An Action may be authorized but never executed.

Similarly, an Action may be attempted without authorization and therefore represent an unauthorized attempt rather than an authorized Action.

---

### 12.26 Decision and Audit

Authorization Decisions may be relevant to audit or accountability processes.

Where applicable, an authorization record may reference:

```text
Subject
Action
Resource
Decision
Time
Context
Authority
Policy
Conditions
Restrictions
Source
```

The specific information retained should be determined by applicable governance, legal, security, privacy, and operational requirements.

ADE-IF does not require that every authorization decision be centrally stored.

---

### 12.27 Decision Across Distributed Authorities

An Authorization Decision may depend upon information from multiple authoritative sources.

For example:

```text
Authority A
    │
    └── Required Information
            │
            ▼
Authority B
    │
    └── Required Information
            │
            ▼
Authorization Evaluation
            │
            ▼
Authorization Decision
```

The requesting system may combine the required semantic results without requiring the underlying authorities to merge their complete records.

This remains consistent with the distributed identity principles established by ADE-IF.

---

### 12.28 Decision and Privacy

An Authorization Decision may provide only the result necessary for the requesting system.

For example:

```text
Authorization Evaluation
        │
        ▼
Permitted
```

The requesting system may not need access to the complete information used to reach the decision.

This supports:

* Data minimization
* Purpose limitation
* Distributed authority
* Privacy-aware information exchange

The decision itself should therefore not automatically expose the underlying identity or authorization information.

---

### 12.29 Foundational Principle

ADE-IF treats an Authorization Decision as the contextual result of evaluating whether an Entity may perform a defined Action.

Conceptually:

```text
Subject
   +
Action
   +
Resource
   +
Authority
   +
Permission
   +
Restrictions
   +
Conditions
   +
Context
   ↓
Authorization Evaluation
   ↓
Authorization Decision
```

The decision should remain distinguishable from:

* Identity
* Authentication
* Authority
* Permission
* Restriction
* Capability
* Action Execution

Authorization Decisions should be contextual, traceable where appropriate, and capable of representing uncertainty or unavailable information without automatically converting those conditions into denial.

---
## 13. Authorization Sources and Lifecycle

An **Authorization Source** identifies the Entity, system, authority, policy, record, or other recognized source from which authorization-related information originates.

Authorization may depend upon information established by one or more sources.

The source of an authorization should remain distinguishable from the Entity to whom the authorization applies.

Conceptually:

```text
Authorization Source
        │
        ▼
Authority / Policy / Rule
        │
        ▼
Authorization
        │
        ▼
Subject Entity
```

An Authorization Source may establish, grant, verify, modify, suspend, revoke, or otherwise provide information relevant to an authorization.

---

### 13.1 Types of Authorization Sources

Authorization information may originate from different types of sources.

Examples include:

* Government authority
* Regulatory authority
* Organization
* Employer
* System administrator
* Resource owner
* Contracting party
* Delegating authority
* Automated policy system
* Authorization service
* Other recognized authority

For example:

```text
Government Authority
        │
        └── Legal Authority

Organization
        │
        └── Organizational Authority

System Administrator
        │
        └── Operational Authority

Automated Policy
        │
        └── System Authorization Rule
```

The meaning and validity of a source should depend upon the applicable context and governing authority.

---

### 13.2 Source and Authority

An Authorization Source may provide evidence or information about Authority, but the source and Authority are not necessarily identical.

Conceptually:

```text
Source
   │
   ▼
Authority
   │
   ▼
Authorization
```

For example, an organizational record may identify an Entity as holding a particular role.

That record may provide information relevant to authority without itself being the complete authority relationship.

The distinction should remain available where required.

---

### 13.3 Source and Authorization

An Authorization may identify the source from which it was established.

For example:

```text
Authorization
    │
    ├── Subject = Entity A
    ├── Action = Approve
    ├── Scope = Project A
    └── Source = Organization Policy
```

This allows a requesting system to determine where the authorization information originated.

A source reference does not necessarily require disclosure of the complete underlying source record.

---

### 13.4 Multiple Authorization Sources

An authorization decision may depend upon multiple sources.

For example:

```text
Government Authority
        │
        └── Legal Requirement
                │
                ▼
Organization
        │
        └── Operational Policy
                │
                ▼
System
        │
        └── Current Configuration
                │
                ▼
Authorization Evaluation
```

The sources may remain independently authoritative for the information they provide.

The requesting system may combine the relevant results without requiring all underlying records to be merged.

---

### 13.5 Source Authority

An Authorization Source should be evaluated according to the authority it is recognized to possess within the applicable context.

For example:

```text
Source A
   │
   └── Authority over Identity Information

Source B
   │
   └── Authority over Employment Status

Source C
   │
   └── Authority over System Access
```

A source that is authoritative for one type of information should not automatically be assumed to be authoritative for all other information.

---

### 13.6 Source Scope

An Authorization Source may have a defined scope.

Scope may include:

* Entity
* Action
* Resource
* Organization
* Location
* Jurisdiction
* Time
* Purpose
* Policy
* Other defined boundaries

Conceptually:

```text
Authorization Source
        │
        ├── Scope
        ├── Authority
        ├── Jurisdiction
        └── Conditions
```

The source should therefore be interpreted within its applicable scope.

---

### 13.7 Source and Jurisdiction

Authorization Sources may operate within different jurisdictions.

For example:

```text
Canadian Authority
        │
        └── Canadian Authorization Information

South African Authority
        │
        └── South African Authorization Information
```

An Authorization Source operating within one jurisdiction should not automatically be assumed to establish authority within another.

Cross-jurisdiction authorization should therefore preserve the distinction between the source, its authority, and the jurisdiction in which that authority applies.

---

### 13.8 Source Availability

An Authorization Source may be unavailable.

Possible source states include:

```text
Available
Unavailable
Unknown
Suspended
Revoked
Expired
```

Source unavailability should not automatically be interpreted as invalid authorization.

For example:

```text
Authorization Source
        │
        └── Unavailable
                │
                ▼
      Authorization Status Unknown
```

The applicable policy should determine how an unavailable source affects the Authorization Decision.

---

### 13.9 Source Verification

Where required, a system may need to establish that an Authorization Source is genuine and recognized for the relevant purpose.

Conceptually:

```text
Authorization Source
        │
        ▼
Source Verification
        │
        ├── Verified
        ├── Not Verified
        ├── Unknown
        └── Unavailable
```

Source verification should remain distinct from verification of the authorization itself.

For example:

```text
Source Verified
      ≠
Authorization Valid
```

A recognized source may provide authorization information that is expired, restricted, or otherwise no longer applicable.

---

### 13.10 Authorization Lifecycle

Authorization may change over Time.

A conceptual lifecycle may include:

```text
Requested
    ↓
Evaluating
    ↓
Granted
    ↓
Active
    ↓
Suspended
    ↓
Restored
    ↓
Expired / Revoked / Cancelled
```

Not every authorization must pass through every state.

The applicable ADE specification or policy should define the permitted lifecycle transitions.

---

### 13.11 Requested

**Requested** indicates that authorization has been requested but has not yet been established.

For example:

```text
Entity
   │
   ▼
Authorization Request
   │
   ▼
Requested
```

Requested should not be interpreted as authorization.

---

### 13.12 Evaluating

**Evaluating** indicates that the authorization request is currently being assessed.

For example:

```text
Authorization Request
        │
        ▼
Identity / Authentication
        │
        ▼
Authority
        │
        ▼
Permissions / Restrictions
        │
        ▼
Conditions
        │
        ▼
Evaluating
```

The system may require information from one or more sources before reaching a decision.

---

### 13.13 Granted

**Granted** indicates that authorization has been established by the applicable authority or authorization mechanism.

For example:

```text
Authorization Evaluation
        │
        ▼
Requirements Satisfied
        │
        ▼
Granted
```

Granted does not necessarily mean that the authorization is currently exercisable.

Time, location, state, conditions, restrictions, or other requirements may still determine whether it is Active.

---

### 13.14 Active

**Active** indicates that the authorization is currently established and available for use within its applicable context.

For example:

```text
Authorization
    │
    ├── Status = Active
    ├── Subject = Entity A
    ├── Action = Operate
    └── Resource = Machine A
```

An Active authorization remains subject to its applicable Permissions, Restrictions, Conditions, and Context.

---

### 13.15 Suspended

**Suspended** indicates that an authorization has been temporarily prevented from being exercised.

For example:

```text
Active Authorization
        │
        ▼
Suspension Condition
        │
        ▼
Suspended
```

Suspension does not necessarily mean that the underlying authorization has been permanently revoked.

It may later return to Active status.

---

### 13.16 Restored

**Restored** indicates that a previously suspended authorization has become active again after the applicable requirements have been satisfied.

For example:

```text
Suspended
    │
    ▼
Suspension Condition Resolved
    │
    ▼
Restored
    │
    ▼
Active
```

The applicable policy should determine whether restoration occurs automatically or requires a new authorization decision.

---

### 13.17 Expired

**Expired** indicates that an authorization is no longer active because its defined validity period has ended.

For example:

```text
Valid From
    │
    ▼
Active
    │
    ▼
Valid Until
    │
    ▼
Expired
```

An expired authorization should not be treated as an active authorization unless a new authorization is established.

---

### 13.18 Revoked

**Revoked** indicates that an authorization has been withdrawn by an Entity or mechanism possessing the applicable authority to revoke it.

For example:

```text
Active Authorization
        │
        ▼
Authorized Revocation
        │
        ▼
Revoked
```

Revocation should remain distinguishable from expiration.

For example:

```text
Expired
    ≠
Revoked
```

Expiration results from the end of a defined validity period.

Revocation results from an explicit withdrawal of authorization.

---

### 13.19 Cancelled

**Cancelled** indicates that an authorization or authorization request has been terminated through an applicable cancellation process.

For example:

```text
Authorization Request
        │
        ▼
Cancellation
        │
        ▼
Cancelled
```

Cancellation should remain distinguishable from denial and revocation.

---

### 13.20 Authorization Lifecycle and Context

Changes in Authorization Context may cause the effective authorization state to change.

For example:

```text
Authorization
      │
      ▼
Context Change
      │
      ├── Time
      ├── Location
      ├── State
      ├── Emergency
      ├── Policy
      └── Restriction
      │
      ▼
Authorization Re-evaluation
```

The underlying authorization record may remain unchanged while its effective applicability changes because of the current context.

---

### 13.21 Authorization Lifecycle and Restrictions

A Restriction may temporarily prevent an Active authorization from being exercised.

For example:

```text
Authorization = Active
        │
        ▼
Restriction Becomes Applicable
        │
        ▼
Action = Restricted
```

The authorization itself does not necessarily become Revoked.

This distinction allows the model to represent contextual limitations without unnecessarily changing the underlying authorization state.

---

### 13.22 Authorization Lifecycle and Conditions

A Condition may determine when an authorization becomes effective or ceases to be effective.

For example:

```text
Authorization
        │
        └── Condition = Emergency
                        │
                        ▼
                 Emergency Occurs
                        │
                        ▼
                 Authorization Active
```

When the condition ceases:

```text
Emergency Ends
        │
        ▼
Condition No Longer Satisfied
        │
        ▼
Authorization Re-evaluation
```

The resulting state should be determined by the applicable authorization policy.

---

### 13.23 Authorization Lifecycle and Delegation

Delegated authorization should have a lifecycle that remains connected to the authority from which it originated.

For example:

```text
Original Authority
        │
        ▼
Delegated Authorization
        │
        ▼
Active
        │
        ▼
Original Authority Revoked
        │
        ▼
Delegated Authorization Re-evaluated
```

A delegated authorization may therefore cease to be valid when the authority upon which it depends is revoked, expired, suspended, or otherwise no longer applicable.

The exact inheritance and dependency rules should be defined by the applicable ADE specification.

---

### 13.24 Authorization Lifecycle and Override

An Override Authorization may be temporary and context-specific.

For example:

```text
Normal Authorization
        │
        ▼
Emergency
        │
        ▼
Override Authorization
        │
        ▼
Temporary Action
        │
        ▼
Override Ends
        │
        ▼
Normal Authorization Context Restored
```

Override authorization should therefore have explicit scope, conditions, and lifecycle boundaries.

---

### 13.25 Lifecycle Events

Changes to authorization may themselves be represented as Events within ADE-Core.

Examples include:

```text
Authorization Requested
Authorization Granted
Authorization Activated
Authorization Suspended
Authorization Restored
Authorization Modified
Authorization Delegated
Authorization Revoked
Authorization Expired
Authorization Cancelled
```

These Events may provide temporal context for authorization lifecycle changes.

Detailed Event representation remains subject to the applicable ADE specifications.

---

### 13.26 Authorization Source Changes

The source of an authorization may change over Time.

For example:

```text
Organization A
      │
      └── Original Authorization Source
                │
                ▼
        Organizational Change
                │
                ▼
Organization B
      │
      └── New Authorization Source
```

A change in source should not automatically be interpreted as a change in the Subject Entity.

The applicable authority and policy should determine whether the authorization remains valid, must be re-established, or must be revoked.

---

### 13.27 Distributed Authorization Sources

Authorization information may remain distributed across multiple sources.

For example:

```text
                 Authorization Request
                         │
              ┌──────────┼──────────┐
              ▼          ▼          ▼
          Authority A Authority B Authority C
              │          │          │
              ▼          ▼          ▼
          Required    Required    Required
         Information Information Information
              │          │          │
              └──────────┼──────────┘
                         ▼
               Authorization Evaluation
                         │
                         ▼
               Authorization Decision
```

The sources do not necessarily need to combine their underlying records.

The requesting system may obtain only the information necessary to evaluate the authorization request.

---

### 13.28 Source Independence

Each Authorization Source should remain responsible for the information or authority within its defined scope.

For example:

```text
Source A
    └── Responsible for Information A

Source B
    └── Responsible for Information B
```

One source should not automatically become authoritative for information belonging to another source.

This supports:

* Distributed governance
* Jurisdictional independence
* Data ownership
* Data minimization
* Interoperability

---

### 13.29 Source and Privacy

An Authorization Source may provide only the minimum information required to support an authorization decision.

For example:

```text
Authorization Source
        │
        ▼
Required Verification
        │
        ▼
Authorization Result
        │
        ▼
Requesting System
```

The requesting system may receive:

```text
Permitted
```

without receiving the complete underlying source record.

This supports the ADE-IF principle that authorization does not require unnecessary disclosure of underlying information.

---

### 13.30 Source and Audit

Where appropriate, an authorization record may reference its source for accountability or audit purposes.

Possible references include:

```text
Source
Authority
Policy
Authorization Identifier
Decision Time
Effective Time
Expiration Time
Revocation Information
```

The amount of information retained should depend upon applicable legal, privacy, security, governance, and operational requirements.

ADE-IF does not require a centralized authorization audit system.

---

### 13.31 Lifecycle Integrity

Where authorization decisions have significant consequences, systems may require mechanisms to establish that lifecycle changes are legitimate.

Examples may include:

* Source references
* Authority references
* Authorization identifiers
* Time information
* Decision records
* Integrity mechanisms
* Audit records
* Other applicable controls

ADE-IF does not require a specific technical implementation.

The architecture remains technology-independent.

---

### 13.32 Lifecycle and Uncertainty

Authorization lifecycle information may itself be uncertain.

For example:

```text
Authorization Status
        │
        ▼
Unknown
```

This should remain distinguishable from:

```text
Revoked
Expired
Denied
```

Similarly:

```text
Source Unavailable
        │
        ▼
Authorization State Unable to Determine
```

should not automatically be converted into:

```text
Authorization = Denied
```

unless the applicable policy explicitly requires that outcome.

---

### 13.33 Foundational Principle

ADE-IF treats Authorization Sources as identifiable origins of authorization-related authority or information and Authorization Lifecycle as the representation of how authorization changes over Time.

Conceptually:

```text
Authorization Source
        │
        ▼
Authority / Policy
        │
        ▼
Authorization
        │
        ▼
Lifecycle
        │
        ├── Requested
        ├── Granted
        ├── Active
        ├── Suspended
        ├── Restored
        ├── Expired
        ├── Revoked
        └── Cancelled
```

Authorization Sources should remain distinguishable from Subjects, Permissions, Restrictions, and Authorization Decisions.

Authorization Lifecycles should remain contextual, traceable where appropriate, and capable of representing changes without requiring a centralized authorization record.

---


