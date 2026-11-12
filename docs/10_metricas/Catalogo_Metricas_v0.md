# Catálogo de métricas del producto — SAMed

ID: CI-901 · Versión: v0 · Fecha: 2026-11-12 · Dueño: Terry · Estado: En revisión (debe revisarlo el equipo completo antes de `lb-req-1.0`)
Responde al enunciado Fase 9 y §12. Se calcula en `v1.0.0` ("antes") y en `v1.1.0` ("después" del RFC-001).

## 1. Cómo leer este catálogo

- Enfoque GQM (objetivo → pregunta → métrica): cada métrica responde una pregunta de ingeniería y lleva a una decisión. Si una métrica no lleva a ninguna decisión, es decorativa y se quita (Fase 9).
- Regla de validez (§12): una métrica sin fuente, fórmula, unidad e interpretación no es evidencia cuantitativa.
- Los umbrales con "Sin dato" los fija el dueño indicado y se registran en acta. Los únicos umbrales ya escritos se derivan del enunciado (100 % de requisitos críticos demostrados, regresión completa) o de una regla del equipo (0 defectos críticos escapados). Ningún valor medido aparece aquí: todos los resultados son "Sin dato" hasta `v1.0.0`.

## 2. Objetivos y preguntas de ingeniería

| Objetivo | ID | Pregunta |
|---|---|---|
| G1. El proceso crítico PN-05 es confiable | Q1 | ¿La administración de dosis está disponible cuando enfermería la necesita? |
| | Q2 | ¿El sistema se recupera rápido de los fallos? |
| | Q3 | ¿La operación crítica responde en un tiempo aceptable, también después del MFA? |
| G2. Lo que se afirma está demostrado | Q4 | ¿Cada requisito crítico está respaldado por evidencia en la versión evaluada? |
| | Q8 | ¿Los controles de seguridad están verificados, no solo implementados? |
| G3. El proceso de construcción controla la calidad | Q5 | ¿Detectamos los defectos antes de la línea base? |
| | Q6 | ¿El módulo hecho con Cleanroom tiene menos defectos que el resto? |
| | Q9 | ¿Cuánto confiamos en lo que generan los agentes de IA? |
| G4. El cambio impuesto quedó controlado | Q7 | ¿El cambio de emergencia (MFA) rompió algo que ya funcionaba? |

## 3. Métricas

