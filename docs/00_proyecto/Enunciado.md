# PROYECTO FINAL

«Sistema de Misión Crítica: Ingeniería de Evidencia, Seguridad, Verificación, Configuración y Calidad»

Texto copiado del mensaje de Terry del 2026-11-11 (fuente de verdad n.º 1 del proyecto). Se conserva la numeración del original, incluidos los números 17–34 de la sección 10 y el «15.7» de pruebas (por su posición sería 14.7).

## 1. Denominación del proyecto
Sistema de Misión Crítica: Ingeniería de Evidencia, Seguridad, Verificación, Configuración y Calidad.

## 2. Propósito
El proyecto integra: Seguridad, Confiabilidad, Modelado y Verificación del Software; y Gestión de Configuración y Métricas del Producto Software. El equipo deberá demostrar que un sistema crítico puede mantenerse seguro, confiable, verificable, controlado y medible incluso cuando sus requisitos y configuración evolucionan.

No se evaluará únicamente la existencia de documentos o modelos. El núcleo del proyecto será la consistencia entre requisitos, riesgos, controles, especificaciones, modelos, pruebas, versiones, métricas y evidencias.

## 3. Pregunta
¿Cómo demostrar que un software crítico permanece seguro, confiable, verificable y controlado aun cuando sus requisitos y configuración evolucionan?

## 4. Escenario y condiciones mínimas
Cada equipo deberá trabajar con un sistema de misión crítica realista o ficticio, por ejemplo: plataforma hospitalaria, sistema financiero, control académico, emergencias, logística, gestión aeroportuaria o IoT industrial.

- El sistema deberá manejar información sensible o activos críticos.
- Deberá poseer múltiples actores, reglas de negocio y dependencias.
- Al menos un proceso deberá tener consecuencias relevantes ante fallos.
- Existirán requisitos susceptibles de contradicción, cambio o impacto transversal.
- El sistema deberá permitir analizar seguridad, confiabilidad, especificación, verificación, configuración y métricas.
- El equipo deberá mantener un repositorio organizado de artefactos y evidencias.

## 5. Desarrollo del proyecto

### FASE 1. Ingeniería de seguridad
- Identificar activos críticos, amenazas, vulnerabilidades, riesgos y controles.
- Analizar confidencialidad, integridad y disponibilidad según los requisitos del sistema.
- Relacionar los controles con requisitos, diseño, implementación, pruebas, despliegue y mantenimiento.
- Justificar técnicamente la prioridad de los riesgos y la suficiencia de los controles.

Producto: matriz Activo → Amenaza → Vulnerabilidad → Riesgo → Control → Evidencia y matriz Etapa → Riesgo → Práctica → Evidencia.

### FASE 2. Ingeniería de confiabilidad
- Analizar escenarios de fallo y comportamiento operacional.
- Calcular e interpretar MTTF, MTTR, MTBF y disponibilidad utilizando datos proporcionados u obtenidos de forma controlada.
- Determinar qué componentes representan mayor amenaza para la confiabilidad.
- Proponer acciones justificadas para mejorar la confiabilidad sin depender de un único indicador.

Producto: matriz Fallo → Frecuencia → Impacto → Recuperación → Indicador, cálculos y diagnóstico técnico.

### FASE 3. Reconstrucción mediante Cleanroom
- Seleccionar un módulo crítico del sistema.
- Rediseñar conceptualmente su proceso utilizando prevención de defectos y desarrollo incremental.
- Organizar Incremento → Especificación → Diseño → Verificación → Certificación.
- Contrastar el enfoque Cleanroom con un proceso centrado principalmente en detección y corrección de defectos.

Producto: expediente Cleanroom del módulo crítico y análisis comparativo.

### FASE 4. Formalización del comportamiento crítico
- Seleccionar al menos tres requisitos críticos.
- Transformar los requisitos desde lenguaje natural hacia especificaciones con estados, operaciones, precondiciones, postcondiciones, invariantes y restricciones.
- Detectar ambigüedades e inconsistencias.
- Demostrar la correspondencia entre requerimiento y comportamiento especificado.

Producto: matriz Requisito → Operación → Precondición → Postcondición → Invariante → Restricción → Evidencia.

