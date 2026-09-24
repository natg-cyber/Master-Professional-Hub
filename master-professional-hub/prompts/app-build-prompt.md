# Prompt de construcción — Master Professional Hub como app interactiva

Pega este prompt en un agente de desarrollo de software o en una herramienta de creación de apps. Adjunta `Master_Professional Hub_Prompt.md` y `Job_Application_Tracker.xlsx` como archivos de referencia.

---

## PROMPT

Actúa como product designer, arquitecto de software y desarrollador full-stack senior. Convierte el sistema de Career Coach, búsqueda de empleo y networking descrito en los archivos adjuntos en una aplicación interactiva, sencilla y funcional para una usuaria individual.

### 1. Objetivo del producto

Construye un **Master Professional Hub** que permita:

1. Registrar y seguir oportunidades laborales desde su descubrimiento hasta la entrevista/cierre.
2. Preparar CVs, revisiones ATS, cover letters e интервью prep por oportunidad, usando contenido y evidencia que aporte la usuaria.
3. Gestionar contactos y conversaciones de networking sin asumir que cada contacto conduce a una vacante.
4. Vincular una conversación con una empresa o una postulación cuando la usuaria lo decida.
5. Importar el Job Application Tracker existente y descargar los datos para seguir trabajando en Excel.

La aplicación organiza y prepara el trabajo; no postula a empleos, no envía mensajes, no contacta personas ni modifica archivos externos sin una acción explícita de la usuaria.

### 2. Antes de construir

1. Inspecciona los dos archivos adjuntos. Trata `Master_Professional Hub_Prompt.md` como reglas de negocio y `Job_Application_Tracker.xlsx` como plantilla y fuente de compatibilidad.
2. Conserva las hojas y columnas del tracker real, que pueden cambiar entre versiones. La versión actualmente inspeccionada contiene `Dashboard`, `Posiciones`, `Prep Entrevistas`, `Investigacion Empresa` y `Networking`. Encabezados detectados:
   - `Posiciones`: `ID`, `Fuente`, `Empresa`, `Rol`, `Fecha`, `Link JD`, `Score (1-10)`, `% Match`, `Keywords Faltantes`, `Red Flags (IDs)`, `Red Flags Resueltas`, `ATS Pass (Si/No)`, `Estado CV`, `Estado Cover Letter`, `Estado General`, `Resultado`.
   - `Prep Entrevistas`: `ID Posicion`, `Pregunta Conductual`, `Situation`, `Task`, `Action`, `Result`, `Takeaway / Tie-back`, `RF que resuelve`, `Fecha`.
   - `Investigacion Empresa`: `ID Posicion`, `Empresa`, `Reclutador / Hiring Manager`, `Hallazgos clave (empresa)`, `Hallazgos publicos (reclutador)`, `Fecha`.
   - `Networking`: `Nombre`, `Rol`, `Empresa`, `Como la conoci`, `Fecha contacto`, `Objetivo conversacion`, `Puntos de conexion (Hecho/Posible/Pregunta abierta)`, `Fecha conversacion`, `Reflexion`, `Siguiente paso`, `Estado`.
   - `Dashboard`: hoja de resumen; inspeccionar su diseño/fórmulas antes de exportar.
3. No reemplaces ni renombres las hojas o encabezados originales. Detecta la estructura de la versión que importe la usuaria; si no coincide, muestra el mapeo y pide confirmación. Añade campos propios de la app en una hoja adicional si hace falta. Conserva valores y columnas desconocidas al importar/exportar.
4. Si el entorno elegido no puede generar XLSX fielmente, ofrece CSV para cada tabla y JSON completo como alternativa, e informa claramente la limitación antes de declarar que XLSX funciona.
5. Primero presenta un plan breve de arquitectura, modelo de datos, pantallas y estrategia de importación/exportación. Después implementa el MVP en el workspace y entrega instrucciones para ejecutarlo. No te detengas en una maqueta si el entorno permite construir una app funcional.

### 3. Usuarios, idioma y experiencia

- Diseña para una sola usuaria; no agregues cuentas, roles, colaboración multiusuario ni pagos al MVP.
- Interfaz bilingüe ES/EN; el idioma inicial se puede elegir. No traduzcas nombres de hojas ni encabezados existentes del tracker.
- Interfaz clara y accesible, adaptable a escritorio y móvil. Mantén la navegación y acciones principales simples.
- La app debe poder usarse sin conexión a servicios de IA: registrar, editar, buscar, vincular, filtrar, importar y exportar siempre funcionan.
- Si se conecta un modelo de IA, delimita esa integración en un servicio reemplazable. No inventes evidencia profesional. Muestra el contenido generado como borrador editable y rastrea a qué datos de origen se apoya.

### 3A. Metodologías que deben quedar visibles en la experiencia

