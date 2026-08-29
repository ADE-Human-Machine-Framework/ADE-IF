# ADE Human-Machine Framework

## ADE-IF Use Cases

**Status:** Foundational Draft
**Repository:** ADE-IF
**Version:** 0.1.0

---

## 1. Purpose

This document defines real-world scenarios used to examine and test the ADE Identity Framework (ADE-IF).

The purpose of these use cases is to determine whether the concepts defined by ADE-IF can represent practical identity, verification, authorization, privacy, and cross-system situations without unnecessary duplication of information.

Use cases are intended to support examination and challenge before concepts become formalized ADE standards.

---

## 2. Use Case 1 — Identity Reference and Authorized Access

### 2.1 Scenario

A person needs to access a service that requires verification of specific information about them.

The service does not need the person's complete identity record.

The required information may be held by one or more authoritative information sources.

The person may not possess an SSI credential, digital identity wallet, or other portable identity credential.

The requesting system should nevertheless be able to establish whether the person is authorized for the requested purpose.

---

## 3. Participants

The scenario involves several possible participants:

```text
Person
   │
   │ requests service
   ▼
Requesting System
   │
   │ requests required information
   ▼
Authoritative Information Source
```

Additional authorities or information sources may participate where required.

For example:

```text
Person
   │
   ▼
Requesting System
   │
   ├──► Canadian Authority
   │
   └──► South African Authority
```

The existence of multiple sources does not require those sources to combine their underlying records.

---

## 4. Identity Reference

The requesting system does not necessarily need to obtain or store a complete identity record.

Instead, it may use an **Identity Reference** to identify the subject and determine where authoritative information relevant to the request may be obtained.

Conceptually:

```text
Identity Reference
        │
        ├── identifies Entity
        │
        ├── references Information Source
        │
        ├── identifies Authority
        │
        └── identifies applicable Information
```

The Identity Reference therefore acts as a structured reference to identity-related information rather than necessarily containing all of that information.

---

## 5. Distributed Information

Identity-related information may exist across multiple authoritative sources.

For example:

```text
Canadian Authority
    │
    ├── Citizenship information
    └── Canadian identity information


South African Authority
    │
    ├── Citizenship information
    └── South African identity information
```

A request concerning a person with relationships to both jurisdictions does not necessarily require the two authorities to merge or duplicate their complete records.

Instead, the requesting system may obtain only the information required for the specific purpose.

---

## 6. Minimum Necessary Information

The requesting system should request only the information necessary to satisfy the purpose of the transaction or service.

For example, a system may need to establish:

```text
Is this person authorized to access the service?

Answer:
YES
```

It may not need:

```text
Full name
Full address
Date of birth
Citizenship history
Passport number
Complete identity record
```

unless those specific attributes are required for the authorized purpose.

This supports data minimization and reduces unnecessary exposure of identity information.

---

## 7. Verification Without an SSI Credential

A person should not be required to possess an SSI credential solely because a system needs to verify information about them.

The requesting system may instead use an authorized identity reference and obtain verification from an authoritative information source.

Conceptually:

```text
Person
   │
   │ presents identity reference
   ▼
Requesting System
   │
   │ verifies required information
   ▼
Authoritative Source
   │
   ▼
Verification Result
```

The person may therefore participate in an identity verification process without carrying a complete digital identity credential.

---

## 8. Identity, Verification, and Authorization

ADE-IF distinguishes three related but separate concepts.

### Identity

Answers:

> **Which Entity is being referenced?**

### Verification

Answers:

> **Is the relevant information sufficiently verified for this purpose?**

### Authorization

Answers:

> **Is the Entity authorized to perform or receive the requested action?**

These should not be treated as the same condition.

For example:

```text
Identity
    ↓
Person identified

Verification
    ↓
Required information confirmed

Authorization
    ↓
Person permitted to perform requested action
```

A system may therefore verify an identity-related attribute without granting authorization.

---

## 9. Human and Non-Human Entities

ADE-IF may need to distinguish between different classes of Entities involved in identity and authorization processes.

For example:

```text
H = Human
D = Device
S = System
O = Organization
```

The classification identifies the type of Entity involved in a process.

It should not, by itself, be interpreted as proof of identity or authorization.

For example:

```text
H = Human
```

does not mean:

```text
Human is authorized
```

Similarly:

```text
D = Device
```

does not automatically mean:

```text
Device is trusted
```