### FASE 5. Modelado formal y verificación
- Construir un modelo del comportamiento del módulo crítico.
- Representar estados, transiciones, propiedades y restricciones.
- Identificar estados válidos, inválidos, inaccesibles o contradictorios.
- Verificar propiedades relevantes respecto de los requerimientos.
- Documentar contraejemplos, inconsistencias o comportamientos no previstos cuando existan.

Producto: modelo formal, expediente de verificación y matriz Requisito → Propiedad → Verificación → Resultado → Evidencia.

### FASE 6. Gestión de Configuración del Software
- Identificar los elementos de configuración (CI) del proyecto.
- Definir nomenclatura, responsables, versiones, dependencias y estados.
- Establecer líneas base y criterios de creación/aprobación.
- Demostrar cómo se preservará la integridad de requisitos, modelos, código, pruebas y documentación.

Producto: Plan de Gestión de Configuración, inventario de CI y estructura de líneas base.

### FASE 7. Repositorio, control de versiones y gestión de cambios
- Implementar un repositorio real para los artefactos controlados.
- Definir estrategia de ramas, commits, tags/releases e integración.
- Registrar solicitudes de cambio y su trazabilidad.
- Gestionar al menos un conflicto o escenario de integración controlada.
- Demostrar que el historial permite reconstruir la evolución del producto.

Producto: repositorio, evidencias de versionamiento y expediente de cambios.

### FASE 8. Cambio de emergencia
- Realizar un cambio (un-RFC) crítico posterior a la línea base.
- Realizar análisis de impacto sobre requisitos, riesgos, controles, modelos, pruebas, configuración y métricas.
- Emitir una decisión técnica sobre aceptación, rechazo o aplazamiento.
- Implementar o modelar el cambio autorizado, ejecutar las verificaciones necesarias y establecer una nueva línea base.
- Demostrar exactamente qué cambió y qué permaneció estable.

Producto: RFC → Análisis de impacto → Decisión → Modificación → Versión → Prueba/Verificación → Evidencia → Nueva línea base.

### FASE 9. Métricas del producto software
- Definir preguntas de ingeniería que deban responderse mediante medición.
- Seleccionar medidas, métricas e indicadores pertinentes.
- Definir fórmula, unidad, fuente de datos, umbral y criterio de interpretación.
- Comparar cuando sea pertinente el comportamiento antes y después del cambio.
- Evitar métricas decorativas que no conduzcan a una decisión.

Producto: catálogo de métricas, hoja de cálculo/resultados y perfil cuantitativo de calidad.

### FASE 10. Matriz de evidencia
- Integrar todos los artefactos en una cadena verificable.
- Comprobar que cada requisito crítico posee evidencia suficiente.
- Identificar huecos de trazabilidad o contradicciones entre artefactos.
- Emitir un dictamen técnico final sobre el estado del producto.

Producto: matriz Requisito → Riesgo → Control → Especificación → Modelo → Prueba → Configuración → Versión → Métrica → Evidencia.

## 6. Incidente obligatorio: requisito contradictorio
Durante el desarrollo, se incorporará un requisito nuevo que pueda entrar en conflicto con una propiedad, restricción o requisito existente. El equipo deberá determinar si ambos pueden coexistir y sustentar su conclusión mediante la especificación y el modelo, no mediante opinión.

El expediente deberá mostrar:
- requisito original y requisito nuevo;
- propiedades o invariantes afectadas;
- posible contradicción o estado imposible;
- evidencia de verificación;
- decisión técnica y tratamiento propuesto.

## 7. Cambio de emergencia obligatorio
Ejemplo de RFC: «El sistema deberá incorporar autenticación multifactor para todas las operaciones críticas. Las sesiones existentes deberán mantenerse compatibles y la modificación no podrá degradar los niveles de disponibilidad comprometidos».

El equipo deberá demostrar la cadena completa:

RFC → Impacto → Riesgo → Decisión → Cambio → Versión → Verificación/Prueba → Métrica → Evidencia → Nueva línea base

## 8. Matriz obligatoria
| REQ | Riesgo | Control | Especificación | Modelo | Prueba | CI/Versión | Métrica | Evidencia |
|---|---|---|---|---|---|---|---|---|
| Completar | Completar | Completar | Completar | Completar | Completar | Completar | Completar | Completar |

Regla: si una fila crítica termina sin evidencia verificable, el equipo no podrá afirmar que ese requisito está demostrado.

