# Route Map

## Purpose
Define the route structure for Crewfinder Rigging OS.

The route model assumes:
- calculation access stays fast and available
- workflow completeness is enforced at review and signoff stages
- company and freelancer workspaces remain properly separated

---

## Route Design Rules
- mobile-first pages
- no unnecessary nesting
- clear separation between personal, company, and admin surfaces
- route naming must match system responsibilities

---

## Personal / Freelancer Routes

### Dashboard Entry
- `/tools/rigging`

Purpose:
- personal landing page
- recent jobs
- quick actions
- templates and saved work access

### Quick Calculation
- `/tools/rigging/quick`

Purpose:
- fast calculator access
- immediate field math
- no signoff workflow required

### Personal Jobs
- `/tools/rigging/jobs`
- `/tools/rigging/jobs/new`
- `/tools/rigging/jobs/[jobId]`

Purpose:
- list jobs
- create jobs
- manage point lists and calculations

### Verification Workspace
- `/tools/rigging/jobs/[jobId]/verify`

Purpose:
- per-point verification
- checklist progress
- issue logging

### Reporting
- `/tools/rigging/jobs/[jobId]/report`

Purpose:
- generate summary output
- export records

### Signoff
- `/tools/rigging/jobs/[jobId]/signoff`

Purpose:
- hard gate state review
- signoff only when requirements are satisfied

### Library
- `/tools/rigging/library`
- `/tools/rigging/library/templates`
- `/tools/rigging/library/equipment`

Purpose:
- personal templates
- equipment references

---

## Company Routes

### Company Rigging Home
- `/company/tools/rigging`

Purpose:
- company landing page
- active rigging jobs
- policy summary
- team collaboration access

### Company Policies
- `/company/tools/rigging/policies`

Purpose:
- configure enforcement thresholds
- define required checklist items
- define approved equipment and workflow rules

### Company Templates
- `/company/tools/rigging/templates`

Purpose:
- reusable company job templates

### Company Library
- `/company/tools/rigging/library`

Purpose:
- approved equipment and reference records

### Company Jobs
- `/company/tools/rigging/jobs/[jobId]`
- `/company/tools/rigging/jobs/[jobId]/team`
- `/company/tools/rigging/jobs/[jobId]/verify`
- `/company/tools/rigging/jobs/[jobId]/report`
- `/company/tools/rigging/jobs/[jobId]/signoff`

Purpose:
- shared operational workspace
- team permissions
- verification
- report generation
- signoff enforcement

---

## Admin Routes

### Admin Control Surface
- `/admin/tools/rigging`

Purpose:
- feature flags
- plan gating
- disclaimer content
- usage visibility
- reference data governance

---

## Route Behaviour Rules

### Calculation Behaviour
Calculations may be run freely in valid working contexts.
Warnings should be visible immediately.
Calculations alone do not approve work.

### Signoff Behaviour
The signoff route is the hard enforcement gate.
A job may not be signed off unless required workflow conditions are complete.

### Policy Behaviour
Company routes must reflect company enforcement rules without requiring code changes.

---

## Future Route Extensions
Possible later additions:
- `/tools/rigging/jobs/[jobId]/documents`
- `/company/tools/rigging/jobs/[jobId]/documents`
- `/tools/rigging/jobs/[jobId]/history`
- `/company/tools/rigging/jobs/[jobId]/history`

These should be added only when the document and audit layers are implemented in full.
