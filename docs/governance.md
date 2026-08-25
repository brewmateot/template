# Gobierno de GitHub

Esta configuración se completa en la organización y no puede imponerse solo desde el repositorio.

## Organización y repositorios

- Mantén el código corporativo en una organización privada aprobada; separa los proyectos personales.
- Usa un repositorio por producto o conjunto mantenible, no uno por incidencia.
- No subas exportaciones DeltaV/FHX, topologías OT, nombres de servidores, credenciales o cadenas de conexión.

## GitHub Project

Crea un Project de organización para el portfolio técnico con estados `Inbox`, `Triage`, `Proposed`, `Ready`, `In Progress`, `In Review`, `QA`, `Blocked` y `Done`.

Campos recomendados: `Type`, `Priority`, `Area`, `Risk`, `Size`, `Environment`, `Executor`, `Iteration` y `Target date`. Mantén vistas de triage, ejecución, roadmap, QA y alto riesgo/producción.

La automatización de este repositorio permanece sin permisos de escritura hasta configurar el Project, una identidad de mínima autoridad y sus secretos en la organización.

## Ruleset de `main`

Configura un ruleset que exija:

- Pull Request obligatoria; push directo, force-push y borrado prohibidos.
- Checks de CI obligatorios y rama actualizada antes del merge.
- Al menos una aprobación humana y conversaciones resueltas.
- CODEOWNERS aplicado a cambios sensibles.
- Revisión adicional para producción u OT.

## Producción y runners

- Usa GitHub Environments protegidos con reviewers humanos y restricciones de rama.
- No permitas que quien inicia un despliegue sea su único aprobador.
- Ejecuta pruebas internas en un self-hosted runner aislado, con cuenta de servicio de mínimos privilegios y sin acceso directo a producción.
- No concedas a agentes permisos para descargar cambios a DeltaV, PLC, MES productivo o SQL/JDE productivo.

## Integraciones

GitHub es la fuente de verdad técnica. Añade Jira solo si una exigencia corporativa lo requiere, manteniendo Jira para iniciativa/portfolio y GitHub para Issues, código, pruebas y PRs. Evita una sincronización bidireccional completa.