## 9. Entregables obligatorios
1. Expediente técnico del sistema de misión crítica.
2. Modelo de activos, amenazas, vulnerabilidades, riesgos y controles.
3. Informe cuantitativo de confiabilidad.
4. Expediente de aplicación de Cleanroom.
5. Especificaciones funcionales/formales de requisitos críticos.
6. Modelo formal y expediente de verificación.
7. Plan de Gestión de Configuración.
8. Inventario de elementos de configuración y líneas base.
9. Repositorio y evidencias de control de versiones.
10. Expediente de solicitudes y decisiones de cambio.
11. Informe del requisito contradictorio.
12. Informe de impacto y tratamiento del cambio de emergencia.
13. Catálogo, cálculo e interpretación de métricas del producto.
14. Matriz maestra de trazabilidad y evidencias.
15. Informe técnico final de certificación.
16. Defensa.

## 10. Estructura del informe final
17. Portada e identificación del equipo.
18. Resumen ejecutivo.
19. Descripción del sistema y criticidad.
20. Requisitos y arquitectura/contexto relevante.
21. Ingeniería de seguridad.
22. Análisis de confiabilidad.
23. Aplicación de Cleanroom.
24. Especificación funcional/formal.
25. Modelado y verificación.
26. Gestión de configuración y líneas base.
27. Repositorio y control de versiones.
28. Gestión de cambios.
29. Métricas e indicadores del producto.
30. Matriz de trazabilidad.
31. Análisis de incidentes/cambios impuestos.
32. Dictamen técnico final.
33. Conclusiones.
34. Anexos y evidencias.

## 11. Defensa
La defensa será una auditoría técnica. No se evaluará una exposición memorística del informe. Se solicitará evidencias concretas y el equipo deberá navegar inmediatamente entre requisito, riesgo, especificación, modelo, prueba, versión, métrica y evidencia.

Preguntas posibles:
- Demuestre que el requisito R-XX está satisfecho.
- ¿Qué evidencia demuestra que este control reduce el riesgo identificado?
- ¿Qué propiedad de su modelo garantiza este comportamiento?
- ¿Qué ocurre si se viola esta invariante?
- Demuestre que el cambio no rompió un requisito previamente validado.
- ¿Cuál es la línea base válida y cómo puede demostrarlo?
- ¿Qué métrica respalda su afirmación de confiabilidad?
- Su modelo afirma X y su evidencia muestra Y. ¿Cuál artefacto está equivocado?

## 12. Reglas de validez
- Una afirmación sin evidencia se considerará no demostrada.
- Una métrica sin fuente, fórmula, unidad e interpretación no será considerada evidencia cuantitativa válida.
- Un cambio sin solicitud, análisis de impacto, versión y evidencia será considerado no controlado.
- Una especificación que contradiga el modelo o una prueba que no corresponda a la versión evaluada generará una inconsistencia crítica.
- Las capturas de pantalla deberán estar contextualizadas y vinculadas con el artefacto que pretenden demostrar.
- Cada integrante deberá poder defender los elementos críticos del proyecto; la defensa podrá incluir evaluación individual.
- El equipo deberá poder reconstruir el estado exacto del producto en cada línea base declarada.

## 13. Principio
«LO QUE NO TENGA EVIDENCIA, NO EXISTE.»

La calidad no se declara: se demuestra mediante una cadena coherente, trazable y verificable de evidencia de ingeniería.

## 14. Requerimientos mínimos obligatorios del sistema a desarrollar
Condición obligatoria del proyecto: cada equipo deberá desarrollar y evolucionar un sistema software funcional. El sistema será el objeto real sobre el cual se aplicarán seguridad, confiabilidad, especificación y verificación, gestión de configuración, control de cambios y métricas. No se aceptará un proyecto exclusivamente documental.

### 14.1 Tipo de solución tecnológica
- Aplicación web funcional: OBLIGATORIA.
- Aplicación móvil: OBLIGATORIA.
- La aplicación web y móvil deberán consumir y compartir servicios, datos de forma coherente; no se aceptarán dos aplicaciones aisladas que representen soluciones distintas.
- La solución deberá disponer de una arquitectura identificable y documentada, con separación razonable de responsabilidades.
- La solución deberá utilizar persistencia de datos mediante una base de datos adecuada al problema.
- El código fuente y los artefactos controlados deberán mantenerse en un repositorio de control de versiones.

