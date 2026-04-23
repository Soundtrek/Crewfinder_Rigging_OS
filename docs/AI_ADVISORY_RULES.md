# AI Advisory Rules

## Purpose
Define how artificial intelligence may be used safely inside Crewfinder Rigging OS.

This document establishes a strict boundary: AI may assist interpretation and workflow understanding, but it may never replace deterministic rigging math, workflow enforcement, or accountable human signoff.

---

## Core Position
AI in Rigging OS is advisory only.

AI may:
- explain
- suggest
- summarize
- highlight

AI may not:
- approve
- certify
- sign off
- override
- replace deterministic calculations

---

## Safe AI Use Cases

### 1. Explanation
AI may explain why a deterministic result failed or why a warning appeared.

Examples:
- explain high sling tension caused by angle
- explain difference between math-safe and policy-compliant
- explain why signoff is blocked

### 2. Safer Alternative Suggestions
AI may suggest possible safer alternatives based on deterministic outputs.

Examples:
- reduce angle by increasing drop
- split load differently
- review equipment selection

These suggestions must be framed as advisory only.

### 3. Workflow Summaries
AI may summarize the current job state.

Examples:
- list unresolved items
- summarize verification gaps
- summarize override history

### 4. Document/Checklist Assistance
AI may help users understand missing records or incomplete checklist items.

Examples:
- identify which required items are still missing
- summarize uploaded notes into a checklist view

---

## Unsafe AI Uses (Forbidden)
AI must never:
- produce the authoritative rigging math result
- determine safe/unsafe status independently
- bypass workflow enforcement
- submit signoff actions
- generate override decisions
- imply legal compliance
- imply engineering approval
- imply certification of people, equipment, or structures

---

## Source of Truth Hierarchy
The system must always follow this order of authority:

1. deterministic calculation engine
2. workflow enforcement engine
3. company policy rules
4. human authorized actions
5. AI advisory layer

AI is always last in authority.

---

## UI Rules
When AI is shown in the interface:
- it must be clearly labeled as advisory
- it must not visually resemble final approval
- it must reference the deterministic result it is explaining
- it must never appear as the only result shown

---

## Audit Rules
AI interactions should be loggable where relevant.

At minimum, the system should be able to record:
- prompt purpose or advisory action type
- related job or calculation context
- output summary
- timestamp
- user who requested it

---

## Product Rule
Rigging OS must remain fully usable and trustworthy when AI is disabled.

AI is an enhancement layer, not a dependency for core safety workflows.
