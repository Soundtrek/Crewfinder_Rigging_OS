# Compliance System Behaviour (Operational Standard Mode)

## Purpose
Define how Rigging OS behaves as an operational-standard tool that enforces workflow completeness without making legal compliance claims.

---

## Core Principle
The system enforces PROCESS COMPLETENESS, not legal compliance.

---

## Enforcement Model
Rigging OS operates in controlled states:

### Draft
- job can be incomplete
- calculations editable
- no signoff allowed

### In Progress
- points added
- calculations present
- partial verification allowed

### Ready for Review
System checks:
- required calculations exist
- points defined
- basic verification entries present

### Ready for Signoff
System requires:
- all points have verification state
- no unresolved critical warnings
- required checklists completed

### Locked (Signed Off)
- job becomes read-only
- all data versioned
- signoff records attached

---

## Mandatory Checks Before Signoff

The system must enforce:
- all rigging points have a status
- calculations exist for load-bearing elements
- no critical safety warnings remain unresolved
- required workflow steps completed

---

## Warning Classification

### Informational
- non-critical notes

### Warning
- user attention required

### Critical
- blocks signoff

---

## Company Policy Integration

Company rules may define:
- acceptable angle ranges
- required safety factors
- required documentation fields

System must:
- enforce these at workflow level
- differentiate between math-safe and policy-compliant

---

## Audit Requirements

System must record:
- calculation inputs and outputs
- user actions
- verification updates
- signoff actions
- timestamps

---

## Key Rule

The system may block workflow progression.
The system must NOT claim legal compliance.
