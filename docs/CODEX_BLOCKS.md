# Codex Blocks

## Purpose
Provide implementation-ready build blocks for the first development phase of Crewfinder Rigging OS.

These blocks are written so they can be handed to Codex or a developer as direct execution briefs.

---

## Block 1 — Create Initial Database Schema

### Goal
Create the first migration for the rigging core data model.

### Build
Add a migration that creates these tables:
- rigging_jobs
- rigging_job_points
- rigging_calculations
- rigging_company_policies
- rigging_signoffs
- rigging_audit_log
- rigging_overrides

### Requirements
- use UUID primary keys
- include created_at and updated_at where relevant
- include owner_profile_id and company_profile_id where relevant
- include status fields with explicit allowed values
- include jsonb columns for flexible calculation payloads
- do not hardcode company rules into schema defaults

### Notes
- status model must support draft, in_progress, ready_for_review, ready_for_signoff, locked
- override severity must support minor, major, critical
- audit records must be append-only in design intent

---

## Block 2 — Create Type Definitions and Domain Models

### Goal
Create shared TypeScript domain types for the rigging system.

### Build
Add a rigging domain type layer covering:
- RiggingJob
- RiggingJobPoint
- RiggingCalculation
- RiggingVerificationStatus
- RiggingSignoff
- RiggingOverride
- RiggingOverrideSeverity
- RiggingWarning
- RiggingCompanyPolicy

### Requirements
- keep deterministic calculation results strongly typed
- include explicit warning severity typing
- include explicit signoff and override state typing

---

## Block 3 — Build Deterministic Calculation Engine

### Goal
Create the first rigging calculation service.

### Build
Implement a deterministic service layer for:
- vertical load calculation
- 2-leg bridle calculation
- 3-leg bridle calculation
- sling angle tension check
- hitch-type adjustment logic
- hardware WLL comparison

### Requirements
- metric and imperial aware input handling
- normalized output payloads
- no AI usage
- no randomness
- return warnings with clear classifications

### Output Shape
Each calculation must return:
- normalized_inputs
- calculated_values
- warnings
- status
- explanation_codes

---

## Block 4 — Create API Routes for Calculations

### Goal
Expose the deterministic calculation engine through API routes.

### Build
Add these routes:
- POST /api/rigging/calculate/bridle
- POST /api/rigging/calculate/sling
- POST /api/rigging/calculate/validate

### Requirements
- validate request payloads strictly
- reject malformed inputs with clean errors
- return structured JSON only
- calculation route must not mutate persistent data

---

## Block 5 — Build Quick Calculator UI

### Goal
Create the first user-facing field calculator.

### Build
Add route:
- /tools/rigging/quick

### UI Requirements
- calculator type selector
- units selector
- input form
- results card
- warning strip
- mobile-first layout

### Behaviour
- allow calculations freely
- never block calculations at input stage
- clearly surface warnings
- do not imply approval or signoff

---

## Block 6 — Create Rigging Job CRUD

### Goal
Create the first job workspace storage layer.

### Build
Add API routes:
- GET /api/rigging/jobs
- POST /api/rigging/jobs
- GET /api/rigging/jobs/[jobId]
- PATCH /api/rigging/jobs/[jobId]

### Requirements
- support personal and company ownership scopes
- support status transitions
- enforce workspace scoping

---

## Block 7 — Create Point Management and Verification

### Goal
Support point records and point verification state.

### Build
Add API routes:
- POST /api/rigging/jobs/[jobId]/points
- PATCH /api/rigging/jobs/[jobId]/points/[pointId]
- GET /api/rigging/jobs/[jobId]/verification
- PATCH /api/rigging/jobs/[jobId]/points/[pointId]/verification

### Requirements
- verification state must be explicit
- support issue logging notes
- unresolved critical issues must be queryable later by enforcement

---

## Block 8 — Build Signoff Readiness Evaluator

### Goal
Create the enforcement logic for signoff-stage blocking.

### Build
Implement a readiness evaluator that checks:
- required points exist
- all points have verification state
- required calculations exist
- critical unresolved items are absent
- company-required checks are satisfied where applicable

### Requirements
- calculation remains allowed before signoff
- blocking happens only at signoff stage
- evaluator returns machine-readable failure reasons

---

## Block 9 — Build Signoff and Override Endpoints

### Goal
Implement controlled signoff and audited override.

### Build
Add routes:
- POST /api/rigging/jobs/[jobId]/signoff
- POST /api/rigging/jobs/[jobId]/override-signoff

### Requirements
- signoff blocked unless ready or override is authorized
- override requires reason
- override requires severity
- override requires role authorization
- override writes audit records
- override state must be visible in job history

---

## Block 10 — Build Audit Trail Layer

### Goal
Record important actions across the rigging workflow.

### Build
Add history support for:
- calculation save actions
- point changes
- verification changes
- signoff attempts
- overrides

### Requirements
- append-only behaviour
- actor identity required
- timestamp required

---

## Block 11 — Add Company Policy Surface (Initial)

### Goal
Create the first policy configuration layer.

### Build
Add routes:
- GET /api/company/rigging/policies
- POST /api/company/rigging/policies

### Requirements
- allow safety factor rules
- allow angle thresholds
- allow required checks list
- prepare for future role-based override severity rules

---

## Block 12 — Add Safe AI Advisory Stub

### Goal
Create a future-safe placeholder for AI without coupling core logic to it.

### Build
Add non-authoritative advisory interface contract only.

### Requirements
- no AI dependency in core calculation engine
- no AI dependency in signoff flow
- label any advisory outputs as advisory
- core system must work fully when AI is disabled

---

## Delivery Rule
Build in this order:
1. schema
2. types
3. deterministic engine
4. calculator API
5. quick UI
6. jobs
7. verification
8. readiness evaluator
9. signoff and override
10. audit
11. policies
12. advisory stub

Do not skip readiness, signoff, or override.
