# UI Canvas

## Purpose
Define the real user interface structure for Crewfinder Rigging OS.

This is not a loose idea document. It is a screen-by-screen UI canvas intended to guide actual interface design and build.

The UI must feel like a real professional field tool:
- fast
- clear
- safety-aware
- mobile-first
- usable under pressure

---

# 1. UI Design Principles

## Core Principles
- mobile-first first, desktop second
- one clear primary action per screen
- warnings highly visible
- no clutter
- no CAD-like complexity in MVP
- dark mode friendly for arenas, backstage, and low-light use
- touch-friendly spacing and controls

## Emotional Target
The product should feel:
- professional
- calm
- fast
- trustworthy
- serious

It must never feel:
- playful
- experimental
- consumer-app casual
- visually noisy

---

# 2. Global Layout System

## Mobile Shell
Top bar:
- page title
- current job context when applicable
- overflow menu

Main area:
- primary module content

Bottom action bar:
- back
- save
- calculate / verify / signoff depending on screen

## Desktop Shell
Left sidebar:
- Rigging Home
- Quick Calc
- Jobs
- Templates
- Equipment
- Policies (company)
- Reports
- Admin (admin only)

Main content:
- working canvas

Right panel:
- warnings
- job summary
- state badge
- signoff readiness

---

# 3. Visual Language

## Color Roles
Use restrained, corporate color language.

### Neutral Base
- charcoal / graphite base for dark mode
- clean white / soft gray for light mode

### Status Colors
- safe = green
- warning = amber
- critical = red
- override = purple or strong accent distinct from warning red
- locked / signed off = blue-gray

## Typography
- strong page titles
- compact but readable field labels
- large numeric result presentation
- warning text must remain readable in poor lighting

## Card System
Core UI units should be cards with:
- title
- body
- status badge
- action row

Primary card types:
- calculation card
- warning card
- point card
- verification card
- signoff card
- override card

---

# 4. Core Screens

## Screen A — Rigging Home
Route:
- /tools/rigging

Purpose:
Main entry dashboard for the user.

### Layout
Header:
- page title: Rigging OS
- subtext: field calculations, jobs, and signoff workflow

Top action row:
- New Quick Calculation
- New Job
- Open Last Job

Sections:
1. Recent Jobs
2. Quick Actions
3. Templates
4. Alerts / Pending Signoff

### Key UI Blocks
Recent Jobs card list:
- job title
- venue
- date
- status badge
- unresolved warnings count

Quick Actions tiles:
- Bridle Calc
- Sling Calc
- New Job
- Verify Points

---

## Screen B — Quick Calculator
Route:
- /tools/rigging/quick

Purpose:
Fast field-use calculator.

### Layout
Top section:
- calculator type segmented control
  - Bridle
  - Sling
  - Load Check

Inputs section card:
- unit system toggle (metric / imperial)
- dynamic input fields based on selected calculator

Result section card:
- main calculated value large and prominent
- secondary values below
- status badge on top right

Warning section:
- stacked warning cards

Bottom action bar:
- Calculate
- Save to Job
- Clear

### Interaction Rules
- calculation is always allowed
- warnings appear immediately after calculation
- never visually imply approval

### Example Bridle Layout
Input fields:
- total load
- legs
- span
- drop

Result fields:
- tension per leg
- resultant force
- angle state
- warning classification

---

## Screen C — Job List
Route:
- /tools/rigging/jobs

Purpose:
List, filter, and open rigging jobs.

### Layout
Header:
- title
- New Job button

Filters row:
- status
- venue
- date
- company / personal

Job cards:
- title
- venue
- event date
- state badge
- verification progress
- unresolved critical count
- open button

---

## Screen D — Job Workspace
Route:
- /tools/rigging/jobs/[jobId]

Purpose:
Main operational workspace.

### Desktop Layout
Left column:
- job info card
- point list

Main center:
- calculation cards attached to job
- notes
- timeline snippets

Right column:
- warnings summary
- readiness summary
- actions

### Mobile Layout
Stacked sections:
1. job info
2. point list
3. calculations
4. warnings
5. readiness card

### Key Cards
Job Info Card:
- title
- venue
- date
- owner
- status badge

Point List Card:
- point name
- intended load
- actual load
- verification badge

Calculation Card:
- calc type
- main value
- warnings count
- open details

Readiness Card:
- ready for review: yes/no
- ready for signoff: yes/no
- missing items list

Primary actions:
- Add Point
- Add Calculation
- Verify Points
- Review Signoff Readiness

---

## Screen E — Point Verification
Route:
- /tools/rigging/jobs/[jobId]/verify

Purpose:
Field verification workflow.

### Layout
Top summary strip:
- job title
- points complete count
- unresolved issues count

Point verification list:
Each point card shows:
- point label
- intended load
- actual load field
- verification status control
- issue note field
- issue severity badge if present

Verification status options:
- pending
- installed
- checked
- loaded
- blocked
- discrepancy

Bottom action bar:
- Save Progress
- Mark Next Point
- Review Issues

