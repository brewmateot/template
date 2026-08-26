# Engineering Workflow

## Status: Proposed

Meaning:
The Tech PM has analyzed the request and prepared the work.

Allowed actions:
- Tech PM may create or update the Issue.
- No implementation agent may start development.

Exit condition:
- Human approval.
- Acceptance criteria defined.
- QA strategy defined.
- Dependencies identified.

Next status:
Ready

---

## Status: Ready

Meaning:
The work has been approved by the human owner and is ready for implementation.

Allowed actions:
- Implementation agent may start.
- Human may manually take ownership.

Exit condition:
- Implementation work has started.

Next status:
In Progress

---

## Status: In Progress

Meaning:
An implementation agent or human is actively working on the task.

Requirements:
- Dedicated branch.
- Changes linked to the Issue.
- Tests created/updated.
- Scope must remain within the Issue.

Next status:
In Review

---

## Status: In Review

Meaning:
Implementation is complete and a Pull Request is open.

Requirements:
- PR linked to Issue.
- CI passing.
- Tests executed.
- Implementation summary provided.

Next status:
QA

---

## Status: QA

Meaning:
The implementation is ready for functional and regression validation.

Requirements:
- Acceptance criteria verified.
- Automated tests passing.
- Manual validation performed when required.

Next status:
Done

---

## Status: Done

Meaning:
The task is completely finished.

Requirements:
- PR merged.
- QA completed.
- Documentation updated when required.