| ID | Pregunta | Nombre | Fórmula | Unidad | Fuente de datos | Umbral | Interpretación y decisión | Dueño | Se mide en |
|---|---|---|---|---|---|---|---|---|---|
| MET-001 | Q1 | Disponibilidad del proceso crítico | A = tiempo operativo / tiempo total de la ventana de medición (equivale a MTTF / (MTTF + MTTR)) | % | Monitor de salud del endpoint de administración de dosis + registro de inyección de fallos (CI-301) | ≥ objetivo del RNF de disponibilidad (Sin dato; lo fija Germán) | Por debajo del objetivo no se aprueba la línea base. En `v1.1.0` el MFA no debe bajarla (exigencia del RFC, §7) | Germán | `v1.0.0` y `v1.1.0` |
| MET-002 | Q2 | MTTF | Σ tiempo operativo entre fallos / n.º de fallos | min | Ídem MET-001 | Sin dato (Germán) | Muestra qué tan seguido falla el componente; el más frecuente se prioriza | Germán | `v1.0.0` y `v1.1.0` |
| MET-003 | Q2 | MTTR | Σ tiempo de recuperación / n.º de fallos | min | Logs del escenario de fallo y recuperación (CI-301) | Sin dato (Germán) | Si es alto, se mejora primero el procedimiento de recuperación | Germán | `v1.0.0` y `v1.1.0` |
| MET-004 | Q2 | MTBF | MTTF + MTTR | min | MET-002 y MET-003 | Sin dato (Germán) | Se reporta junto con MET-001, nunca como único indicador | Germán | `v1.0.0` y `v1.1.0` |
| MET-005 | Q3 | Tiempo de respuesta p95 de "registrar administración de dosis" | Percentil 95 de la latencia bajo una carga definida | ms | Prueba de carga k6 (CI-702) sobre la versión medida | Sin dato (Germán, en el RNF de rendimiento) | Si sube con el MFA por encima del umbral, el RFC-001 analiza si se acepta o se ajusta | Germán | `v1.0.0` y `v1.1.0` |
| MET-006 | Q4 | Cobertura de evidencia de requisitos críticos | n.º de requisitos críticos con veredicto "Demostrado" / n.º de requisitos críticos | % | Matriz maestra (CI-902) | 100 % para dictamen favorable | Menos de 100 %: el dictamen lista qué requisito no está demostrado y por qué | Terry | `v1.0.0` y `v1.1.0` |
| MET-007 | Q5 | Eficiencia de eliminación de defectos (DRE) | Defectos eliminados antes de `v1.0.0` / (eliminados antes de `v1.0.0` + encontrados después) | % | Issues con etiqueta `defecto` (versión de origen y de detección) y registro ERR (CI-811) | Sin dato (Terry) | DRE baja: se refuerzan las revisiones o pruebas de la actividad donde se inyectaron | Terry | `v1.1.0` |
| MET-008 | Q5 | Defectos críticos escapados a la línea base | n.º de DEF críticos detectados después de `v1.0.0` cuyo origen ya estaba en `v1.0.0` | defectos | Issues `defecto` con versión de origen | 0 (regla del equipo) | Uno o más: se revisa la auditoría de esa línea base y se registra ERR/LEC | Terry | `v1.1.0` |
| MET-009 | Q6 | Densidad de defectos: módulo Cleanroom frente al resto | DEF del módulo / tamaño del módulo, comparada con DEF del resto / tamaño del resto | DEF/KLOC | Issues `defecto` + conteo de líneas con `cloc` | Sin umbral: es comparativa | Evidencia cuantitativa del análisis Cleanroom frente a detección y corrección. Unidad de tamaño por confirmar con Juan | Terry con Juan | `v1.0.0` |
| MET-010 | Q7 | Éxito de la regresión tras el MFA | Casos de regresión que pasan en `v1.1.0` / casos de regresión ejecutados | % | Registro de ejecuciones (CI-703) | 100 % | Menos de 100 %: el RFC-001 no se cierra ni se crea `v1.1.0` | Terry | `v1.1.0` |
| MET-011 | Q8 | Controles de seguridad verificados | CTL con al menos una prueba de seguridad pasada en la versión / CTL vigentes | % | Matriz de seguridad (CI-203) + ejecuciones (CI-703) | 100 % de los controles de riesgos altos (criterio a confirmar por Neyls) | Un control sin prueba se reporta como riesgo residual | Neyls | `v1.0.0` y `v1.1.0` |
| MET-012 | Q9 | Errores de origen agente | ERR con origen "agente" / ERR totales | % | Registro de errores y lecciones (CI-811) | Sin umbral: orienta reglas de prompt | Si crece, se agregan reglas a `AGENTS.md` y a la plantilla de prompt | Terry | `v1.0.0` y `v1.1.0` |

## 4. Resultados

| ID | `v1.0.0` | `v1.1.0` | Variación | Evidencia |
|---|---|---|---|---|
| MET-001 a MET-012 | Sin dato | Sin dato | Sin dato | Sin dato |

Los resultados se registran con su evidencia `EVI-MET-NNN` y la hoja de cálculo exportada; el cálculo lo hace el script CI-704.

## 5. Pendientes

| Pendiente | Quién |
|---|---|
| Revisión del catálogo por los 4 (criterio de `lb-req-1.0`) | Juan, Germán, Neyls, Terry |
| Umbrales de MET-001 a MET-005 y ventana de medición de disponibilidad | Germán |
| Criterio de "riesgo alto" para MET-011 | Neyls |
| Unidad de tamaño para MET-009 (KLOC u otra) | Juan |
