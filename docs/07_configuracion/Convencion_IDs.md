# Convención de IDs, nombres y versiones — Proyecto Final

Versión: v1 · Fecha: 2026-11-11 · Basada en la convención v2 del primer parcial · Estado: Propuesta

En la defensa hay que saltar en segundos de un requisito a su riesgo, especificación, modelo, prueba, versión, métrica y evidencia. Solo funciona si cada elemento tiene un ID único que se escribe igual en el código, los commits, la matriz, los documentos y los nombres de archivo.

## 1. Prefijos

| Elemento | Formato | Ejemplo | Dónde nace | Dueño |
|---|---|---|---|---|
| Requisito funcional | `RF-NNN` | RF-006 | `docs/01_sistema/requisitos` | Juan |
| Requisito no funcional | `RNF-NNN` | RNF-004 | ídem | Juan (seguridad: Neyls) |
| Regla de negocio | `RN-NNN` | RN-003 | ídem | Juan |
| Proceso de negocio | `PN-NN` | PN-05 | ídem | Juan |
| Activo (seguridad) | `AS-NNN` | AS-002 | `docs/02_seguridad` | Neyls |
| Amenaza / vulnerabilidad | `AM-NNN` / `VU-NNN` | AM-004 | ídem | Neyls |
| Riesgo | `RSK-NNN` | RSK-007 | ídem (confiabilidad: Germán desde RSK-100) | Neyls / Germán |
| Control | `CTL-NNN` | CTL-010 | ídem | Neyls |
| Escenario de fallo | `FAL-NNN` | FAL-003 | `docs/03_confiabilidad` | Germán |
| Especificación formal | `ESP-NNN` | ESP-002 | `docs/05_especificacion` | Juan |
| Invariante | `INV-NNN` | INV-001 | ídem | Juan |
| Propiedad del modelo | `PRO-NNN` | PRO-004 | `docs/06_modelo_verificacion` | Neyls |
| Incremento Cleanroom | `INC-CR-N` | INC-CR-2 | `docs/04_cleanroom` | Juan / Germán |
| Caso de prueba | `TC-NNN` | TC-021 | `docs/12_pruebas` | Quien diseña la prueba (rango por persona, §2) |
| Ejecución de prueba | `EJ-NNN` | EJ-045 | ídem | Quien ejecuta |
| Elemento de configuración | `CI-NNN` | CI-014 | `docs/07_configuracion` | Terry |
| Solicitud de cambio | `RFC-NNN` | RFC-001 (MFA) | `docs/09_cambios` | Terry |
| Incidente de requisito | `INC-NNN` | INC-001 | ídem | Juan |
| Métrica | `MET-NNN` | MET-003 | `docs/10_metricas` | Terry |
| Defecto (producto) | `DEF-NNN` | DEF-012 | Issues de GitHub (etiqueta `defecto`) | Quien lo encuentra |
| Error de proceso | `ERR-NNN` | ERR-004 | `docs/14_errores_lecciones` | Claude registra |
| Lección | `LEC-NNN` | LEC-002 | ídem | Claude registra |
| Evidencia | `EVI-TIPO-NNN` | EVI-PRU-031 | `evidencias/Registro_Evidencias` | Claude valida, Terry registra |
| Tarea | `TAR-NNN` | TAR-012 | `01_Plan` | Terry |
| Acta | `ACT-NNN` | ACT-001 | `00_Gobernanza/Actas` | Terry |

Nota: `ACT` queda para actas, como en el parcial; por eso los activos usan `AS`.

Reglas: tres dígitos con ceros; numeración correlativa que no se reinicia; un ID nunca se reutiliza (si se descarta, estado Retirado); el ID nace en su lugar y luego se usa en todo lo demás.

## 2. Rangos por persona (evita choques sin coordinar)

| Prefijo | Terry | Germán | Neyls | Juan |
|---|---|---|---|---|
| TC | 300–399 | 100–199 | 200–299 | 001–099 |
| DEF | 300–399 | 100–199 | 200–299 | 001–099 |
| RSK | — | 100–199 (confiabilidad) | 001–099 (seguridad) | — |

## 3. Tipos de evidencia

| Tipo | Contenido |
|---|---|
| ENT | Entorno, instalación, configuración, versiones |
| COD | Código, análisis estático, revisión de PR |
| PRU | Ejecución de casos de prueba (con versión y ambiente) |
| SEG | Pruebas de seguridad (ZAP, autorización negativa, inyección) |
| CNF | Confiabilidad: inyección de fallos, recuperación, tiempos |
| REN | Rendimiento y carga |
| MOV | Pruebas móviles y de compatibilidad |
| MOD | Ejecuciones del modelo formal, contraejemplos |
| GC | Gestión de configuración: tags, ramas, diff, conflicto, CI |
| MET | Hojas de cálculo y salidas de métricas |

## 4. Nombres

- Evidencias: `EVI-TIPO-NNN_descripcion-corta_<tag-o-version>_AAAA-MM-DD.ext` (ej. `EVI-PRU-031_admin-dosis-duplicada_v1.0.0_2026-12-01.png`). La versión en el nombre cumple la regla "prueba que corresponda a la versión evaluada".
- Documentos: `Nombre_vN.md`. Una versión terminada no se edita: se crea `vN+1` (en el repo lo maneja Git; en OneDrive la anterior va a `99_Archivo/`).
- Commits: `tipo(ámbito): descripción [ID][ID]`; tipos `feat`, `fix`, `test`, `docs`, `refactor`, `chore`, `ci`.

## 5. Estados

| Elemento | Estados |
|---|---|
| Requisitos, riesgos, controles | Propuesto → Vigente → Retirado |
| Casos de prueba | No ejecutado → Pasa / Parcial / Falla / Bloqueado (Falla exige DEF) |
| Defectos | Abierto → En corrección → Corregido (versión) → Verificado / No reproducible |
| RFC | Recibido → En análisis → Aceptado / Rechazado / Aplazado → Implementado → Verificado → Cerrado |
| CI | En trabajo → En revisión → Aprobado (en línea base) → Modificado por RFC |
| Evidencias | Válida / Descartada |

## 6. Reglas de calidad (del enunciado y del parcial)

1. Nada sin evidencia: sin EVI válida no hay veredicto ("Sin evidencia").
2. Una captura sola no es evidencia: dice cómo se obtuvo, en qué versión y qué IDs respalda.
3. Métrica = fuente + fórmula + unidad + umbral + interpretación, o no cuenta.
4. Un cambio sin RFC, impacto, versión y evidencia es un cambio no controlado.
5. Sin secretos en el repo ni en capturas.
