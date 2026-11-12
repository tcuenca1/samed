# Ficha del sistema SAMed — Sistema de Administración Segura de Medicamentos

Versión: v1 · 2026-11-12 · Etapa 0 · Responsable: Juan (revisa Germán) · Estado: Propuesta, se detalla en la Etapa 1
Datos 100 % sintéticos; hospital ficticio.

## 1. Propósito y criticidad
SAMed controla el ciclo médico → farmacia → enfermería para que el paciente correcto reciba el medicamento correcto, en la dosis y hora correctas. Una falla (dosis duplicada, alergia ignorada, paciente equivocado, sistema caído junto a la cama) puede causar daño al paciente.

## 2. Actores y roles (RF-02, mínimo 3)
| Rol | Puede | No puede |
|---|---|---|
| Médico | Prescribir, ver historia del paciente, ordenar acceso de emergencia | Validar su propia prescripción, administrar |
| Farmacéutico | Validar/rechazar prescripciones, gestionar stock y lotes, dispensar | Prescribir, administrar |
| Enfermería | Ver dosis pendientes, administrar y registrar (web y móvil) | Prescribir, validar |
| Administrador | Gestionar usuarios, roles y catálogos | Ver historia clínica detallada ni administrar |
| Auditor | Consultar auditoría y reportes (solo lectura) | Modificar nada |

## 3. Procesos de negocio (RF-04, mínimo 5)
| ID | Proceso | Quién |
|---|---|---|
| PN-01 | Admisión del paciente y registro de alergias | Administrador / Médico |
| PN-02 | Prescripción de medicamento | Médico |
| PN-03 | Validación farmacéutica (interacciones, alergias, dosis máxima) | Farmacéutico |
| PN-04 | Dispensación con control de stock y lotes | Farmacéutico |
| **PN-05** | **Administración de dosis al paciente (PROCESO CRÍTICO, RF-06)** | Enfermería (móvil y web) |
| PN-06 | Alertas y notificaciones de dosis pendientes/atrasadas | Sistema |

## 4. Proceso crítico PN-05 y reglas preliminares (se formalizan en Etapa 3)
- RN-001: solo se administra una prescripción en estado Validada.
- RN-002: no se administra si el paciente tiene alergia registrada al principio activo.
- RN-003: no se supera la dosis máxima diaria.
- RN-004: una dosis programada no se administra dos veces.
- RN-005: se verifica paciente (pulsera/QR) antes de registrar.
- RN-006: toda administración queda en auditoría (RF-10).
Módulo crítico para Cleanroom: **Administración de dosis**.

## 5. Capacidades móviles (Android) — requisito 14.5
Dos procesos en la app: **administración de dosis** (PN-05) y **consulta/confirmación de dosis pendientes con alertas** (PN-06). Cámara para escanear QR de pulsera; notificaciones; almacenamiento local para tolerar cortes de conexión.

## 6. Integración externa (RF-14)
Servicio externo de interacciones/medicamentos (simulado o API pública), con riesgos y manejo de fallo documentados en la Etapa 2.

## 7. Candidatos para el requisito contradictorio y el RFC
- Contradictorio (Etapa 5): acceso de emergencia que permite administrar sin validación farmacéutica previa vs. RN-001.
- Cambio de emergencia (Etapa 7): MFA para todas las operaciones críticas sin degradar disponibilidad.
