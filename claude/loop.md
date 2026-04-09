# Loop

```
/loop 30m

## AUTONOMOUS PROJECT ADVANCEMENT LOOP

### 1. ORIENT (first 2 minutes)
- Read `projects/{{project_slug}}/handoff.md` to identify the current phase, completed phases, and next incomplete phase.
- Read `.planning/STATE.md` to confirm current state, blockers, and any pending decisions.
- Cross-check: if handoff.md and STATE.md disagree on current phase, trust handoff.md and update STATE.md to match.
- Identify the ONE next incomplete phase. Do not skip ahead or work on multiple phases.

### 2. EXECUTE (bulk of the cycle)
- Work exclusively on the next incomplete phase identified in step 1.
- Follow the phase's requirements, acceptance criteria, and deliverables exactly as documented in handoff.md.
- After each meaningful unit of work (function complete, section written, config applied), verify it works:
  - Code changes: run existing tests, lint, or do a quick smoke test.
  - Documentation: confirm all links/references are valid.
  - Config changes: validate syntax.
- Track what you accomplished and what remains in scratch notes.

### 3. EVALUATE COMPLETION
A phase is COMPLETE only when ALL of its documented acceptance criteria are met. If the phase has no explicit acceptance criteria, it is complete when all listed deliverables exist and pass basic validation.

If the phase is NOT complete but the 30-minute cycle is ending:
- Document exactly where you stopped and what remains.
- Mark the phase as IN_PROGRESS (not complete).

### 4. BLOCKER PROTOCOL
If you encounter any of these, STOP working on the phase immediately:
- Missing dependency (API key, credential, external service, package not installable)
- Ambiguous requirement that could be interpreted 2+ ways with materially different outcomes
- A failing test or error you cannot resolve after 3 distinct attempts
Action: Log the blocker in handoff.md under `## Blockers`, update STATE.md status to BLOCKED, and proceed to step 5. Do NOT attempt workarounds that compromise quality.

### 5. COMMIT & PUSH
- Stage only files related to the current phase's work.
- Commit with message format: `[{{project_slug}}] Phase {{phase_number}}: {{brief_description}}`
  - Example: `[petrostar-compliance] Phase 3: implement audit logging middleware`
- If work is partial: `[{{project_slug}}] Phase {{phase_number}} (WIP): {{brief_description}}`
- Push to all configured remotes: `git push --all`
- If push fails, log the error in handoff.md and continue to step 6.

### 6. UPDATE HANDOFF
Update `projects/{{project_slug}}/handoff.md`:
- Mark completed phases with ✅ and completion timestamp.
- Update current phase status (COMPLETE / IN_PROGRESS / BLOCKED).
- Add a `## Last Cycle Summary` section at the top with:
  - Timestamp
  - Phase worked on
  - What was accomplished (bullet list, 3-6 items)
  - What remains (if incomplete)
  - Blockers (if any)
- Update `.planning/STATE.md` to match.

### 7. CLIENT STATUS EMAIL
Create a file at `projects/{{project_slug}}/comms/status-{{date}}.md` with this structure:
```