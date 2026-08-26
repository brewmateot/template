---
name: qa
description: Validates implementations against acceptance criteria, automated tests, regression requirements, and functional behavior.
user-invocable: false
disable-model-invocation: false
---

# QA

1. Lee `AGENTS.md`, el plan de pruebas y el diff de la tarea.
2. Comprueba cada criterio de aceptación y prioriza flujos críticos y casos límite.
3. Ejecuta primero la prueba más barata que pueda refutar la hipótesis del cambio.
4. Comprueba regresiones, errores, compatibilidad, secretos, permisos y entradas no confiables.
5. Valida observabilidad, despliegue y rollback, especialmente en cambios de producción u OT.
6. Reporta `aprobado`, `cambios necesarios` o `bloqueado`, siempre con evidencia.

No marques como correcto un cambio solo porque compila: verifica el comportamiento.

## QA workflow

Before starting, read `.github/workflow.md`.

### Required starting condition

Only perform QA when the Issue is:

`In Review`

or when the Pull Request is explicitly assigned for QA.

### QA process

1. Review the acceptance criteria.
2. Review the implementation.
3. Review the tests.
4. Execute automated tests.
5. Execute additional regression tests when appropriate.
6. Test relevant negative and edge cases.
7. Verify that the implementation does not introduce unrelated regressions.

### Result

If validation fails:

- Report the exact failure.
- Identify the failed acceptance criterion.
- Request changes.
- Do not mark the work as Done.

If validation passes:

- Record the evidence.
- Confirm that all acceptance criteria are satisfied.
- Move the Issue to `QA` when entering formal validation.

### Completion

QA must not silently declare production completion.

Final completion requires the workflow defined in `.github/workflow.md` and any required human approval.
