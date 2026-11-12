# Inventario de elementos de configuración y líneas base — SAMed

ID: CI-802 · Versión: v1 · Fecha: 2026-11-12 · Dueño: Terry · Estado: En revisión (entra en `lb-req-1.0`)
Reemplaza a `Inventario_CI_v0.md`. Reglas de identificación, versiones y estados en el Plan de GC (CI-801 §3 a §5).

Cómo leer la columna Versión: `vN` para documentos con versión en el nombre; commit corto para archivos sin versión en el nombre; `—` si el CI está Planificado (todavía no existe). Al crear cada línea base se reemplaza por el tag.

## 1. Inventario

| ID | Nombre | Tipo | Ruta | Dueño | Versión | Estado | Entra en | Depende de |
|---|---|---|---|---|---|---|---|---|
| CI-101 | Ficha del sistema SAMed | Requisito | `docs/01_sistema/Ficha_SAMed_v1.md` | Juan | v1 | En trabajo | lb-req-1.0 | — |
| CI-102 | Catálogo de requisitos RF/RNF/RN y criterios de aceptación | Requisito | `docs/01_sistema/Requisitos_v1.md` | Juan | — | Planificado | lb-req-1.0 | CI-101 |
| CI-103 | Procesos de negocio PN-01 a PN-06 | Requisito | `docs/01_sistema/Procesos_v1.md` | Juan | — | Planificado | lb-req-1.0 | CI-102 |
| CI-104 | Arquitectura | Diseño | `docs/01_sistema/Arquitectura_v1.md` | Germán | — | Planificado | lb-req-1.0 | CI-102 |
| CI-105 | Modelo de datos (ER y restricciones) | Diseño | `docs/01_sistema/Modelo_Datos_v1.md` | Germán | — | Planificado | lb-req-1.0 | CI-102, CI-103 |
| CI-106 | Manual de instalación/ejecución y guía de uso | Documentación | `docs/01_sistema/` (ruta por definir) | Germán | — | Planificado | v1.0.0 | CI-607 |
| CI-201 | RNF de seguridad (RNF-101+) | Requisito | `docs/02_seguridad/RNF_Seguridad_v1.md` | Neyls | — | Planificado | lb-req-1.0 | CI-102, CI-202 |
| CI-202 | Activos preliminares (AS) | Seguridad | `docs/02_seguridad/Activos_v0.md` | Neyls | — | Planificado | lb-req-1.0 | CI-101 |
| CI-203 | Matriz activo → amenaza → vulnerabilidad → riesgo → control → evidencia | Seguridad | `docs/02_seguridad/` | Neyls | — | Planificado | lb-esp-1.0 | CI-201, CI-202, CI-104 |
| CI-204 | Matriz etapa del ciclo → riesgo → práctica → evidencia | Seguridad | `docs/02_seguridad/` | Neyls | — | Planificado | v1.0.0 | CI-203 |
| CI-301 | Escenarios de fallo y cálculos de confiabilidad (FAL) | Confiabilidad | `docs/03_confiabilidad/` | Germán | — | Planificado | v1.0.0 | CI-104 |
| CI-401 | Expediente Cleanroom del módulo de administración de dosis | Especificación/Modelo | `docs/04_cleanroom/` | Juan | — | Planificado | v1.0.0 | CI-103, CI-402 |
| CI-402 | Especificaciones formales (ESP, INV) | Especificación/Modelo | `docs/05_especificacion/` | Juan | — | Planificado | lb-esp-1.0 | CI-102 |
| CI-501 | Modelo formal Alloy | Especificación/Modelo | `docs/06_modelo_verificacion/*.als` | Neyls | — | Planificado | lb-esp-1.0 | CI-402 |
| CI-502 | Expediente de verificación del modelo (PRO) | Especificación/Modelo | `docs/06_modelo_verificacion/` | Neyls | — | Planificado | lb-esp-1.0 | CI-501 |
| CI-601 | API (NestJS) | Código | `apps/api/` | Germán | — | Planificado | v1.0.0 | CI-605, CI-606 |
| CI-602 | Aplicación web (React + Vite) | Código | `apps/web/` | Juan | — | Planificado | v1.0.0 | CI-605, CI-604 |
| CI-603 | Aplicación móvil (React Native + Expo, Android) | Código | `apps/mobile/` | Neyls | — | Planificado | v1.0.0 | CI-605, CI-604 |
| CI-604 | Esquemas y tipos compartidos (Zod) | Código | `packages/shared/` | Germán | — | Planificado | v1.0.0 | CI-605 |
| CI-605 | Contrato OpenAPI v1 | Diseño | `packages/shared/openapi.yaml` | Germán | — | Planificado | lb-req-1.0 | CI-102, CI-105 |
| CI-606 | Migraciones y datos sintéticos de BD | Base de datos | `db/` | Germán | — | Planificado | v1.0.0 | CI-105 |
| CI-607 | Entorno local (Docker Compose con PostgreSQL) | Infraestructura | `infra/docker-compose.yml` | Germán | — | Planificado | v1.0.0 | CI-608 |
| CI-608 | Plantilla de variables de entorno | Infraestructura | `.env.example` | Germán | 5cc63f2 | En trabajo | lb-req-1.0 | — |
| CI-701 | Catálogo de casos de prueba (TC) | Prueba | `docs/12_pruebas/` | Los 4 (rangos TC por persona) | — | Planificado | v1.0.0 | CI-102 |
| CI-702 | Pruebas automatizadas (unitarias, integración, E2E, carga) | Prueba | `apps/*/test`, `apps/web/e2e` | Dueño de cada app | — | Planificado | v1.0.0 | CI-701 |
| CI-703 | Registro de ejecuciones y resultados (EJ) | Prueba | `docs/12_pruebas/` | Quien ejecuta | — | Planificado | v1.0.0 | CI-701 |
| CI-704 | Script de cálculo de métricas y tablero de indicadores | Código | `scripts/metricas/` | Terry | — | Planificado | v1.0.0 | CI-901 |
| CI-801 | Plan de Gestión de Configuración | Gobernanza | `docs/07_configuracion/Plan_GC_v1.md` | Terry | v1 | En revisión | lb-req-1.0 | CI-803 |
| CI-802 | Inventario de CI y líneas base (este documento) | Gobernanza | `docs/07_configuracion/Inventario_CI_v1.md` | Terry | v1 | En revisión | lb-req-1.0 | CI-801 |
| CI-803 | Convención de IDs, nombres y versiones | Gobernanza | `docs/07_configuracion/Convencion_IDs.md` | Terry | v1 | En trabajo | lb-req-1.0 | — |
| CI-804 | Reglas para agentes de IA | Gobernanza | `AGENTS.md`, `CLAUDE.md` | Terry | c4c2272 | En trabajo | lb-req-1.0 | CI-803 |
| CI-805 | README del repositorio | Gobernanza | `README.md` | Terry | 5cc63f2 | En revisión | lb-req-1.0 | CI-801 |
| CI-806 | Dueños de carpetas | Gobernanza | `.github/CODEOWNERS` | Terry | 5cc63f2 | En revisión | lb-req-1.0 | CI-801 |
| CI-807 | Plantilla de PR | Gobernanza | `.github/pull_request_template.md` | Terry | 5cc63f2 | En trabajo | lb-req-1.0 | CI-803 |
| CI-808 | Pipeline de integración continua (gitleaks; luego lint y pruebas) | Infraestructura | `.github/workflows/ci.yml` | Terry | 5cc63f2 | En trabajo | lb-req-1.0 | — |
| CI-809 | Exclusiones de Git | Infraestructura | `.gitignore` | Terry | 5cc63f2 | En trabajo | lb-req-1.0 | — |
| CI-810 | Contexto del proyecto (enunciado, plan, guía de Git, metodología, plan de evidencias) | Gobernanza | `docs/00_proyecto/` | Terry | — | En revisión (PR #3) | lb-req-1.0 | — |
| CI-811 | Registro de errores y lecciones (ERR, LEC) | Gobernanza | `docs/14_errores_lecciones/Registro_Errores.md` | Terry | 5cc63f2 | En trabajo | lb-req-1.0 | CI-803 |
| CI-812 | Registro de evidencias (EVI) | Gobernanza | `evidencias/Registro_Evidencias.md` | Terry | — | Planificado | lb-req-1.0 | CI-803 |
| CI-813 | Expediente de solicitudes y decisiones de cambio (RFC) | Cambio | `docs/09_cambios/` | Terry | — | Planificado | v1.1.0 | CI-801 |
| CI-814 | Expediente del requisito contradictorio INC-001 | Cambio | `docs/09_cambios/INC-001/` | Juan | — | Planificado | lb-esp-1.1 | CI-402, CI-501 |
| CI-815 | Expediente RFC-001 (MFA) | Cambio | `docs/09_cambios/RFC-001/` | Terry (con Neyls) | — | Planificado | v1.1.0 | CI-813 |
| CI-816 | Evidencias de versionamiento y conflicto controlado | Documentación | `docs/08_versionamiento/` | Terry | — | Planificado | v1.1.0 | CI-801 |
| CI-901 | Catálogo de métricas (MET) | Métrica/Matriz | `docs/10_metricas/Catalogo_Metricas_v0.md` | Terry | v0 | En revisión | lb-req-1.0 | CI-102 |
| CI-902 | Matriz maestra de trazabilidad y evidencias | Métrica/Matriz | `docs/11_matrices/Matriz_Maestra_v0.xlsx` | Terry | v0 | En revisión | lb-req-1.0 | CI-102, CI-802, CI-901 |
| CI-903 | Informe técnico final de certificación | Documentación | `docs/13_certificacion/` | Terry | — | Planificado | v1.1.0 | CI-902, CI-901 |

Cambios respecto de v0: se conservan los IDs ya emitidos (CI-101, CI-801 a CI-804) y se completa cada categoría; Plan de GC e inventario pasan a v1 con `git mv`. Ningún ID fue reutilizado ni retirado.

## 2. Estructura de líneas base

| Línea base | Tag | CI incluidos |
|---|---|---|
| LB-REQ | `lb-req-1.0` | CI-101 a CI-105, CI-201, CI-202, CI-605, CI-608, CI-801 a CI-812, CI-901, CI-902 |
| LB-ESP | `lb-esp-1.0` | LB-REQ + CI-203, CI-402, CI-501, CI-502 |
| LB-ESP tras INC-001 | `lb-esp-1.1` | LB-ESP + CI-814 |
| LB-1 | `v1.0.0` | Todos salvo CI-813, CI-815, CI-816, CI-903 |
| LB-2 | `v1.1.0` | Todos |

## 3. Dudas abiertas

- CI-808 (pipeline) y CI-809 (`.gitignore`) quedan con Terry por ser configuración de todo el repositorio; si Germán los asume al agregar lint y pruebas al pipeline, se cambia aquí y en `CODEOWNERS`.
- CI-202 (activos) se incluyó en `lb-req-1.0` porque los RNF de seguridad (CI-201) lo referencian; confirmar con Neyls.
- CI-810 depende de la fusión del PR #3.
- Las rutas de los CI Planificados salen de las instrucciones de cada integrante; se ajustan cuando cada dueño cree su archivo.
