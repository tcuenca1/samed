# Plan de Gestión de Configuración — SAMed

ID: CI-801 · Versión: v1 · Fecha: 2026-11-12 · Dueño: Terry · Estado: En revisión (entra en `lb-req-1.0`)
Reemplaza a `Plan_GC_v0.md` (renombrado en Git, el historial se conserva). Responde al enunciado Fase 6 y §14.8.

## 1. Propósito y alcance

Definir cómo se identifican, versionan, controlan, registran y auditan los elementos de configuración (CI) de SAMed, de modo que en cualquier línea base se pueda reconstruir el estado exacto del producto y demostrar qué cambió y qué permaneció estable (enunciado §12, Fase 8).

Alcance: todo el repositorio `tcuenca1/samed` (requisitos, especificaciones, modelos, código de API, web y móvil, paquete compartido, base de datos, infraestructura, pruebas y resultados, métricas, matrices, solicitudes de cambio, documentación). Fuera de alcance: la carpeta de coordinación en OneDrive (borradores, actas, buzones), salvo la copia final de entrega.

## 2. Roles

| Rol | Persona | Responsabilidad en GC |
|---|---|---|
| Gestor de configuración y presidente del CCB | Terry (`tcuenca1`) | Mantiene este plan y el inventario (CI-802), crea tags y releases, fusiona a `develop` y `main`, convoca al CCB |
| Dueños de CI | Juan (`JuanPaladinesCoding`), Germán (`German1450`), Neyls (`TheBat849`), Terry | Crean y modifican sus CI por PR; revisan los PR que tocan sus carpetas (`.github/CODEOWNERS`, CI-806) |
| Revisor | Cualquier integrante distinto del autor | Aprueba el PR (mínimo 1 aprobación) |
| Agentes de IA | — | Redactan y revisan consistencia de IDs; figuran solo como coautores (`AGENTS.md`, CI-804). No aprueban ni fusionan |
| CCB | Terry + dueño del CI afectado + un integrante más | Decide cada RFC (aceptar, rechazar, aplazar) y deja la decisión en `docs/09_cambios/` |

## 3. Identificación de CI

Criterio: algo es CI si un requisito, una prueba, una métrica o una evidencia depende de él, o si hace falta para reconstruir una versión.

Cada CI tiene un ID `CI-NNN` que nunca se reutiliza (si se descarta pasa a Retirado). La centena indica la categoría; dentro de ella la numeración es correlativa:

| Rango | Categoría | Ubicación | Dueño por defecto |
|---|---|---|---|
| CI-1xx | Requisitos, procesos, arquitectura, datos, manual | `docs/01_sistema/` | Juan (arquitectura, datos y manual: Germán) |
| CI-2xx | Seguridad | `docs/02_seguridad/` | Neyls |
| CI-3xx | Confiabilidad | `docs/03_confiabilidad/` | Germán |
| CI-4xx | Cleanroom y especificación formal | `docs/04_cleanroom/`, `docs/05_especificacion/` | Juan |
| CI-5xx | Modelo formal y verificación | `docs/06_modelo_verificacion/` | Neyls |
| CI-6xx | Código, contrato, base de datos, infraestructura | `apps/`, `packages/`, `db/`, `infra/`, `.env.example` | Germán (api, shared, db, infra), Juan (web), Neyls (mobile) |
| CI-7xx | Pruebas y scripts | `docs/12_pruebas/`, `apps/*/test`, `scripts/` | Quien los crea |
| CI-8xx | Gobernanza, configuración, cambios, versionamiento, evidencias | raíz, `.github/`, `docs/00_proyecto/`, `docs/07_configuracion/`, `docs/08_versionamiento/`, `docs/09_cambios/`, `docs/14_errores_lecciones/`, `evidencias/` | Terry |
| CI-9xx | Métricas, matrices, certificación | `docs/10_metricas/`, `docs/11_matrices/`, `docs/13_certificacion/` | Terry |

El inventario (`Inventario_CI_v1.md`, CI-802) registra por CI: nombre, tipo, ruta, dueño, versión, estado, línea base en la que entra y dependencias.

## 4. Nomenclatura y versiones

| Elemento | Regla |
|---|---|
| Documentos | `Nombre_vN.md` (Convención de IDs §4, CI-803). Cabecera con ID, versión, fecha, dueño y estado. Una versión aprobada en línea base no se edita: el cambio crea `vN+1` con `git mv`, y Git conserva la anterior |
| Archivos sin versión en el nombre (README, `.github/*`, `.gitignore`, `.env.example`, código) | Su versión es el commit corto que los modificó por última vez; en línea base, el tag |
| Producto (código) | SemVer `vMAYOR.MENOR.PARCHE`: `v1.0.0` = línea base previa al cambio impuesto; `v1.1.0` = posterior al RFC-001 (MFA) |
| Líneas base documentales | `lb-req-1.0`, `lb-esp-1.0`, `lb-esp-1.1` |
| Incrementos Cleanroom | Tags `inc-1`, `inc-2`, `inc-3` |
| Evidencias | `EVI-TIPO-NNN_descripcion_<tag-o-version>_AAAA-MM-DD.ext` |