Presenta estas metodologías como el método de trabajo del producto. Identifica visualmente cuál se aplica en cada fase, sin convertirlas en etiquetas vacías:

- **Career coaching:** estilo colaborativo y centrado en la usuaria; aclarar objetivo, reflejar contexto, presentar opciones/compromisos y dejar la decisión en sus manos. No bloquear entregables directos con preguntas innecesarias.
- **START:** para preparar respuestas conductuales y reflexionar sobre experiencias: **Situation, Task, Action, Result, Takeaway/Tie-back**. Distingue la contribución personal y la evidencia disponible; deja componentes sin confirmar abiertos, sin inventar detalles.
- **Google XYZ:** editor de bullets de CV: X = resultado/contribución, Y = evidencia/medida, Z = acción. Usa el patrón “Accomplished X, as measured by Y, by doing Z” solo con hechos aportados. Si no hay métrica, propone una formulación cualitativa honesta.
- **Senior recruiter first-pass / red-flag reading:** revisión inicial aproximada de 10 segundos para ver rol, relevancia, seniority, evidencia y gaps. Presenta los RF como riesgos potenciales que debe verificar el usuario, ligados a evidencia concreta y a la JD; distingue problema de presentación de gap real.

En cada resultado de IA muestra el nombre del método aplicado y los campos/componentes utilizados; incluye una nota breve cuando falte evidencia. Permite a la usuaria editar el análisis y el borrador.

### 4. Navegación principal

**Onboarding inicial: presentación de la usuaria, luego router:** En el primer uso, pedir a la usuaria que presente su sector/área profesional y los tipos de roles o postulaciones para los que busca coaching. Ejemplo: “sector: urban planning / desarrollo urbano; roles: project coordination, development approvals, permitting o construction administration”. Guardar como `ProfessionalProfile` reutilizable (sector, roles, ubicación si la indica y objetivo de coaching si lo comparte). No inventar datos ni pedir de nuevo un perfil que ya esté disponible y vigente. Si la usuaria entrega perfil y elección de flujo en el mismo mensaje, aceptar ambos.

Después de esa presentación (o de reutilizar el perfil vigente), mostrar el router antes de iniciar intake de una vacante o preguntas específicas de networking:

> **¿Qué quieres trabajar ahora?**
> 1. **Una vacante o postulación**
> 2. **Networking**
> 3. **Conectar networking con una vacante existente**

No abras por defecto una vacante, no exijas datos de postulación antes de esta selección y no combines flujos sin que la usuaria elija la opción 3.

- **Si elige 1:** abrir el listado de oportunidades existentes y ofrecer `Retomar una vacante` o `Añadir una vacante`. Al elegir/crear una, cargar su registro único y continuar desde la fase solicitada; pedir solo datos faltantes para esa fase.
- **Si elige 2:** preguntar qué quiere hacer en networking: `Explorar sector/rol/comunidad`, `Preparar conversación o contacto` o `Registrar conversación`. No pedir ni crear una vacante como requisito. Mantener los registros de networking independientes salvo que la usuaria decida vincularlos.
- **Si elige 3:** mostrar y permitir buscar/seleccionar una vacante existente primero; después ofrecer `Vincular un contacto/conversación existente` o `Crear un contacto/conversación relacionado`. No crear una candidatura ni enviar mensajes por la acción de vincular.
- Si hay más de una vacante o contacto que coincide, pedir que la usuaria elija. Si no hay registros compatibles, ofrecer crear uno o volver al menú inicial.
- Mantener visible `Cambiar de flujo` para volver al router sin perder el borrador actual. Guardar borradores y mostrar su estado antes de salir.
- Si la usuaria ya elige explícitamente una de las tres opciones en el mismo mensaje, tomar esa selección como respuesta y no repetir la pregunta. No volver a pedir presentación si `ProfessionalProfile` está disponible y vigente; no repetir el router durante el mismo flujo salvo que la usuaria seleccione `Cambiar de flujo` o inicie una nueva sesión.

Implementa estas áreas:

1. **Overview / Inicio:** próximas acciones y entrevistas, postulaciones activas, conversaciones recientes, seguimientos vencidos/próximos y accesos rápidos. No inventes métricas sin registros suficientes.
2. **Opportunities / Vacantes:** tabla y vista de detalle de oportunidades/postulaciones, búsqueda y filtros por estado, empresa, rol, sector y fuente.
3. **Networking:** lista de contactos y organizaciones; conversaciones, notas, próximos seguimientos y oportunidades relacionadas.
4. **Career materials / Materiales:** CV base y borradores/versiones por postulación, cover letters, preguntas y respuestas START. Si no se implementa almacenamiento documental seguro, permitir metadatos/enlaces y descarga del texto, sin fingir que se guarda un archivo.
5. **Import & Export:** importar tracker, previsualizar mapeo/errores, descargar XLSX y CSV/JSON.
6. **Settings:** idioma, preferencias locales, privacidad y gestión/exportación/eliminación de datos.

