# SAMed — Sistema de Administración Segura de Medicamentos

Proyecto final de Ingeniería de Software II (sistema de misión crítica). Hospital ficticio, datos sintéticos.

- Stack: NestJS + PostgreSQL (api), React (web), React Native/Expo (Android), Zod compartido.
- Estructura: `apps/{api,web,mobile}`, `packages/shared`, `db`, `infra`, `scripts`, `docs/01…14`, `evidencias`.
- Reglas: ver `AGENTS.md`, `docs/07_configuracion/Plan_GC_v0.md` y `docs/07_configuracion/Convencion_IDs.md`.
- Ramas: `main` (líneas base), `develop`, `feat/*`, `fix/*`, `docs/*`, `rfc/*`. Tags: `lb-req-1.0`, `lb-esp-1.0`, `v1.0.0`, `v1.1.0`.
- Equipo: tcuenca1 (líder), German1450, TheBat849, JuanPaladinesCoding.
- Secretos: nunca en el repo; solo `.env.example`.
