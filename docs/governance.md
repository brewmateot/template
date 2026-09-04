# Gobierno de GitHub y Codex

Parte de esta configuración vive fuera del repositorio y debe completarse en cada proyecto creado desde el template.

## GitHub Project compartido

El PM técnico usa `https://github.com/users/brewmateot/projects/2` como tablero común. Debe tener los estados `Proposed`, `Ready`, `In Progress`, `In Review`, `QA`, `Blocked` y `Done`.

Campos recomendados: `Type`, `Priority`, `Area`, `Risk`, `Size`, `Environment`, `Executor`, `Iteration` y `Target date`. Mantén vistas de triage, ejecución, roadmap, QA y alto riesgo/producción.

El workflow `add-to-project.yml` incorpora Issues abiertas, reabiertas o transferidas. En cada repositorio generado configura el secret `ADD_TO_PROJECT_PAT`: los templates no copian secrets. Concédele únicamente el acceso necesario para añadir Issues al Project; si el repositorio es privado, el token también necesita acceso a él.

Codex usa el servidor MCP de GitHub definido en `.codex/config.toml` para crear Issues, comprobar el Project y actualizar estados. La primera sesión debe autenticarse y disponer de permisos de escritura sobre el repositorio y el Project.

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

## Datos y repositorios

- Mantén el código corporativo en una organización privada aprobada y separa proyectos personales.
- No subas exportaciones DeltaV/FHX, topologías OT, nombres de servidores, credenciales o cadenas de conexión.
- GitHub es la fuente de verdad técnica. Añade otra herramienta de portfolio solo cuando exista una necesidad clara y evita sincronizaciones bidireccionales innecesarias.
