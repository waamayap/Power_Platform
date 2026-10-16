# Fase 1 — Documentación

Documentación de la Fase 1 del Sistema de Gestión de Proyectos APSB: gestión de solicitudes, priorización y creación de proyectos con Power Apps, SharePoint y Power Automate.

## Documentos generales

| Documento | Contenido |
|---|---|
| [Documentación técnica y funcional](documentacion-tecnica.md) | Arquitectura, modelo de datos, app, flujos, reglas de negocio, pruebas y operación |
| [Manual de usuario — Solicitudes](manual-usuario-solicitudes.md) | Uso del módulo paso a paso |
| [Modelo de datos (MER)](modelo-datos.md) | Columnas de Solicitudes, Priorización y Proyectos y sus relaciones |

## Flujos de Power Automate

| Flujo | Qué hace |
|---|---|
| [Calcular vencimiento 15 días hábiles](flujos/calcular-vencimiento-15-dias-habiles.md) | Calcula la fecha límite sin contar fines de semana ni festivos |
| [Actualizar próximo de vencimiento](flujos/actualizar-proximo-vencimiento.md) | Recalcula a diario los días restantes y alerta |
| [Enviar carta próximo a vencer](flujos/enviar-carta-proximo-vencer.md) | Notifica las solicitudes cercanas a su vencimiento |
| [Notificar profesional asignado](flujos/notificar-profesional-asignado.md) | Envía un correo cuando se asigna o cambia el profesional |
| [Generar carta de respuesta](flujos/generar-carta-respuesta.md) | Llena una plantilla de Word según la viabilidad |
| [Sincronizar Solicitudes → Priorización](flujos/sincronizar-solicitudes-priorizacion.md) | Lleva a Priorización las solicitudes viables |
| [Sincronizar Priorización → Proyectos](flujos/sincronizar-priorizacion-proyectos.md) | Crea el proyecto cuando la priorización se aprueba |
| [Generar código de proyecto](flujos/generar-codigo-proyecto.md) | Asigna el código `APSB-[tipo]-[comuna]-[consecutivo]` |
| [Crear fases al registrar proyecto](flujos/crear-fases.md) | Crea las 6 fases del ciclo de vida del proyecto |

## Configuración en Power Apps

| Documento | Contenido |
|---|---|
| [Campo Profesional asignado](power-apps/campo-profesional-asignado.md) | Selección de persona y correo para notificaciones |
| [Campo Número radicado según origen](power-apps/campo-numero-radicado-origen.md) | Habilita o genera el radicado según el origen |

---

> **Versión pública.** Se omitieron URLs del sitio de SharePoint, identificadores del entorno, correos institucionales, nombres de personas y las capturas que los muestran. Las capturas omitidas están marcadas en cada documento.
