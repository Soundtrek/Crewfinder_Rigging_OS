# Architecture

## Overview
Crewfinder Rigging OS is designed as a modular system embedded inside the Crewfinder application.

It consists of:
- frontend UI (Next.js)
- API layer (Next.js API routes)
- deterministic calculation engine
- database (Supabase/Postgres)
- optional AI advisory layer

---

## Core Layers

### 1. UI Layer
- mobile-first interface
- quick calculator
- job workspace
- verification UI
- reporting UI

### 2. API Layer
Handles:
- calculations
- job CRUD
- verification updates
- policy retrieval
- report generation

### 3. Calculation Engine
- deterministic math
- no external dependency required
- returns structured JSON

### 4. Data Layer
- jobs
- points
- calculations
- policies
- templates
- signoffs
- audit logs

### 5. Compliance Behaviour Layer
- workflow enforcement
- blocking logic
- state transitions

---

## State Model

Job states:
- draft
- in_progress
- ready_for_review
- ready_for_signoff
- locked

---

## Integration Points

### Crewfinder Core
- profiles
- companies
- shows
- invites

### Future
- AI advisory system
- reporting pipelines
- document storage

---

## Key Design Rule

All logic must be:
- deterministic
- explainable
- auditable

No hidden behaviour allowed.
