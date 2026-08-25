# AGENTS.md

## Purpose

This repository contains a technical project managed through GitHub Issues, Pull Requests, GitHub Projects, and automated QA.

Agents must work within the scope defined by the GitHub Issue assigned to them and must not silently expand the scope.

## General principles

- Prefer simple, maintainable solutions over unnecessary complexity.
- Read the existing code and documentation before making changes.
- Reuse existing patterns and components whenever possible.
- Do not introduce breaking changes without explicitly documenting them.
- Do not modify unrelated code.
- Do not remove existing functionality unless the Issue explicitly requires it.
- Never assume that production access or production execution is allowed.
- Never commit credentials, secrets, tokens, passwords, certificates, or sensitive operational information.

## Before making changes

The agent must:

1. Read the assigned GitHub Issue completely.
2. Inspect the relevant repository structure.
3. Read applicable documentation.
4. Identify dependencies and potential side effects.
5. Determine how the requested change can be tested.
6. Confirm that the implementation remains within the Issue scope.

If the requirements are ambiguous, document the assumption in the Pull Request rather than silently making a major design decision.

## Implementation

When implementing a task:

- Create a dedicated branch.
- Keep changes focused on the Issue.
- Follow the repository's existing coding conventions.
- Add or update automated tests whenever practical.
- Update documentation when behavior or interfaces change.
- Prefer incremental, reviewable changes.
- Do not bypass validation because a change appears trivial.

## Testing

Before opening a Pull Request:

- Run the project's documented build and test commands.
- Run linting/static analysis where available.
- Verify the acceptance criteria from the Issue.
- Test relevant failure and edge cases.
- Check that unrelated functionality has not regressed.

If a test cannot be executed, explicitly state:

- why it could not be executed;
- what was tested instead;
- what remains to be validated.

Never claim a test passed when it was not actually executed.

## Production and operational systems

For changes affecting production systems, OT systems, databases, integrations, SCADA, MES, PLCs, infrastructure, or external services:

- Do not execute production changes unless explicitly authorized.
- Prefer test or staging environments.
- Identify operational risks before implementation.
- Provide a rollback procedure.
- Document prerequisites and dependencies.
- Clearly distinguish simulated/test validation from production validation.

Agents must never infer production authorization from the existence of credentials or connectivity.

## Pull Requests

Every implementation Pull Request must contain:

- Summary of the change.
- Link to the GitHub Issue.
- Technical approach.
- Files/components affected.
- Tests executed.
- Test results.
- Known limitations.
- Risks and possible side effects.
- Deployment considerations.
- Rollback procedure when applicable.

## Definition of Done

A technical task is considered complete only when:

- Acceptance criteria are satisfied.
- Automated tests and required checks pass.
- Documentation is updated where necessary.
- No secrets have been introduced.
- The Pull Request is reviewable.
- Required human approvals have been obtained.
- Deployment/rollback considerations are documented when applicable.

## Agent limitations

Agents must not:

- Merge their own Pull Requests unless explicitly authorized by repository policy.
- Disable required CI checks to make a Pull Request pass.
- Remove tests merely to obtain a passing pipeline.
- Change security controls without explicit authorization.
- Modify production systems without explicit authorization.
- Expand the scope of an Issue without documenting it.
- Hide failed tests, warnings, or known limitations.

## Communication style

Use concise technical language.

When reporting work, clearly separate:

- Implemented
- Tested
- Not tested
- Risks
- Remaining work
