# Build Requirements

## Purpose
Define the full product requirements for Crewfinder Rigging OS at production-spec level.

---

## Product Goal
Build a field-first rigging workflow enforcement system for entertainment and live events that combines deterministic calculations, operational workflow control, verification, reporting, and safety-support documentation inside the Crewfinder ecosystem.

---

## Core Product Requirements

### 1. Deterministic Calculation Engine
The system must provide fast, explainable, repeatable rigging calculations.

Required calculation families:
- vertical load checks
- two-leg bridle calculations
- three-leg bridle calculations
- four-leg shared load model
- sling angle tension checks
- hitch-type adjustments
- hardware WLL comparison
- simple load distribution checks

### 2. Hard Workflow Enforcement
The system must block workflow progression when required conditions are incomplete.

At minimum, the system must be able to block signoff when:
- required points are missing
- required calculations are missing
- critical warnings remain unresolved
- required verification states are incomplete
- required company policy records are missing

### 3. Mobile-First Speed
The system must be usable on a phone in the field.

Minimum expectations:
- fast load time
- large touch targets
- readable results in poor site conditions
- dark mode support
- minimal friction for quick calculations

### 4. Job-Based Workflow
The system must support jobs as the main working container.

A job should support:
- general event info
- point list
- calculations
- verification records
- notes
- attached records
- signoff state

### 5. Company Policy Layer
The system must support company-defined operational rules.

These may include:
- angle thresholds
- safety factors
- required records before signoff
- approved equipment lists
- mandatory checklist steps

### 6. Reporting and Export
The system must generate usable reports and archived output records.

Required outputs:
- calculation summary
- job summary
- verification summary
- signoff-ready report pack

### 7. Auditability
The system must record:
- who did what
- when they did it
- what inputs were used
- what outputs were generated
- what state changes occurred

---

## Non-Functional Requirements

### Performance
- calculation response should feel immediate
- normal calculator interactions should not require full-page reloads

### Reliability
- calculation outputs must be stable and deterministic
- no hidden randomness in the core engine

### Security
- workspace scoping required
- role-based access required
- audit logs required

### Maintainability
- no hardcoded business logic where admin/company configuration is required
- versionable records
- modular docs and modular implementation path

---

## Compliance-Oriented Behaviour Requirements
The system must support operational completeness without claiming legal authority.

Required behaviours:
- status progression controls
- clear warning levels
- visible distinction between calculated safe and workflow complete
- clear distinction between company-policy pass and general mathematical pass

---

## Scope Boundaries

### In Scope
- calculations
- jobs
- point verification
- reporting
- signoff workflow
- company policies
- audit trail
- compliance-support records

### Out of Scope for MVP
- CAD drafting
- structural modelling suite
- advanced 3D rigging design
- legal certification issuance
- engineering approval workflow

---

## Success Standard
Rigging OS succeeds when it is:
- used during real builds
- trusted for fast calculations
- relied on for workflow control
- adopted by companies as a standard operating tool