### 5. Modelo de datos

Usa identificadores estables y relaciones explícitas. Como mínimo:

```text
Opportunity
- id, company, job_title, location, sector, job_description, source, source_url
- date_found, date_applied, status, next_action, next_action_date
- initial_match_score, revised_match_score, matches_and_gaps, top_skills, full_skills
- clarifying_questions, resume_version_id, cover_letter_reference, start_examples
- red_flags[]: id, description, evidence_status, status
- created_at, updated_at

Contact
- id, name, title, organization, professional_profile_url, source/verification_note
- known_facts, possible_connections_to_confirm, open_questions, notes
- created_at, updated_at

Conversation
- id, contact_id, date, channel, user_stated_summary, learnings, commitments
- next_step, follow_up_date, follow_up_status, draft_message
- related_opportunity_ids[] (optional; only link when user chooses)
- created_at, updated_at

ResumeVersion / CareerArtifact
- id, opportunity_id (optional), artifact_type, version_label, content or file reference
- status: Draft | Proposed | Approved | Archived; approval is version-specific
- created_at, updated_at
```

No exijas una vacante para crear un contacto o registrar networking. Las relaciones de contacto, conversación, organización y vacante son opcionales y editables. No dupliques una vacante al vincular un contacto.

### 6. Flujo de vacantes

Estados iniciales configurables, con estos valores por defecto:

`Exploring → Intake incomplete → Scored → Resume draft → Resume approved → Applied → Interview confirmed → Closed`.

- Un registro por vacante. Recopila empresa, título, JD y CV una vez; reutilízalos en las fases. Solicita solo campos faltantes para la acción actual.
- Fase 1: evaluación de ajuste, fortalezas, evidencia transferible, gaps, keywords y RF1…RF3 estables por oportunidad.
- Fase 2: borrador de CV adaptado, con evidencia real y cambios visibles.
- Fase 3a: revisión ATS/lectura inicial y comparación de puntaje con el mismo criterio; no promete pasar ATS.
- Fase 3b: cover letter bloqueada hasta aprobación explícita de la versión de CV. El borrador no se envía solo.
- Fases de entrevista: investigar empresa solo con fuentes disponibles; preguntas técnicas/conductuales y respuestas START sin inventar resultados.
- Loop de red flags: evidencia nueva propone una edición; no resuelve RF hasta que el cambio respaldado esté aprobado.
- Buscar vacantes solo si se integra una fuente de búsqueda disponible. Si no existe, la usuaria puede ingresar una vacante manualmente o importar datos; nunca simular resultados.

### 7. Flujo de networking conectado con vacantes

El flujo empieza desde el **router inicial de la sección 4**. Networking es una ruta de primera clase y no depende de una vacante. Solo la opción explícita `Conectar networking con una vacante existente` abre el puente entre ambos módulos.

Networking tiene tres puntos de entrada independientes:

**A. Explorar sector, rol o comunidad**
- Captura objetivo, sector/tema, geografía y límites prácticos solo si faltan.
- Sugiere un plan de investigación/conexiones como borrador; no asume que la usuaria está buscando empleo.

**B. Preparar contacto/conversación**
- Presenta información como `Hecho verificable | Posible conexión por confirmar | Pregunta abierta`.
- Permite preparar objetivo, apertura, tres preguntas, guía flexible, cierre y borrador de mensaje.
- Nunca envía mensajes ni inventa familiaridad, compromisos o atributos personales.

**C. Registrar conversación**
- Resume solo lo que aporte la usuaria.
- Captura aprendizajes, recursos, compromisos, próximo paso y fecha opcional de seguimiento.
- Propone el borrador de seguimiento y registro; la usuaria revisa/edita antes de marcarlo como listo.

**Puente networking ↔ vacantes**
- Desde una conversación, ofrecer `Vincular a una vacante existente`, `Crear una vacante a partir de esta oportunidad` o `Dejar sin vincular`.
- Desde una vacante, ofrecer `Añadir contacto relacionado` o `Preparar networking sobre esta empresa/rol`.
- Vincular no significa aplicar ni contactar; requiere acción explícita. Mantén una sola Opportunity y relaciona Contact/Conversation por ID.
- Un dato compartido (empresa, título, sector, fuente) puede prellenarse como propuesta editable. No convertir una conversación en candidatura automáticamente.
- Mostrar una línea temporal sencilla que diferencie hitos de vacante y de networking, con origen y fecha.

### 8. Gates, aprobaciones y honestidad

