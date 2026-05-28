Para la introducción pública, consulta el [sitio de Doctor Bones en GitHub Pages](https://lightrock.github.io/drbones/).

# Doctor Bones

Doctor Bones es una plantilla de repositorio independiente del proveedor para desarrollo asistido por IA.

Te ayuda a mantener la memoria del proyecto dentro del repositorio en vez de atrapada en el chat. Le da a tu equipo humano/IA una disciplina operativa compartida: órdenes de trabajo, playbooks, ejemplos, comprobaciones, reglas de traspaso y hábitos de preparación para releases.

La idea es que, cada vez que empieces un proyecto nuevo, empieces con un Doctor Bones.

No necesariamente tienes que obtener tu copia de esta plantilla en tu PC local o entorno de agente para usarla. Doctor Bones lleva su arquitectura cognitiva en el propio repositorio. Si sigues las instrucciones de inicio de abajo, tu IA de primer plano debería tener suficiente inteligencia del proyecto para razonar a partir de la guía del repositorio, los ejemplos, los playbooks, las comprobaciones y las reglas de traspaso.

Por defecto, nada tiene que "ejecutarse" en ningún lugar de la forma tradicional, y no necesariamente tienes que invocar a un ejecutor como Codex. Primero apunta tu IA de primer plano a la instancia adecuada de repositorio basada en Doctor Bones. Usa un ejecutor solo cuando la tarea necesite ediciones de archivos, un entorno de ejecución, comprobaciones, commits o pull requests.

## Más sobre la idea

Antes de que la IA programe, enseña al repositorio a hablar. Antes de que la IA diga que terminó, define qué significa terminado. Antes de que la IA recomiende, separa evidencia de conclusión. Antes de que la IA parche, define autoridad, verificación y reglas de frontera.

¿Podemos definir estándares nativos del repositorio que Cursor, Codex, Claude Code, Copilot... y los bots de GitHub deban obedecer?

¿Podemos hacer que sea fácil adaptarlo a tus necesidades específicas?

## En progreso / TODO / POR TERMINAR

Consulta [TODO.md](../../TODO.md) para ver la lista aproximada de lo que todavía debe convertirse en archivos del repositorio, esquemas, rúbricas, ejemplos, comprobaciones e integraciones objetivo.

## Idiomas

- [English](../../README.md)
- Español: este archivo
- [Français](README.fr.md)
- [Deutsch](README.de.md)
- [Português do Brasil](README.pt-BR.md)
- [हिन्दी](README.hi.md)

## Qué es esto

Es una capa de disciplina nativa del repositorio para usar asistentes de IA y agentes de programación sin perder intención, restricciones, comprobaciones ni historial del proyecto.

El modelo básico es:

```text
intención humana
→ la IA de primer plano aclara la tarea
→ el repositorio captura guía duradera
→ la IA ejecutora realiza trabajo acotado
→ las comprobaciones verifican lo verificable
→ la finalización se conecta de nuevo con la intención fuente
```

Piensa en la IA de primer plano como el asistente de planificación y arquitectura. Piensa en la IA ejecutora como el trabajador con acceso a archivos, un entorno de ejecución, pruebas y herramientas de commit/PR.

El repositorio es la capa de memoria y disciplina entre ambos.

## Primeros pasos

1. Si copiaste esta plantilla, reescribe pronto este README alrededor de tu proyecto real.
2. Lee [`examples/README.md`](../../examples/README.md) para ver los ejemplos de flujo de trabajo day-in-the-life.
3. Lee [`readme_pmp.md`](../../readme_pmp.md) al menos una vez y tenlo a mano.
4. Lee [`AGENTS.md`](../../AGENTS.md) antes de pedir a un asistente de IA que cambie el repositorio.
5. Usa una orden de trabajo para trabajo sustancial, de múltiples archivos, sensible a la arquitectura o sensible al proceso.
6. Ejecuta las comprobaciones disponibles antes de tratar el trabajo como completo.

## Límite del proceso

No crees las órdenes de trabajo de tu proyecto en el repositorio fuente público de Doctor Bones a menos que estés contribuyendo intencionalmente a Doctor Bones mismo.

Para tu propio proyecto, primero crea o usa tu propio repositorio a partir de esta plantilla. Luego apunta tu IA de primer plano a la URL de ese repositorio de proyecto y crea allí las órdenes de trabajo.

Usa `lightrock/drbones` como plantilla fuente, implementación de referencia y proyecto upstream. Usa tu repositorio copiado basado en Doctor Bones como el lugar donde viven la memoria de tu proyecto, las órdenes de trabajo, las lecciones aprendidas y los cambios específicos del proyecto.

## Prompt de inicio para la IA de primer plano

Este prompt es para un repositorio creado a partir de la plantilla Doctor Bones. Después de copiar esta plantilla, reemplaza `<your project repository URL>` con la URL de tu propio repositorio de proyecto.

Cuando inicies un nuevo chat o pestaña para el repositorio de tu proyecto, pega esto en la IA de primer plano:

```text
You are the foreground AI for <your project repository URL>.

Current repo state beats chat memory. Inspect the current project repository before giving
architecture advice, writing workorders, or suggesting repo changes.

Read README.md, examples/README.md, readme_pmp.md, AGENTS.md, and the relevant folder
guidance from the project repository first. Then identify current state, target, constraints,
foreground/executor decision, and the smallest useful next move.
```

## Atajo de orden de trabajo

Para trabajo sustancial en tu repositorio de proyecto copiado, habla con la IA de primer plano hasta que la tarea esté clara, luego di:

```text
Create a workorder and also show it to me here.
```

Puedes copiar un enlace al archivo de la orden de trabajo y decirle a tu IA ejecutora, trabajando en un entorno para el repositorio de tu proyecto, que la realice.

También puedes copiar/pegar el cuerpo de la orden de trabajo si le pediste a la IA de primer plano que lo mostrara primero. Mantén limpio ese bloque de copiar/pegar: sin citas, notas del asistente, explicaciones, enlaces extra ni comentarios dentro del cuerpo de la orden de trabajo.

## Comprobaciones

Ejecuta estos comandos desde la raíz del repositorio cuando estén disponibles:

```text
python tools/pmp_check.py --area all
python -m pytest
```

Si una comprobación falla, pega la salida exacta del comando en la IA de primer plano y pide la corrección segura más pequeña.
