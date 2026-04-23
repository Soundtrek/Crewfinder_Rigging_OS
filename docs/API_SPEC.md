# API Specification

## Purpose
Define the API layer for Rigging OS.

The API must support:
- fast calculations
- job workflows
- verification updates
- policy enforcement
- reporting

---

## Core Principles
- deterministic outputs
- structured JSON responses
- no hidden logic
- versionable payloads

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

---

## Company Policy

### GET /api/company/rigging/policies

### POST /api/company/rigging/policies

---

## Reporting

### POST /api/rigging/jobs/[jobId]/export/pdf

---

## Audit

### GET /api/rigging/jobs/[jobId]/history

---

## API Rule

The API must enforce workflow rules at signoff stage, not during calculation.