Los tags son anotados e inmutables: no se mueven ni se borran. Un error en una línea base se corrige con una nueva (por ejemplo `lb-req-1.1`).

## 5. Estados de un CI

| Estado | Significado | Cómo se llega |
|---|---|---|
| Planificado | El CI está identificado pero el archivo aún no existe | Alta en el inventario |
| En trabajo | Existe en una rama o en `develop`, todavía cambia libremente | Primer commit |
| En revisión | Tiene un PR abierto | Apertura del PR |
| Aprobado (en línea base) | Fusionado y dentro de un tag de línea base | Creación del tag |
| Modificado por RFC | Cambió después de su línea base, con RFC aprobado | Fusión del cambio del RFC |
| Retirado | Descartado; su ID no se reutiliza | Decisión registrada en el inventario |

"Planificado" no figura aún en la tabla de estados de la Convención de IDs (CI-803 §5). Se propone agregarlo allí; mientras tanto este plan lo define.

## 6. Repositorio, ramas, commits y PR

Repositorio: GitHub `tcuenca1/samed`. Cada integrante lo clona fuera de OneDrive (ver `docs/00_proyecto/Guia_Git.md`).

| Rama | Uso | Sale de | Quién fusiona |
|---|---|---|---|
| `main` | Solo líneas base y releases | — | Terry, desde `develop` o `rfc/*` |
| `develop` | Integración | `main` | Terry, tras PR aprobado y CI verde |
| `feat/<ID>-desc` | Funcionalidad o documento nuevo | `develop` | — |
| `fix/DEF-NNN-desc` | Corrección de defecto | `develop` | — |
| `docs/<ID>-desc` | Solo documentación | `develop` | — |
| `rfc/RFC-NNN-desc` | Cambio de emergencia | tag `v1.0.0` | — |
| `claude/*` | Rama creada por un agente de IA en la nube; se trata como `feat/*` o `docs/*` | `develop` | — |

Reglas:

1. Nadie hace push directo a `main` ni a `develop`; todo entra por PR. Única excepción registrada: el commit inicial del esqueleto en `main` (`5cc63f2`).
2. Commits: `tipo(ámbito): descripción [ID]`, en español, tipos `feat`, `fix`, `docs`, `test`, `refactor`, `chore`, `ci`. No mencionan etapas ni fases; citan IDs (RF, RNF, RSK, TC, CI, RFC…). Ver `AGENTS.md`.
3. Autoría: el autor es la persona dueña de la decisión; un agente de IA solo como `Co-Authored-By`. Si alguien sube trabajo de otro: `--author` o `Co-authored-by` y la línea "Subido por X a pedido de Y".
4. PR: plantilla obligatoria (`.github/pull_request_template.md`, CI-807: qué cambia, IDs, pruebas y versión, evidencia, riesgo residual), 1 aprobación de otra persona, CI verde (gitleaks).
5. Conflicto al fusionar: no se resuelve borrando; se avisa a Terry. El conflicto controlado entre ramas sobre el catálogo de roles y permisos se documenta en `docs/08_versionamiento/` (CI-816).

## 7. Líneas base

| Línea base | Tag | Qué congela (CI) | Criterio de creación y aprobación | Aprueba |
|---|---|---|---|---|
| LB-REQ | `lb-req-1.0` | Ver inventario, columna "Entra en" = `lb-req-1.0` (requisitos, procesos, arquitectura, datos, OpenAPI v1, RNF de seguridad, gobernanza y GC) | Todo RF/RNF con ID, criterio de aceptación comprobable y dueño; tabla de cobertura contra §14.2 y §14.3 sin huecos; catálogo de métricas revisado por los 4; auditoría §10 sin hallazgos abiertos | Terry, con acta |
| LB-ESP | `lb-esp-1.0` | LB-REQ + especificación formal, modelo y su verificación | Toda propiedad verificada o con contraejemplo documentado | Terry, con acta |
| LB-ESP tras INC-001 | `lb-esp-1.1` | LB-ESP + expediente del requisito contradictorio | Conclusión sustentada por especificación y modelo | Terry, con acta |
| LB-1 | `v1.0.0` | Código, BD, pruebas y resultados, métricas "antes", matrices exportadas | CI verde; casos críticos ejecutados sobre `v1.0.0`; evidencias registradas con esa versión en el nombre | CCB |
| LB-2 | `v1.1.0` | LB-1 + RFC-001 implementado, regresión, métricas "después" | RFC-001 aprobado; regresión en verde (MET-010 = 100 %); disponibilidad ≥ objetivo del RNF de disponibilidad (Sin dato: lo define Germán) | CCB |

Al menos una línea base previa al cambio impuesto (`v1.0.0`) y una posterior al cambio aprobado (`v1.1.0`), como exige §14.8.

### 7.1 Procedimiento para crear una línea base

1. Auditoría de configuración (§10) con la lista de chequeo de la línea base.
2. PR de `develop` a `main` (o de `rfc/*` a `main`), aprobado.
3. Tag anotado sobre el commit de fusión en `main`:
   `git tag -a lb-req-1.0 -m "LB-REQ: requisitos, arquitectura y contrato v1 [ACT-NNN]"` y `git push origin lb-req-1.0`.
