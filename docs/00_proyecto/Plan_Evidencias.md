# Plan de evidencias — SAMed

Versión: v1 · 2026-11-12 · Regla del enunciado: sin evidencia verificable el requisito no está demostrado.

## 1. Cuándo se toman
**Durante el desarrollo, no al final.** Cada evidencia se toma en cuanto existe lo que prueba, sobre una versión identificada (commit o tag). Una evidencia tomada después, sobre otra versión, genera una inconsistencia crítica. Las instrucciones y evidencias de etapas cerradas se archivan en `99_Archivo/`; las evidencias válidas viven en el repo (`evidencias/<TIPO>/`) y se citan por ID.

## 2. Qué debe llevar cada evidencia
ID `EVI-TIPO-NNN`, versión evaluada (tag o commit corto), ambiente, fecha, comando o pasos para repetirla, resultado esperado vs obtenido, IDs que respalda (RF, RSK, TC, PRO…). Las capturas muestran URL o comando y no muestran secretos.

## 3. Evidencias previstas por etapa
| Etapa | Tipo | Qué se captura | Respalda |
|---|---|---|---|
| 1 | ENT | Instalación reproducible desde cero (clone, `docker compose up`, app corriendo); versiones de herramientas | RNF-10, 14.4 |
| 1 | GC | Protección de ramas, historial de PR, CODEOWNERS | Plan GC |
| 2 | CNF | Plan de inyección de fallos y datos base de MTTF/MTTR | RNF-05 |
| 3 | MOD | Ejecución de Alloy: propiedades verificadas y contraejemplos | PRO-*, ESP-* |
| 4 | COD | PR revisados, resultados de pruebas unitarias e integración en CI | RF-04, RF-05 |
| 4 | GC | Conflicto de integración controlado (antes, resolución, después) | Fase 7 |
| 5 | MOD | Contradicción: modelo antes/después y contraejemplo o prueba de coexistencia | INC-001 |
| 6 | PRU | Casos de sistema y aceptación del proceso crítico, con versión v1.0.0 | RF-06 |
| 6 | SEG | Autorización negativa en servidor, inyección, sesión/expiración, ZAP | RNF-01…03, 14.6 |
| 6 | REN | Prueba de carga (k6) de la administración de dosis | RNF-06 |
| 6 | CNF | Fallo y recuperación de la BD/API; tiempos de recuperación | RNF-12, RNF-04 |
| 6 | MOV | App en Android real: login, 2 procesos, sin conexión, notificaciones | 14.5, RNF-09 |
| 6 | PRU | Web en dos navegadores y en resolución móvil | RNF-08 |
| 6 | MET | Métricas "antes" con fórmula, fuente y unidad | Fase 9 |
| 7 | GC | RFC-001, `git diff v1.0.0 v1.1.0 --stat`, CCB | Fase 8 |
| 7 | PRU/SEG | MFA funcionando y regresión completa | RFC-001 |
| 7 | REN/CNF | Disponibilidad y carga después del MFA | RFC-001 |
| 7 | MET | Métricas "después" y comparación | Fase 9 |
| 8 | MET | Informe de huecos de la matriz y dictamen | Fase 10 |

## 4. Quién las toma
Cada integrante toma las de su área y las deja en `02_Equipo/<nombre>/Entregas/Evidencias/` con una nota breve (qué muestra, cómo se obtuvo, versión). Terry y Claude validan, asignan ID y las suben al repo en `evidencias/<TIPO>/`. Las evidencias descartadas se archivan con el motivo.
