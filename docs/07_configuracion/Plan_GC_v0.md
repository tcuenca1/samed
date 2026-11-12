# Plan de Gestión de Configuración — v0 (Etapa 0)

Versión: v0 · 2026-11-12 · Responsable: Terry · Se completa como v1 en la Etapa 1 (E07)

## 1. Elementos de configuración (CI) por categoría
| Categoría | Prefijo CI | Ubicación | Dueño |
|---|---|---|---|
| Requisitos y fichas | CI-1xx | docs/01_sistema | Juan |
| Seguridad y riesgos | CI-2xx | docs/02_seguridad | Neyls |
| Confiabilidad | CI-3xx | docs/03_confiabilidad | Germán |
| Cleanroom y especificación | CI-4xx | docs/04_cleanroom, docs/05_especificacion | Juan |
| Modelo formal | CI-5xx | docs/06_modelo_verificacion | Neyls |
| Código | CI-6xx | apps/, packages/, db/ | Germán (api, db), Neyls (mobile), Juan (web) |
| Pruebas y scripts | CI-7xx | docs/12_pruebas, scripts/ | Quien las crea |
| Configuración y cambios | CI-8xx | docs/07_configuracion, docs/09_cambios | Terry |
| Métricas y matrices | CI-9xx | docs/10_metricas, docs/11_matrices | Terry |

## 2. Nomenclatura, versiones y estados
IDs según `Convencion_IDs.md`. Versión de CI: `vMAYOR.MENOR` en el encabezado del documento; el código se versiona con tags. Estados: En trabajo → En revisión → Aprobado (en línea base) → Modificado por RFC.

## 3. Ramas, commits y PR
`main` (solo líneas base) · `develop` (integración) · `feat/<ID>-desc`, `fix/DEF-NNN-desc`, `docs/<ID>-desc`, `rfc/RFC-NNN-desc`. Commits: `tipo(ámbito): descripción [ID]`. Todo entra por PR con CI verde y una revisión. La primera confirmación de `main` (esqueleto de la Etapa 0) es la única excepción a esta regla.

## 4. Líneas base
| Línea base | Tag | Criterio de creación | Aprueba |
|---|---|---|---|
| LB-REQ | lb-req-1.0 | RF/RNF con ID, criterio de aceptación y dueño; revisados por los 4 | Terry |
| LB-ESP | lb-esp-1.0 (1.1 tras INC-001) | Especificación y modelo verificados | Terry |
| LB-1 | v1.0.0 | CI verde, pruebas críticas ejecutadas sobre esta versión, evidencia registrada | CCB |
| LB-2 | v1.1.0 | RFC-001 aprobado, regresión completa, disponibilidad ≥ objetivo | CCB |

## 5. Integridad
Protección de `main`/`develop`, CODEOWNERS por carpeta, gitleaks en el CI, matrices exportadas a `docs/11_matrices/<tag>/` en cada línea base, evidencias con la versión en el nombre.

## 6. CCB
Terry (preside), dueño del artefacto afectado y un tercero. Decide cada RFC (aceptar/rechazar/aplazar) y lo deja en `docs/09_cambios/`.