### 14.2 Requerimientos funcionales mínimos
| ID | Requerimiento | Exigencia mínima |
|---|---|---|
| RF-01 | Autenticación | Inicio y cierre de sesión con tratamiento seguro de credenciales. |
| RF-02 | Autorización | Control de acceso basado en roles/permisos; mínimo tres roles con capacidades diferenciadas. |
| RF-03 | Usuarios | Administración de usuarios, estados y permisos según las reglas del dominio. |
| RF-04 | Procesos de negocio | Implementar mínimo cinco procesos de negocio relevantes; no se considerarán suficientes cinco CRUD independientes. |
| RF-05 | Reglas de negocio | Implementar reglas verificables, restricciones, validaciones y condiciones de aceptación. |
| RF-06 | Proceso crítico | Incluir al menos un proceso crítico cuya falla, indisponibilidad o uso incorrecto tenga impacto demostrable. |
| RF-07 | Trazabilidad | Cada funcionalidad evaluada deberá vincularse con uno o más requisitos identificados. |
| RF-08 | Validaciones | Validar datos de entrada tanto en interfaz como en la lógica del sistema cuando corresponda. |
| RF-09 | Errores/excepciones | Gestionar excepciones y errores sin exponer información sensible ni dejar el sistema en estados inconsistentes. |
| RF-10 | Auditoría | Registrar eventos relevantes del sistema: accesos, operaciones críticas, cambios de estado o acciones equivalentes. |
| RF-11 | Búsqueda/consulta | Incorporar consultas, filtros o recuperación de información útil para los procesos del dominio. |
| RF-12 | Reportes/indicadores | Generar al menos un reporte, tablero o conjunto de indicadores asociado al propósito del sistema. |
| RF-13 | Notificaciones | Incorporar notificaciones o alertas cuando sean justificadas por el dominio. |
| RF-14 | Integración | Cuando el caso lo requiera, integrar al menos un servicio/API o componente externo, documentando sus riesgos y manejo de fallos. |

### 14.3 Requerimientos no funcionales mínimos
| ID | Atributo | Exigencia mínima |
|---|---|---|
| RNF-01 | Seguridad | Identificar activos, amenazas, vulnerabilidades y controles; aplicar controles acordes con los riesgos priorizados. |
| RNF-02 | Confidencialidad | Proteger datos sensibles y restringir su acceso según rol y necesidad. |
| RNF-03 | Integridad | Evitar modificaciones no autorizadas y preservar consistencia de datos y transacciones. |
| RNF-04 | Disponibilidad | Definir un objetivo de disponibilidad y evaluar su cumplimiento con evidencias. |
| RNF-05 | Confiabilidad | Medir e interpretar, cuando existan datos suficientes, MTTF, MTTR, MTBF y disponibilidad. |
| RNF-06 | Rendimiento | Definir al menos tiempos de respuesta o capacidad esperada para operaciones críticas y ejecutar pruebas. |
| RNF-07 | Usabilidad | Definir criterios observables de uso para los procesos principales y recoger evidencia de evaluación. |
| RNF-08 | Compatibilidad web | La aplicación web deberá funcionar correctamente en al menos dos navegadores actuales y adaptarse a resoluciones de escritorio y móvil. |
| RNF-09 | Compatibilidad móvil | Si existe app móvil, definir las versiones/plataformas soportadas y demostrar funcionamiento en el entorno declarado. |
| RNF-10 | Mantenibilidad | Mantener organización modular, convenciones, documentación mínima y trazabilidad que permitan modificar el sistema. |
| RNF-11 | Trazabilidad | Mantener relación Requisito → Riesgo/Control → Diseño/Especificación → Código/Versión → Prueba → Resultado → Evidencia. |
| RNF-12 | Recuperación | Definir y probar al menos un escenario de fallo/recuperación relacionado con el proceso crítico. |
| RNF-13 | Evidencia | Toda afirmación de cumplimiento deberá disponer de evidencia verificable y vinculada a la versión evaluada. |

