# Manual de usuario — Módulo de Solicitudes

**Sistema de Gestión de Proyectos — Agua Potable y Saneamiento Básico (SGP APSB)** · Versión 1.0 · agosto de 2026

> Esta versión pública no incluye las capturas de pantalla del manual original porque muestran datos reales de solicitudes. En el [README de la app](../../README.md) hay una vista general de la pantalla principal con los datos difuminados.

## 1. Introducción

Este manual explica cómo usar el módulo de Solicitudes del SGP APSB. La herramienta sirve para registrar, seguir y tramitar las solicitudes relacionadas con proyectos de acueducto y saneamiento básico.

Con el módulo se puede consultar el listado de solicitudes radicadas, crear solicitudes nuevas, editar la información de cada una y controlar su gestión hasta definir su viabilidad.

### 1.1 Alcance

- Consulta del listado general de solicitudes.
- Creación de una solicitud nueva.
- Edición y visualización de una solicitud existente.
- Registro de los datos generales de la solicitud.
- Gestión de la solicitud (visita técnica y documentos adjuntos).
- Definición de la viabilidad y del tipo de respuesta.

### 1.2 Usuarios

El manual está dirigido al equipo encargado de recibir, analizar y tramitar las solicitudes ciudadanas e institucionales sobre agua potable y saneamiento básico.

## 2. Acceso al módulo

Al entrar a la plataforma aparece un menú superior con las secciones **Solicitudes**, **Banco de Proyectos**, **Sistema de Gestión de Proyectos** y **Repositorio de proyectos**. La pestaña *Solicitudes* se abre por defecto y muestra todas las solicitudes registradas.

### 2.1 Filtro de búsqueda

Encima de la tabla hay un filtro con tres criterios de búsqueda: **Número de Radicado Entrada**, **Profesional Asignado** y **Concepto de viabilidad**.

## 3. Crear una solicitud nueva

En la pestaña *Solicitudes*, pulse el botón **«+»** de la esquina superior derecha del listado. Al pasar el cursor por encima aparece la etiqueta *Nueva solicitud*.

El sistema abre el formulario y asigna automáticamente el consecutivo **SolicitudID**. Después se diligencian los tres pasos descritos en el capítulo 5: Datos generales, Gestión de la solicitud y Viabilidad.

> **Nota:** el formulario conserva los datos mientras se navega entre pasos, pero se recomienda pulsar **Guardar** antes de salir.

## 4. Consultar y editar una solicitud

Cada fila del listado tiene dos íconos:

- 👁 **Ver solicitud:** muestra la información en modo de solo lectura.
- ✏️ **Editar solicitud:** permite modificar la solicitud.

Al pasar el cursor sobre cada ícono aparece una etiqueta con la acción.

## 5. Registro de una solicitud

El registro tiene tres pasos consecutivos. Se avanza con las flechas de la parte inferior del formulario y se puede guardar en cualquier momento con **Guardar**.

### 5.1 Paso 1 — Datos generales

Este paso tiene muchos campos, así que hay que desplazarse dentro del formulario para verlos todos.

- **SolicitudID:** consecutivo automático.
- **Origen del radicado:** canal por el que llegó la solicitud.

| Opción | Uso |
|---|---|
| Mercurio | Solicitud radicada por el sistema de correspondencia Mercurio |
| Plan de Desarrollo | Solicitud originada en el seguimiento al Plan de Desarrollo |
| Acción Judicial | Solicitud derivada de un requerimiento, tutela o acción judicial |
| Otras dependencias | Solicitud remitida por otra dependencia |
| Autoridades de control | Solicitud de un ente de control (Personería, Contraloría, Procuraduría, etc.) |
| Otros | Solicitud que no encaja en las categorías anteriores |

- **Número radicado entrada:** si el origen es *Mercurio*, el campo queda habilitado para digitar el radicado. Con los demás orígenes se bloquea y el sistema lo genera con la estructura **año-mes-día + consecutivo de 4 dígitos**. Ver [campo-numero-radicado-origen.md](power-apps/campo-numero-radicado-origen.md).
- **Fecha de radicado:** fecha en que el remitente radicó la solicitud.
- **Fecha de ingreso a la Subsecretaría:** fecha en que la dependencia recibió la solicitud.
- **Fecha de vencimiento:** fecha límite de respuesta, calculada automáticamente. Ver [flujo de 15 días hábiles](flujos/calcular-vencimiento-15-dias-habiles.md).
- **Asunto:** título breve del motivo de la solicitud.
- **Detalle de la solicitud:** descripción ampliada.
- **Adjuntos de la solicitud:** soportes en PDF, Excel, Word, JPG, etc.
- **Remitente, Dirección, Correo y Teléfono:** datos de contacto de quien radica.
- **Comuna:** comuna asociada a la solicitud.
- **Responsable:** persona de apoyo a la coordinación que radica la solicitud y la asigna.
- **Profesional asignado:** profesional del equipo APSB que gestiona la solicitud. Ver [campo-profesional-asignado.md](power-apps/campo-profesional-asignado.md).

### 5.2 Paso 2 — Gestión de la solicitud

- **Tiene visita técnica:** Sí / No.
- **Fecha de visita técnica:** fecha programada de la visita.
- **Concepto de la visita:** resultado o hallazgos de la visita.
- **Datos adjuntos:** informes, fotografías, actas, etc.

> Mientras no haya archivos, la sección muestra «No hay nada adjunto».

### 5.3 Paso 3 — Viabilidad

- **Resultado del análisis:** conclusiones del análisis técnico o administrativo.
- **Tipo de Respuesta:**

| Opción | Uso |
|---|---|
| Respuesta APSB | La Subsecretaría responde directamente |
| Traslado por competencia | La solicitud se remite a otra dependencia o entidad competente |
| Acuso de respuesta | Confirma el recibido de la respuesta emitida |
| En espera | La respuesta todavía no está definida |

- **Concepto de viabilidad:**

| Opción | Uso |
|---|---|
| Viable | La solicitud puede tramitarse favorablemente y pasa a priorización |
| No viable | La solicitud no puede tramitarse |
| En espera | La viabilidad aún no está definida |

> **Nota:** guarde con **Guardar** al final de cada paso antes de continuar.

## 6. Recomendaciones

- Verifique que el **Número de Radicado Entrada** sea exactamente el de la entidad de origen, porque relaciona la solicitud con el proyecto en las demás fases.
- Registre la fecha de la visita técnica en cuanto se programe.
- Adjunte los soportes apenas estén disponibles.
- Diligencie el **Concepto de viabilidad** solo cuando haya terminado el análisis.
- Guarde al finalizar cada paso para no perder información.
