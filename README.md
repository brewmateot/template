# Template para proyectos gestionados con Codex

Punto de partida para que Codex actúe como PM técnico: convierte una petición en Issues, las incorpora al Project compartido, pide aprobación antes de implementar y coordina implementación, revisión y QA.

## Cómo funciona

- `AGENTS.md`: instrucciones principales del PM técnico que Codex carga al abrir el repositorio.
- `.codex/config.toml`: activa subagentes y configura el servidor MCP de GitHub.
- `.codex/agents/`: especialistas de implementación, QA y seguridad en formato TOML de Codex.
- `.github/workflow.md`: estados y condiciones del ciclo de trabajo.
- `.github/workflows/add-to-project.yml`: añade automáticamente Issues nuevas al [Project #2](https://github.com/users/brewmateot/projects/2).
- `docs/`: arquitectura, operación, plan de pruebas y ADRs.

No hay frontmatter YAML: los antiguos agentes de GitHub Copilot se han sustituido por la configuración nativa de Codex.

## Primera puesta en marcha

1. Crea un repositorio nuevo usando este repositorio como template.
2. Abre el repositorio nuevo en Codex y reinicia la extensión/sesión para que cargue `AGENTS.md` y `.codex/config.toml`.
3. Autentica el servidor MCP `github` desde la configuración de MCP de Codex. En CLI también puedes usar `codex mcp login github`.
4. En el repositorio nuevo, crea el secret de Actions `ADD_TO_PROJECT_PAT`. Los secrets no se copian desde un template. El token debe poder escribir en el Project; para repositorios privados también necesita acceso al repositorio.
5. Comprueba que el Project #2 contiene los estados `Proposed`, `Ready`, `In Progress`, `In Review`, `QA`, `Blocked` y `Done` con esa ortografía.

La configuración de rulesets, revisores y Environments se detalla en [docs/governance.md](docs/governance.md).

## Prueba recomendada en Codex

Abre el repositorio nuevo y escribe:

> Quiero añadir una página de estado sencilla. Primero analiza el repositorio, crea las Issues necesarias y añádelas al Project en Proposed. No implementes nada hasta enseñarme la propuesta y pedirme aprobación. Usa los subagentes del repositorio cuando corresponda.

El resultado esperado es:

1. Codex inspecciona el repositorio y pregunta solo lo imprescindible.
2. Crea y verifica las Issues y las deja en `Proposed`.
3. Se detiene y pide aprobación explícita.
4. Tras aprobar una Issue, la mueve por `Ready` e `In Progress`, implementa en una rama y abre una Pull Request.
5. Coordina QA y solo considera `Done` el trabajo ya fusionado y validado.

Si Codex indica que no puede escribir en GitHub o en Projects, revisa la autenticación y los permisos del servidor MCP. No continúes la prueba dando por hecho que los estados se han actualizado.

## Desarrollo local

El template no fija un lenguaje o framework. Documenta aquí los requisitos de instalación y los comandos de desarrollo, pruebas, lint y build cuando empiece el proyecto.
