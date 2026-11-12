# Reglas para agentes de IA
1. No inventes datos, cifras ni resultados de prueba. Escribe "Sin dato" y quién lo aporta.
2. Cita IDs (RF-, RSK-, TC-, CI-...) en commits, pruebas y documentos. Ver docs/07_configuracion/Convencion_IDs.
3. Nunca escribas secretos; solo .env.example.
4. Toda regla de negocio lleva prueba unitaria.
5. Autorización siempre en el servidor.
6. No toques carpetas ajenas (ver CODEOWNERS). Cambios ajenos: abre un issue.
7. Al terminar informa: qué hiciste, qué NO pudiste verificar, dudas abiertas.
8. Commits: tipo(ámbito): descripción [ID].

## Commits (reglas del equipo)
1. El autor del commit es la persona que dirige y es dueña de la decisión (por defecto, quien pidió el cambio). El agente de IA figura solo como coautor con la línea `Co-Authored-By`, nunca como único autor.
2. Formato: `tipo(ámbito): descripción corta [ID]` en español, tipos feat, fix, docs, test, refactor, chore, ci. Cuerpo opcional: qué cambió y por qué.
3. No mencionar etapas, fases ni planes internos del proyecto (nada de "Etapa 0", "Fase 3", "bloque"). Describir el cambio técnico y citar IDs de requisitos, riesgos, pruebas o RFC (RF-004, RSK-003, RFC-001).
4. Un commit = un cambio con sentido. Sin mensajes vagos ("cambios", "fix").
5. Nunca subir secretos ni `.env`; nunca push directo a `main` ni a `develop` (todo por PR).
6. Si se sube trabajo de otra persona: `--author` o `Co-authored-by` con esa persona y la línea "Subido por X a pedido de Y".
