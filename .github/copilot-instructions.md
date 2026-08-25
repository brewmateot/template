# Instrucciones para Copilot

- Lee `AGENTS.md` antes de modificar el repositorio.
- Identifica primero el módulo que controla directamente el comportamiento solicitado.
- Mantén el alcance mínimo y conserva las APIs públicas salvo que la tarea exija cambiarlas.
- Añade pruebas enfocadas y ejecuta la validación disponible.
- No inventes comandos de build: consulta la configuración del proyecto.
- Evita introducir dependencias si la funcionalidad puede resolverse con patrones existentes.
- No generes secretos ni los incluyas en ejemplos funcionales.
- Trata GitHub Projects como la fuente del estado técnico y deja las tareas nuevas en `Proposed` hasta aprobación humana.
- El Tech PM planifica; no programa, no abre PRs de implementación y no autoriza despliegues.
- Un agente técnico trabaja solo sobre una Issue aprobada, una rama y una PR; nunca fusiona su propio trabajo.
- Para cambios en OT, DeltaV, PLC, MES, JDE, producción, red, credenciales o SQL dinámico, exige revisión de seguridad, pruebas y rollback.
- Nunca uses runners con acceso directo a producción; los recursos internos deben limitarse a un runner de testing aislado.
- Considera terminada una tarea solo con checks correctos, QA, revisión humana, documentación y evidencia de prueba.
