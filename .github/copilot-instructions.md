# Copilot Instructions

## Role

You are working in a professional software engineering repository.

Prioritize correctness, maintainability, traceability, security, and testability over speed.

## Working model

All development work is driven by GitHub Issues.

Before making code changes:

1. Read the Issue.
2. Understand the acceptance criteria.
3. Inspect the existing implementation.
4. Identify dependencies and side effects.
5. Determine the appropriate tests.
6. Make the smallest safe change that satisfies the requirement.

Do not implement requirements that are not part of the assigned Issue unless they are necessary to make the requested change work. Document such cases.

## Code quality

Prefer:

- Small focused changes.
- Existing project conventions.
- Explicit and readable code.
- Reusable functions/components.
- Strong validation of external input.
- Meaningful error handling.
- Deterministic behavior.
- Automated tests.

Avoid:

- Unnecessary abstractions.
- Duplicate logic.
- Hidden side effects.
- Hard-coded environment-specific values.
- Silent failure.
- Dead code.
- Commenting obvious code instead of improving readability.

## Testing requirements

Every technical change should have an appropriate validation strategy.

Depending on the project, this may include:

- Unit tests.
- Integration tests.
- End-to-end tests.
- Static analysis.
- Linting.
- Type checking.
- SQL validation.
- Configuration validation.
- Golden-file comparison.
- Regression tests.

When fixing a bug, prefer adding a regression test that reproduces the original failure.

## Database changes

For SQL/database work:

- Prefer idempotent scripts where practical.
- Explicitly consider transaction boundaries.
- Validate data types.
- Avoid destructive operations without explicit justification.
- Consider concurrency and duplicate execution.
- Consider rollback.
- Never embed credentials in scripts.
- Do not assume the production database is safe to test against.

## External integrations

For APIs, databases, JDE/AS400, MES, SCADA, OPC, historians, or other external systems:

- Treat external systems as unreliable dependencies.
- Validate inputs and outputs.
- Handle timeouts and failures explicitly.
- Avoid unbounded retries.
- Document assumptions about external behavior.
- Include test doubles/mocks where practical.

## OT / industrial systems

When a change affects industrial automation or operational technology:

- Treat availability and safety as first-class requirements.
- Prefer offline, simulation, or test validation.
- Do not execute production operations automatically.
- Do not modify PLC, SCADA, MES, DeltaV, or production infrastructure unless explicitly authorized.
- Include rollback and recovery considerations.

## Security

Never:

- Commit secrets.
- Log credentials or tokens.
- Disable TLS verification just to make a test work.
- Bypass authentication for convenience.
- Reduce security controls without explicit authorization.

Flag suspicious or insecure existing behavior when relevant to the assigned Issue.

## Documentation

Update documentation when changes affect:

- Architecture.
- Configuration.
- APIs.
- Operational procedures.
- Deployment.
- Troubleshooting.
- User-facing behavior.

## Pull Request expectations

Before opening a Pull Request, verify:

- Build succeeds where applicable.
- Tests pass.
- Static checks pass.
- Acceptance criteria are satisfied.
- Documentation is updated where necessary.
- No unrelated files were modified.

The Pull Request description must accurately report what was and was not tested.

Never state that a command or test was executed unless it actually was.

## Decision making

When several technically valid solutions exist:

1. Prefer the least complex solution.
2. Prefer consistency with the existing architecture.
3. Prefer solutions that are easy to test and rollback.
4. Prefer reversible changes.
5. Document important trade-offs.

When uncertainty is significant, stop and explain the uncertainty rather than inventing facts.
