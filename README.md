# Discovery System - Continuous Discovery con Claude Code

Un sistema completo para hacer **Continuous Discovery** que realmente funciona.

Convierte transcripciones de entrevistas en insights accionables y mantiene tu Opportunity Solution Tree actualizado automáticamente.

## ¿Qué es esto?

Este es un sistema file-based que usa Claude Code como tu "discovery assistant".

En lugar de que tus insights de usuarios vivan dispersos en Google Drive, Notion, y Slack, este sistema:
- Centraliza todas tus transcripciones en un solo lugar
- Analiza patterns automáticamente
- Actualiza tu Opportunity Solution Tree basado en evidencia real
- Conecta cada decisión con insights específicos (trazabilidad)

## ¿Por qué necesito esto?

La mayoría de equipos fallan en discovery continuo no porque no hablen con usuarios, sino porque:
- ❌ Las transcripciones se quedan en archivos que nadie vuelve a leer
- ❌ Los insights no conectan con decisiones
- ❌ El Opportunity Solution Tree se actualiza una vez al trimestre (si acaso)
- ❌ No hay trazabilidad: "¿Por qué construimos esto?" → "Parecía importante"

Este sistema soluciona eso.

## Setup (30 minutos)

### Paso 1: Clonar el Repo

```bash
git clone https://github.com/danielmedinac22/discovery-system
cd discovery-system
```

### Paso 2: Configurar Tu Contexto (10 minutos)

Edita los archivos en `context/`:

**`context/business-context.md`:**
- Describe tu producto
- Define tu usuario target
- Explica el problema que resuelves
- Contexto competitivo

**`context/business-outcome.md`:**
- Define tu outcome actual (métrica específica)
- Por qué importa
- Cómo se mide
- Timeframe

Ejemplo:
- Outcome: "Aumentar activación de 42% a 55% en Q1 2026"
- Por qué: "Activación predice retention"
- Medición: "Activación = 3+ acciones core en primeros 7 días"

### Paso 3: Subir Tu Primera Transcripción (5 minutos)

1. Transcribe una entrevista (usa Otter, Grain, Fireflies, o manual)
2. Guarda en `transcripts/YYYY-MM-DD-nombre-usuario.md`
3. Formato simple:

```markdown
# Entrevista: [Nombre] - [Rol en Empresa]
Fecha: YYYY-MM-DD

## P: [Tu pregunta]
R: [Respuesta del usuario]

## P: [Siguiente pregunta]
R: [Respuesta]
```

Ver `transcripts/EXAMPLE-2026-01-15-jane-doe.md` para un ejemplo completo.

### Paso 4: Activar Claude Code (2 minutos)

En la carpeta del proyecto:

```bash
claude code
```

Luego escribe:

```
"Analiza la última transcripción en transcripts/ y actualiza el Opportunity Tree en insights/opportunity-tree.md"
```

Claude:
1. Lee las reglas en `CLAUDE.md`
2. Lee tu contexto de negocio
3. Analiza la transcripción
4. Identifica opportunities basado en evidencia
5. Actualiza el Opportunity Tree
6. Te explica qué encontró y por qué

### Paso 5: Hacer Discovery Continuo (Cada Semana)

El flujo semanal:

1. Habla con un usuario (1 hora)
2. Sube transcripción a `transcripts/` (5 minutos)
3. Pide a Claude: "Analiza [archivo] y actualiza el tree" (2 minutos)
4. Revisa cambios en el Opportunity Tree (10 minutos)
5. Usa insights en tu próxima decisión de producto

**Total: ~1 hora 15 minutos por semana.**

## Estructura del Sistema

```
discovery-system/
├── README.md                    # Este archivo
├── CLAUDE.md                    # Instrucciones para Claude (el cerebro del sistema)
├── context/
│   ├── business-context.md     # Quién eres, qué construyes
│   └── business-outcome.md     # Qué estás tratando de lograr
├── transcripts/
│   ├── .gitkeep
│   └── EXAMPLE-2026-01-15-jane-doe.md  # Ejemplo de transcripción
└── insights/
    └── opportunity-tree.md      # Tu Opportunity Solution Tree (se actualiza automáticamente)
```

## Cómo Funciona

### El Flujo Completo

1. **Subes una transcripción** → `transcripts/`
2. **Claude lee tu contexto** → `business-context.md` + `business-outcome.md`
3. **Claude analiza la transcripción** siguiendo las reglas en `CLAUDE.md`
4. **Claude identifica opportunities** basado en:
   - Frecuencia (¿cuántos usuarios mencionan esto?)
   - Severidad (¿qué tan frustrante es?)
   - Conexión con tu outcome