Entity classification and authorization remain separate semantic concepts.

---

## 10. Authorization Levels

Authorization may require different levels of authority.

For example:

```text
Level 1
    Highest designated human authority

Level 2
    Authorized human authority

Level 3
    Authorized operational authority

Level 4
    Limited authority

Level 5
    Restricted authority
```

These levels are conceptual examples only.

The specific meanings and governance of authorization levels must be defined by the applicable ADE standard, organization, or application.

An authorization level should describe what an Entity is permitted to do within a defined context.

It should not be interpreted as a measure of the person's worth, identity certainty, or general trustworthiness.

---

## 11. Emergency Authorization

Some systems may require emergency intervention.

For example:

```text
System
   │
   │ scheduled operation
   ▼
Automated Action
```

A designated human authority may be able to:

```text
Pause
Cancel
Override
```

the operation.

In higher-risk environments, authorization may require multiple authorized humans.

For example:

```text
Human Level 3
      +
Human Level 3
      ↓
Emergency Authorization
      ↓
Pause / Override
```

This illustrates that authorization may depend on:

* Entity identity
* Entity classification
* Authorization level
* Context
* Action
* Time
* Emergency conditions
* Number of required authorities

---

## 12. No Central Identity Record Required

This use case does not require a single system to possess a complete identity record.

Instead:

```text
                 Identity Reference
                        │
             ┌──────────┴──────────┐
             ▼                     ▼
      Authority A             Authority B
             │                     │
       Required Data          Required Data
             │                     │
             └──────────┬──────────┘
                        ▼
                Verification Result
                        │
                        ▼
                Requesting System
```

The authoritative systems may retain control over the information for which they are responsible.

The requesting system receives only the information or result necessary for the specific purpose.

---

## 13. Cross-Jurisdiction Example

A person has identity relationships with both Canada and South Africa.

A service requires confirmation of a particular citizenship or authorization condition.

The requesting system does not need to create a combined Canadian/South African identity record.

Instead:

```text
Request
  │
  ├──► Canadian Authority
  │       │
  │       └── Required Information
  │
  └──► South African Authority
          │
          └── Required Information
```

The information sources remain authoritative for their respective information.

The requesting system combines the **required semantic results**, not necessarily the underlying identity records.

This distinction is important for jurisdiction, privacy, governance, and data ownership.

---

## 14. Information Availability

An authoritative source may be unavailable.

ADE-IF should therefore distinguish between conditions such as:

```text
Verified
Not Verified
Unknown
Unavailable
Not Applicable
Expired
Revoked
```

For example:

```text
Authority = Unavailable
```

does not necessarily mean:

```text
Identity = Invalid
```

The verification result must retain the distinction between lack of confirmation and evidence that a claim is false.

---

## 15. Use Case Outcome

The desired outcome is:

```text
Person
   ↓
Identity Reference
   ↓
Relevant Authority
   ↓
Required Information
   ↓
Verification
   ↓
Authorization Decision
   ↓
Permitted or Denied Action
```

The process should allow the requesting system to establish the information necessary for the authorized purpose without requiring unnecessary duplication of the person's complete identity information.

---

## 16. Questions for Challenge

This use case should be used to challenge ADE-IF with questions such as:

1. Can an Identity Reference identify an Entity without containing the complete identity record?
2. Can authoritative information remain distributed across jurisdictions?
3. Can a requesting system obtain only the information necessary for its purpose?
4. Can verification occur without requiring an SSI credential?
5. Can identity, verification, and authorization remain separate concepts?
6. Can human and non-human Entities be distinguished without confusing classification with trust?
7. Can authorization levels support different permissions?
8. Can multiple authorized humans participate in emergency authorization?
9. Can unavailable information remain distinguishable from invalid information?
10. Can the model operate without requiring a central identity database?
11. Can the model support different jurisdictions without assuming that one jurisdiction owns all identity information?
12. Can the model preserve authoritative control over information while still allowing interoperable verification?

These questions should guide future ADE-IF development and testing.

---

## 17. Foundational Principle

> **An identity system should provide the information necessary to establish identity, verification, and authorization without requiring unnecessary duplication or disclosure of the underlying information.**

ADE-IF therefore treats identity as a distributed, contextual, and purpose-dependent information relationship rather than requiring every system to possess a complete identity record.

---

**ADE Human-Machine Framework**

*An open architecture for human and machine understanding.*