### 14.4 Requerimientos técnicos y de arquitectura
- Arquitectura documentada mediante diagrama de componentes, contenedores, capas o equivalente, coherente con la implementación.
- Separación entre interfaz, lógica de negocio y persistencia o una arquitectura equivalente técnicamente justificada.
- API o capa de servicios cuando sea necesaria para compartir funcionalidad entre web, móvil u otros clientes.
- Base de datos con modelo documentado y restricciones de integridad pertinentes.
- Gestión segura de configuración y secretos; no se admitirán contraseñas, tokens o claves sensibles expuestas en el repositorio.
- Mecanismo de registro (logging) para operaciones y fallos relevantes.
- Ambientes o configuraciones diferenciables para desarrollo/pruebas y versión evaluada, cuando la tecnología lo permita.
- Procedimiento reproducible de instalación, configuración y ejecución del sistema.
- Identificación inequívoca de la versión entregada y de la línea base correspondiente.

### 14.5 Requerimientos específicos para aplicación móvil
- Autenticarse y respetar los mismos principios de autorización definidos para el sistema.
- Consumir servicios del sistema mediante interfaces documentadas y seguras.
- Implementar al menos dos procesos funcionales relevantes del dominio, no una simple vista informativa.
- Gestionar adecuadamente errores de conectividad y respuestas inválidas del servicio.
- Justificar el uso de capacidades móviles cuando corresponda: notificaciones, cámara, ubicación, biometría, almacenamiento local u otras.
- Mantener consistencia de datos con la aplicación web y el backend.
- Generar evidencias de pruebas funcionales y de compatibilidad en los dispositivos/emuladores declarados.

### 14.6 Seguridad exigible
- Las contraseñas no deberán almacenarse en texto plano.
- Las operaciones protegidas deberán verificar autorización en el servidor/backend y no únicamente ocultarse en la interfaz.
- Las entradas deberán validarse y tratarse para reducir riesgos de manipulación o inyección según la tecnología utilizada.
- Los errores no deberán revelar credenciales, secretos, trazas internas sensibles ni información innecesaria.
- Se deberá controlar la sesión, expiración o mecanismo equivalente de autenticación.
- Los eventos de seguridad relevantes deberán quedar registrados cuando corresponda.
- El equipo deberá documentar riesgos residuales: un control implementado no equivale a riesgo cero.

### 15.7 Pruebas exigibles
- Pruebas unitarias sobre componentes o reglas de negocio relevantes.
- Pruebas de integración sobre interacciones críticas entre componentes/servicios.
- Pruebas de sistema sobre flujos completos.
- Pruebas de aceptación vinculadas con requisitos y criterios de aceptación.
- Pruebas de seguridad seleccionadas según los riesgos identificados.
- Pruebas de rendimiento/carga sobre al menos una operación o flujo crítico.
- Pruebas de recuperación o comportamiento ante fallo.
- Pruebas de regresión después del cambio de emergencia.
- Pruebas web de funcionalidad, interfaz/navegación y compatibilidad.
- Si existe app móvil, pruebas funcionales, conectividad y compatibilidad móvil.
- Cada ejecución deberá registrar versión, ambiente, datos relevantes, resultado esperado, resultado obtenido, estado y evidencia.

### 14.8 Gestión de configuración y repositorio
- Todo equipo utilizará Git o un sistema equivalente de control de versiones.
- El repositorio deberá contener una estrategia de ramas coherente con el proyecto.
- Los commits deberán ser identificables y técnicamente significativos.
- Deberán existir tags/releases o mecanismos equivalentes para identificar versiones evaluadas.
- Se identificarán elementos de configuración: requisitos, modelos, código, scripts, pruebas, documentación y otros artefactos críticos.
- Se establecerá al menos una línea base previa al cambio impuesto y una nueva línea base posterior al cambio aprobado.
- Toda solicitud de cambio relevante deberá registrar origen, impacto, decisión, artefactos afectados, versión y evidencia de verificación.

### 14.9 Documentación y trazabilidad
- Catálogo de requisitos funcionales y no funcionales con identificadores únicos.
- Criterios de aceptación para los requisitos críticos.
- Arquitectura y modelo de datos.
- Matriz de riesgos de seguridad.
- Especificaciones formales del subconjunto crítico exigido por el proyecto.
- Modelo y resultados de verificación.
- Plan de gestión de configuración y líneas base.
- Plan/catálogo de métricas con fórmula, unidad, fuente, umbral e interpretación.
- Casos y resultados de prueba.
- Matriz maestra de trazabilidad y evidencias.
- Manual técnico de instalación/ejecución y guía breve de uso.
- Informe final que identifique claramente limitaciones, incumplimientos y riesgos residuales.