- Mostrar un diff/preview antes de importar, sobrescribir o aplicar cambios masivos; permitir confirmar, cancelar y resolver duplicados.
- CV: `Proposed → Approved` mediante acción explícita, siempre para una versión identificada. Una nueva edición vuelve a Proposed.
- Cover letter: no se habilita como final hasta CV Approved; sigue siendo un borrador hasta su propia aprobación.
- Tracker: nunca escribir en el archivo original al abrir/importar. Trabajar en datos de la app; al exportar, preservar una copia con el nombre que elija la usuaria.
- Las acciones de `Apply`, `Send`, `Contact`, `Upload externally` o similares no deben simularse. MVP solo genera borradores y archivos descargables.
- Errores y falta de datos producen estados `Blocked` con razón clara y acción para resolver, no respuestas inventadas.
- Añade confirmación previa a eliminar registros y ofrece exportación antes de borrar datos.

### 9. Job Tracker: importación y descarga

El tracker debe ser utilizable tanto dentro como fuera de la app.

**Importación**
- Importar el XLSX existente desde el dispositivo.
- Leer hojas y encabezados; mapear por nombre sin depender del orden de columnas.
- Mostrar cantidad de registros, campos que se mapearán, columnas desconocidas, filas vacías y posibles duplicados antes de importar.
- Importación idempotente razonable: detectar posibles duplicados por compañía + título + fecha/URL, pero nunca descartar automáticamente; dejar que la usuaria elija actualizar, conservar ambos o saltar.
- Preservar campos y valores desconocidos en datos de origen para que no se pierdan al exportar.

**Exportación**
- Descargar un XLSX actualizado basado en la copia importada, preservando sus hojas, encabezados, datos y fórmulas; incluir las tablas relacionadas en las hojas correspondientes y añadir una hoja auxiliar solo si se necesita.
- Mapear oportunidades a `Posiciones`, historias START a `Prep Entrevistas`, investigación a `Investigacion Empresa` y contactos/conversaciones a `Networking`, respetando los encabezados detectados y sin cambiar la estructura del original.
- Dashboard puede calcular resúmenes solo a partir de los datos disponibles; evitar errores por celdas vacías y marcar “sin datos” cuando aplique.
- Permitir descarga por separado de `Application Tracker.csv`, `Networking.csv` y copia completa `JSON`.
- Nombre sugerido versionado/fechado, por ejemplo `Job_Application_Tracker_YYYY-MM-DD.xlsx`; el original subido permanece intacto.
- Mostrar enlace/acción de descarga y confirmar qué hojas y registros contiene el archivo.

### 10. Privacidad y persistencia

- En MVP, preferir almacenamiento local del navegador/dispositivo, salvo que la plataforma ya provea una persistencia segura elegida por la usuaria.
- Indicar claramente dónde se guardan los datos, si la app requiere internet y qué datos se envían a un proveedor IA.
- No enviar CVs, contactos ni notas a servicios externos sin explicarlo y obtener elección explícita.
- Añadir exportar todos los datos y eliminar datos locales. No usar analytics/telemetría con información personal por defecto.
- No afirmar cifrado, respaldo en la nube, sincronización o persistencia entre dispositivos si no está implementado.

### 11. Requisitos de calidad y entrega

- Estructura mantenible, validación de entradas, manejo visible de errores y datos vacíos.
- Navegación por teclado, etiquetas accesibles, contraste legible y formularios con errores claros.
- Semillas de demostración opcionales, separadas de datos reales y borrables con un clic; nunca mezclar casos ficticios con el tracker importado.
- Incluye README con requisitos, ejecución, persistencia, limitaciones de IA, importación/exportación y recuperación/backup.
- Antes de finalizar, verifica manualmente los flujos principales: crear/editar vacante; crear contacto sin vacante; conversación independiente; vincular y desvincular conversación/vacante; gates de CV/carta; importar el XLSX de referencia sin alterar su copia; descargar y volver a importar el archivo exportado; errores de datos vacíos.
- Entrega la aplicación ejecutable, ubicación de archivos principales, pasos para iniciarla y una lista breve de funciones realizadas y límites pendientes. No declares funcional una capacidad que no verificaste.

### 12. Priorización de implementación

Construye por etapas, manteniendo un incremento utilizable:

1. **MVP base:** navegación, almacenamiento local, oportunidades, contactos/conversaciones, links opcionales, estados/aprobaciones y CSV/JSON.
2. **Tracker Excel:** importación previsualizada y exportación XLSX que conserva plantilla/columnas.
3. **IA opcional:** borradores de análisis, CV, carta y START mediante proveedor configurable y controles de privacidad.
4. **Integraciones futuras:** búsqueda de vacantes/calendarios/CRM solo cuando una API real y autorización de usuaria estén disponibles.

No añadas alcance futuro como si estuviera construido. Si el entorno no permite una de estas etapas, termina la parte que sí funciona y reporta con precisión qué falta para implementarla.

---
