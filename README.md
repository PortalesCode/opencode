# Aetherium Agents

Ecosistema de agentes opencode para desarrollo de proyectos. Cloná esto en `.opencode/` de cualquier proyecto y tené un equipo completo de IA trabajando con vos.

## Quick start

```bash
# En la raíz de tu proyecto
git clone https://github.com/PortalesCode/agents.git .opencode

# Abrí opencode y hablá con Núcleo
opencode
```

Núcleo te va a guiar: scan del proyecto, configuración de hooks, indexación. Sin configuración manual.

## Cómo funciona

```
🗣️  Hablás con Núcleo
  ├── promt: {idea vaga} → desambiguación → pipeline completo
  ├── GPT: {recomendación} → crítica → arquitectura → plan → código → commit
  ├── implementa {cambio} → Mini-Orchestrator decide complejidad y ejecuta
  └── visión: {texto} → Vision conversa y estructura la visión

📦 Post-commit (automático)
  commit → hook → Chronicle (GRAPH.json) → Vision Tracker (GRAVITY_STATE.json)
```

## Agentes

### Primarios (aparecen en Tab)

| Agente | Rol |
|--------|-----|
| **Núcleo** | Hub conversacional. Con él hablás, él orquesta. |
| **Comodín** | Automatización CLI. No conversa, ejecuta órdenes desde scripts/hooks. |
| **Vision** | Define y estructura la visión del proyecto conversando con vos. |

### Subagentes (hidden, vía Task)

| Grupo | Agentes |
|-------|---------|
| **Visión** | `Vision Tracker` — cruza realidad (commits) vs visión (VISION.md) |
| **Ideas** | `Cartógrafo` — mapea ideas y conexiones. `Interprete-Prompt` — desambigua ideas vagas. |
| **Pipeline** | `Interprete-GPT`, `Arquitecto-de-Software`, `Cerebro`, `Descomponedor-de-tareas`, `Asignador-de-tareas` |
| **Ejecución** | `Mini-Orchestrator` — orquesta cambios según complejidad. `Ejecutor-Quirúrgico` — único que escribe código. |
| **Calidad** | `Inspector`, `Depurador-Codigo` |
| **Stack** | `Vanguardista` — guardián técnico del stack. |
| **Post-commit** | `Chronicle` — procesa commits. |
| **Docs/Git** | `Documentador`, `Maestro-de-Git` |
| **Registro** | `Project Feeder` — indexa el proyecto (local o global). |
| **Scan** | `Context-Speed` — escaneo rápido del entorno. |

## Graph files (`.opencode/graph/`)

| Archivo | Dueño | Qué contiene |
|---------|-------|-------------|
| `GRAPH.json` | Chronicle | Historial de commits |
| `GRAVITY_STATE.json` | Vision Tracker | Interpretación evolutiva del proyecto |
| `VISION.md` | Vision + vos | Propósito, features, stack (consolidado vs exploración) |
| `explore-tecnologias.json` | Vision | Tecnologías: consolidadas, en exploración, descartadas |
| `IDEA_GRAPH.json` | Cartógrafo | Ideas exploradas, mutaciones, descartes |
| `INTENT_GRAPH.json` | Interprete-Prompt + GPT | Patrones de lenguaje del usuario |
| `STACK.json` | Vanguardista | Stack real detectado en el proyecto |

## Requisitos

- [opencode](https://opencode.ai) instalado
- Opcional: un provider configurado (`/connect` en opencode)

## Notas

- La visión la define **siempre el usuario**. Ningún agente la inventa.
- `.opencode/` es la casa de los agentes. No se toca como código del proyecto.
- `node_modules/` está en `.gitignore`.
