# AGENTS.md

## Objetivo

Este repositorio es la unidad mantenible de un producto o aplicación. GitHub es el sistema central para el código, Issues, Pull Requests, revisiones, automatización y estado técnico.

## Reglas de trabajo

- Mantén los cambios pequeños y enfocados en el objetivo de la tarea.
- Respeta las convenciones existentes antes de introducir nuevas abstracciones.
- Añade o actualiza pruebas para cada cambio de comportamiento.
- Actualiza la documentación cuando cambien interfaces, operación o decisiones de arquitectura.
- No incluyas secretos, credenciales ni datos personales en el repositorio.
- Ejecuta las comprobaciones relevantes antes de abrir un pull request.
- No mezcles código corporativo, exportaciones DeltaV/FHX, topologías OT, nombres de servidores o proyectos personales.
- No otorgues a agentes acceso directo a DeltaV, PLC, MES productivo o SQL/JDE productivo.

## Flujo de trabajo

1. El agente `tech-pm` convierte una petición en una Issue con alcance, dependencias, riesgo, criterios de aceptación, pruebas, observabilidad, despliegue y rollback.
2. La Issue permanece en `Proposed` hasta la aprobación humana; solo entonces pasa a `Ready`.
3. El agente `implementer` trabaja en una rama, implementa, prueba y abre una Pull Request. No fusiona ni despliega.
4. CI y el agente `qa` validan el cambio. La revisión humana es obligatoria antes del merge.
5. Los despliegues a producción requieren un Environment protegido y aprobación humana independiente.

Estados recomendados para el Project: `Inbox`, `Triage`, `Proposed`, `Ready`, `In Progress`, `In Review`, `QA`, `Blocked` y `Done`.

## Definition of Ready

Una tarea no está lista para desarrollo hasta incluir problema, objetivo, alcance y fuera de alcance, criterios de aceptación verificables, dependencias, riesgo, plan de pruebas y estrategia de despliegue/rollback.

## Definition of Done

La PR está vinculada a la Issue, los checks pasan, QA y revisión humana están completados, la documentación y la evidencia de prueba están actualizadas, no hay secretos y el rollback está documentado cuando procede.

## Restricciones de alto riesgo

Cambios de credenciales, autenticación, SQL dinámico, archivos, APIs, red, firewall, despliegues, producción u OT requieren revisión de seguridad y aprobación humana. Las pruebas que necesiten red interna deben ejecutarse en un self-hosted runner aislado de producción, con mínimos privilegios.

## Estructura

- `src/`: implementación.
- `tests/`: pruebas automatizadas.
- `docs/architecture.md`: arquitectura y límites del sistema.
- `docs/runbook.md`: operación y respuesta a incidencias.
- `docs/test-plan.md`: estrategia y alcance de pruebas.
- `docs/adr/`: decisiones de arquitectura.
- `.github/`: plantillas, instrucciones y automatización.

## Pull requests

Cada PR debe explicar el problema, el cambio realizado, cómo se validó y cualquier riesgo o trabajo pendiente.