### Critical UX Rule
Verification must be extremely fast.
This screen is designed for gloved hands and rushed environments.

---

## Screen F — Signoff Readiness
Route:
- /tools/rigging/jobs/[jobId]/signoff

Purpose:
Hard gate review screen before signoff.

### Layout
Header:
- Signoff Review
- current job status

Main sections:
1. readiness summary
2. blocking items
3. unresolved warnings
4. company policy checks
5. signoff action area
6. override area (only for authorized roles)

### Readiness Summary Card
Shows:
- calculations complete: yes/no
- point verification complete: yes/no
- critical issues resolved: yes/no
- policy checks passed: yes/no
- overall state badge

### Blocking Items Panel
If blocked:
- list every failed requirement
- each item tappable to open related screen

### Signoff Action Area
If ready:
- role selector (if needed)
- Sign Off button

If not ready:
- Sign Off disabled
- Override section visible only to authorized users

---

## Screen G — Override Dialog / Panel
Purpose:
Controlled exception workflow.

### Layout
Header:
- Override Signoff

Fields:
- override severity selector
  - minor
  - major
  - critical
- mandatory reason textarea
- unresolved items summary
- confirmation checkbox

Action buttons:
- Cancel
- Submit Override

### Visual Rules
- override screen must feel serious
- critical override must have strong visual treatment
- cannot look like a convenience shortcut

### Confirmation copy style
- plain
- accountable
- explicit

Example:
"You are approving signoff with unresolved items. This action will be permanently recorded in job history and reports."

---

## Screen H — Report Preview
Route:
- /tools/rigging/jobs/[jobId]/report

Purpose:
Preview exported report pack.

### Layout
Sections:
- job summary
- points summary
- calculations summary
- warning summary
- verification summary
- signoff status
- override status
- export button

### Override visibility
If override exists:
- prominent override banner
- severity clearly shown
- reason shown
- actor shown

---

## Screen I — Company Policies
Route:
- /company/tools/rigging/policies

Purpose:
Manage company enforcement rules.

### Layout
Sections:
1. safety factor defaults
2. angle thresholds
3. required checks before signoff
4. approved equipment references
5. override permission rules

### Cards
Each policy group appears in its own settings card.

### Primary actions
- Save Policy Changes
- Restore Defaults

---

## Screen J — Equipment Library
Route:
- /tools/rigging/library/equipment
- /company/tools/rigging/library

Purpose:
Reference and approved gear records.

### Layout
Search bar
Filter chips
Equipment cards

Each equipment card:
- name
- category
- WLL reference
- source / manufacturer reference
- approval badge where relevant

---

# 5. Status System in UI

## Job Status Badges
- Draft
- In Progress
- Ready for Review
- Ready for Signoff
- Locked
- Override Signed Off

## Warning Status
- Info
- Warning
- Critical

## Override Status
- Minor Override
- Major Override
- Critical Override

Override badges must always remain visible in:
- job header
- report preview
- history timeline

---

# 6. Interaction Patterns

## Safe Calculation Pattern
1. enter values
2. press calculate
3. get result
4. see warnings
5. optionally save to job

## Verification Pattern
1. open verify screen
2. update point state
3. capture discrepancy if needed
4. save

## Signoff Pattern
1. open signoff page
2. review readiness summary
3. if clean: sign off
4. if blocked: either fix issues or open override flow

## Override Pattern
1. authorized role opens override
2. selects severity
3. enters reason
4. confirms
5. system records audit + flags reports

---

# 7. Mobile UX Rules

- buttons minimum thumb-friendly height
- no dense tables on mobile
- use cards and stacked sections
- keep primary action persistent at bottom where possible
- avoid modal overload
- warnings must remain readable without zooming

---

# 8. Desktop UX Rules

- support multi-column operational view
- preserve right-side summary rail for readiness and warnings
- keep important state visible without scrolling away from work area

---

# 9. Empty States

## No Jobs Yet
Show:
- Create New Job button
- Start Quick Calculation button
- short explanation

## No Calculations Yet
Show:
- Add First Calculation button

## No Points Yet
Show:
- Add First Point button

## Not Ready for Signoff
Show:
- exact reasons
- direct actions to resolve them

---

# 10. Error States

## Calculation Error
- invalid input message near field
- do not crash the page

## Save Failure
- sticky inline error
- retry action

## Unauthorized Override Attempt
- explicit access denied message
- no silent failure

---

# 11. Real UI Component Inventory

## Shared Components
- status badge
- warning banner
- metric result tile
- point card
- calculation card
- readiness checklist panel
- override banner
- sticky bottom action bar

## Specialized Components
- angle warning strip
- signoff gate card
- override confirmation card
- company policy card
- verification quick-toggle row

---

# 12. Real UX Rule

The UI must always answer these questions instantly:
- What am I looking at?
- Is it safe, warning, or critical?
- What do I do next?
- Can this be signed off?
- If not, why not?

---

# 13. Final UI Standard

If the interface does not feel usable during a real load-in, it fails.

If the override flow feels casual, it fails.

If the signoff state is unclear, it fails.
