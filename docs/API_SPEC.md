# API Specification

## Purpose
Define the API layer for Rigging OS.

The API must support:
- fast calculations
- job workflows
- verification updates
- policy enforcement
- reporting
- audited override control

---

## Core Principles
- deterministic outputs
- structured JSON responses
- no hidden logic
- versionable payloads
- override actions always auditable
- override severity must be explicit

---

## Calculation Endpoints

### POST /api/rigging/calculate/bridle
Input:
- load
- legs
- span
- drop

Output:
- per_leg_tension
- total_load
- warnings
- status

---

### POST /api/rigging/calculate/sling
Input:
- sling_type
- hitch_type
- angle
- load

Output:
- adjusted_capacity
- warnings

---

### POST /api/rigging/calculate/validate
Input:
- calculation payload

Output:
- pass
- warnings
- classification

---

## Job Endpoints

### GET /api/rigging/jobs

### POST /api/rigging/jobs

### GET /api/rigging/jobs/[jobId]

### PATCH /api/rigging/jobs/[jobId]

---

## Point Management

### POST /api/rigging/jobs/[jobId]/points

### PATCH /api/rigging/jobs/[jobId]/points/[pointId]

---

## Verification

### GET /api/rigging/jobs/[jobId]/verification

### PATCH /api/rigging/jobs/[jobId]/points/[pointId]/verification

---

## Signoff

### POST /api/rigging/jobs/[jobId]/signoff

Behaviour:
- must validate workflow completeness
- must block if requirements are not met
- may only proceed when requirements are satisfied or an authorized override is used

### POST /api/rigging/jobs/[jobId]/override-signoff

Input:
- override_reason
- override_severity
- unresolved_items
- user_confirmation

Allowed severity values:
- minor
- major
- critical

Behaviour:
- only authorized roles may override
- reason is mandatory
- severity is mandatory
- action must be logged with identity and timestamp
- overridden signoff state must be visible in exports and job history
- critical overrides must be visually emphasized in reports and audit views

---

## Company Policy

### GET /api/company/rigging/policies

### POST /api/company/rigging/policies

Company policies may later define which roles can perform which override severities.

---

## Reporting

### POST /api/rigging/jobs/[jobId]/export/pdf

Exports must visibly indicate:
- whether signoff occurred through override
- override severity
- override reason

---

## Audit

### GET /api/rigging/jobs/[jobId]/history

### GET /api/rigging/jobs/[jobId]/overrides

Override audit records must include:
- actor
- timestamp
- severity
- reason
- unresolved items snapshot

---

## API Rule

The API must enforce workflow rules at signoff stage, not during calculation.

Override is permitted only as a controlled, role-restricted, permanently auditable action.