5. **Claude actualiza el tree** → `insights/opportunity-tree.md`
6. **Tú revisas y decides** qué opportunity probar primero

### El Rol de Cada Archivo

| Archivo | Propósito | Actualización |
|---------|-----------|---------------|
| `CLAUDE.md` | Instrucciones de análisis | Una vez (al inicio) |
| `business-context.md` | Quién eres, qué construyes | Trimestral |
| `business-outcome.md` | Qué optimizas ahora | Cuando cambias objetivo |
| `transcripts/*.md` | Conversaciones con usuarios | Semanal (cada entrevista) |
| `opportunity-tree.md` | Opportunities + Solutions | Automático (Claude) |

## Ejemplos de Uso

### Caso 1: Identificar Opportunities

**Input:** 3 transcripciones subidas esta semana

**Comando:**
```
"Analiza las últimas 3 transcripciones y actualiza el Opportunity Tree"
```

**Output de Claude:**
- Opportunity 1: "Usuarios pierden contexto al regresar después de 2 días"
  - Mencionado por 3/3 usuarios
  - Pain level: Alto
  - Evidencia: [citas específicas]
- Opportunity 2: "No saben si sus comentarios fueron vistos"
  - Mencionado por 2/3 usuarios
  - Pain level: Medio

### Caso 2: Priorizar Opportunities

**Comando:**
```
"De todas las opportunities en el tree, ¿cuál tiene más evidencia y conexión con nuestro outcome actual?"
```

**Output de Claude:**
- Análisis de cada opportunity
- Recomendación basada en frecuencia + severidad + outcome fit
- Suggestion de solution para probar primero

### Caso 3: Generar Solution Ideas

**Comando:**
```
"Para la Opportunity 1, genera 5 solution ideas. Para cada una, explica esfuerzo estimado y probabilidad de resolver el problema"
```

**Output de Claude:**
- Lista de solutions
- Trade-offs de cada una
- Recomendación de cuál probar primero

## Troubleshooting

### "Claude no identifica opportunities"

Posibles causas:
- Tu `business-outcome.md` no está suficientemente específico
- Las transcripciones son muy cortas o vagas
- Necesitas más de 2-3 transcripciones para ver patterns

**Fix:** Define un outcome específico (métrica + número + timeframe) y sube al menos 3 transcripciones.

### "El tree no se actualiza correctamente"

Posibles causas:
- `CLAUDE.md` tiene reglas contradictorias
- El tree existente tiene formato inconsistente

**Fix:** Borra `insights/opportunity-tree.md` y deja que Claude lo regenere desde cero.

### "Las opportunities no conectan con decisiones"

Posibles causas:
- No estás revisando el tree semanalmente
- El equipo no participa en la revisión

**Fix:** Agenda 15 minutos cada semana para revisar el tree con el equipo. Pregunta: "¿Qué opportunity probamos esta semana?"

## Recursos

- **Artículo completo:** [Cómo Construir Un Sistema de Discovery Continuo Con Claude Code](https://productsystemscondaniel.substack.com/p/discovery-system-claude-code?r=2gv0d5)
- **Framework de discovery:** [La Diferencia Entre Hacer Discovery y Pretender Que Lo Haces](https://productsystemscondaniel.substack.com/p/la-diferencia-entre-hacer-discovery?r=2gv0d5)
- **Cómo tomar decisiones:** [El Sistema Completo Para Tomar Decisiones de Producto](https://productsystemscondaniel.substack.com/p/como-tomar-decisiones-de-producto?r=2gv0d5)
- **Claude Code:** [Claude No Le Ganó a OpenAI. Cambió el Juego](https://productsystemscondaniel.substack.com/p/claude-no-le-gano-a-openai-cambio?r=2gv0d5)

## Contribuciones

Si usas este sistema y descubres mejoras:
1. Abre un issue describiendo el problema o sugerencia
2. Si tienes una solución, envía un PR
3. Comparte tu experiencia en Twitter/LinkedIn mencionando [@danielmed_2](https://twitter.com/danielmed_2)

## Licencia

MIT License - Usa, modifica, y comparte libremente.

---

**¿Preguntas?** Abre un issue o escríbeme en [Twitter](https://twitter.com/danielmed_2).

Construido por [Daniel Medina](https://productsystemscondaniel.substack.com) - Product Manager que cree en sistemas, no en hype.
