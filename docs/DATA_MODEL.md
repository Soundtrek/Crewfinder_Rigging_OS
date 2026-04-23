# Data Model

## Overview
Defines the core entities required for Rigging OS.

---

## rigging_jobs
- id
- owner_profile_id
- company_profile_id
- title
- description
- venue
- event_date
- status
- created_at
- updated_at

---

## rigging_job_points
- id
- job_id
- label
- intended_load
- actual_load
- verification_status
- notes

---

## rigging_calculations
- id
- job_id
- type
- input_json
- output_json
- created_at

---

## rigging_company_policies
- id
- company_profile_id
- safety_factor
- max_angle
- required_checks

---

## rigging_templates
- id
- owner_profile_id
- company_profile_id
- template_json

---

## rigging_signoffs
- id
- job_id
- role
- user_id
- timestamp

---

## rigging_audit_log
- id
- job_id
- action
- user_id
- timestamp

---

## Key Principles
- all records must be auditable
- no destructive overwrites
- versioning required for critical data