4. Release de GitHub con notas, enlace al acta y lista de CI incluidos.
5. Exportar la matriz maestra a `docs/11_matrices/<tag>/`.
6. Actualizar el inventario: estado Aprobado y versión de cada CI incluido.

Reconstrucción: `git checkout <tag>` más el manual de instalación (CI-106). Comparación entre líneas base: `git diff v1.0.0 v1.1.0 --stat`.

### 7.2 Lista de chequeo de `lb-req-1.0`

| # | Criterio | Fuente | Responsable |
|---|---|---|---|
| 1 | Catálogo RF/RNF/RN con ID, un solo comportamiento, criterio de aceptación y dueño | CI-102 | Juan |
| 2 | Tabla de cobertura contra §14.2 y §14.3 sin huecos | CI-102 | Juan |
| 3 | Criterios Dado/Cuando/Entonces de RN-001 a RN-006 y caso feliz de PN-05 | CI-102 | Juan |
| 4 | Procesos PN-01 a PN-06 detallados | CI-103 | Juan |
| 5 | Arquitectura, modelo de datos y OpenAPI v1 con roles por endpoint | CI-104, CI-105, CI-605 | Germán |
| 6 | RNF de seguridad con criterio medible | CI-201 | Neyls |
| 7 | Catálogo de métricas revisado por los 4 | CI-901 | Terry |
| 8 | Matriz maestra con una fila por requisito del catálogo | CI-902 | Terry |
| 9 | Inventario coincide con los archivos reales (auditoría física) | CI-802 | Terry + otro |
| 10 | gitleaks verde en `develop`; sin secretos | CI-808 | Terry |

## 8. Control de cambios

- Antes de la primera línea base: los cambios se controlan por PR normal.
- Después de una línea base, todo cambio a un CI Aprobado necesita un RFC en `docs/09_cambios/RFC-NNN/` con: origen, descripción, impacto (requisitos, riesgos, controles, especificación, modelo, pruebas, CI, métricas), decisión del CCB, artefactos afectados, rama, versión y evidencia de verificación (§14.8).
- Estados del RFC: Recibido → En análisis → Aceptado / Rechazado / Aplazado → Implementado → Verificado → Cerrado.
- Cambio de emergencia RFC-001 (MFA): rama `rfc/RFC-001-mfa` desde `v1.0.0`; se fusiona a `main` como `v1.1.0` y también a `develop`.
- Cadena de cada cambio (enunciado §7): RFC → Impacto → Riesgo → Decisión → Cambio → Versión → Verificación → Métrica → Evidencia → Nueva línea base.

## 9. Registro del estado de la configuración

- Inventario de CI (CI-802): se actualiza en cada fusión que crea, renombra o retira un CI y en cada línea base.
- Historial de Git, tags y releases de GitHub.
- Registro de evidencias (CI-812) y registro de errores y lecciones (CI-811).
- Defectos como issues de GitHub con etiqueta `defecto` (IDs DEF por rango de persona).

## 10. Auditorías de configuración

Antes de cada línea base, Terry y otro integrante revisan:

- Funcional: cada requisito incluido tiene, según corresponda a esa línea base, su especificación, prueba ejecutada sobre esa versión y evidencia válida (matriz maestra CI-902).
- Física: cada CI del inventario existe en la ruta y versión declaradas; no hay archivos sin dueño en `CODEOWNERS` ni secretos.

El resultado queda en un acta `ACT-NNN` y, si hay hallazgos, en `ERR-NNN`.

## 11. Integridad y seguridad de la configuración

- Secretos: `.env` en `.gitignore`; solo `.env.example` con valores de ejemplo; gitleaks en cada push y PR (CI-808).
- Protección de ramas `main` y `develop` en GitHub (Settings → Branches → Add rule, o Rulesets): exigir PR, 1 aprobación, check `ci / secretos` en verde, bloquear force push y borrado. Estado al 2026-11-12: **sin protección** (la API de GitHub reporta `protected: false` en ambas). Si el plan de la cuenta no permite proteger ramas en un repositorio privado, se registra como riesgo y se cumple como regla del equipo, verificable en el historial (todo commit en `develop` debe venir de un merge de PR).
- `CODEOWNERS` cubre cada carpeta con dueño, para que GitHub pida su revisión.
- Respaldo: repositorio remoto en GitHub más un clon local en cada PC.

## 12. Herramientas

Git; GitHub (repositorio, PR, issues, Actions, releases); gitleaks; Excel para las matrices (exportadas en cada línea base); Docker Compose para reconstruir el entorno.

## 13. Pendientes

| Pendiente | Quién |
|---|---|
| Activar la protección de `main` y `develop` (§11) | Terry |
| Agregar el estado "Planificado" a la Convención de IDs | Terry |
| Decidir si Germán asume CI-808 (pipeline) al agregar lint y pruebas | Germán y Terry |
| Objetivo de disponibilidad (RNF de disponibilidad, rango RNF-201+) | Germán |
| Ruta definitiva del manual de instalación (CI-106) | Germán |
