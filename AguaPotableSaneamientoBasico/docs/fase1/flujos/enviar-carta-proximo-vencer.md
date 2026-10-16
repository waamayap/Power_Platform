<table><tbody><tr class="odd"><td><strong>DOCUMENTACIÓN DEL FLUJO<br />
APSB_Solicitudes_EnviarCartaCorreo_ProximoVencer</strong></td></tr></tbody></table>

Subsecretaría de Servicios Públicos  
Procedimiento técnico y funcional para notificación de solicitudes próximas a vencer

| **Versión** | **Fecha de elaboración** | **Tipo de documento** |
|-------------|--------------------------|-----------------------|
| 1.0         | 19/04/2026               | Guía operativa        |

# **1. Objetivo**

Documentar el flujo **APSB\_Solicitudes\_EnviarCartaCorreo\_ProximoVencer**, diseñado en Power Automate para identificar solicitudes que se encuentran próximas a vencer y, cuando cumplan las condiciones definidas por el proceso, generar una carta desde plantilla Word, enviarla al correo registrado en la lista de SharePoint y actualizar el estado del registro.

# **2. Alcance y prerrequisitos**

-   El flujo se ejecuta de forma automática mediante recurrencia y revisa los elementos de la lista Solicitudes.

-   La lógica aplica únicamente para registros con “Próximo a vencer (días)” igual a 1.

-   La carta solo se envía cuando el concepto de viabilidad está en “En espera”, el campo Correo no está vacío y la carta aún no ha sido marcada como enviada.

-   Se requiere acceso al sitio de SharePoint Componente\_APSB y a la biblioteca Documentos para generar y almacenar el archivo.

-   La acción “Rellenar una plantilla de Microsoft Word” puede exigir licenciamiento Power Automate Premium según la configuración del entorno.

# **3. Resumen funcional del flujo**

| **Etapa** | **Acción**                 | **Finalidad**                                                      | **Resultado**                                                 |
|-----------|----------------------------|--------------------------------------------------------------------|---------------------------------------------------------------|
| 1         | Recurrence                 | Disparar el flujo en la periodicidad definida.                     | Inicia la revisión automática.                                |
| 2         | Obtener elementos          | Traer los registros de la lista Solicitudes.                       | Se dispone del conjunto de solicitudes a evaluar.             |
| 3         | Aplicar a cada uno         | Recorrer cada elemento recuperado.                                 | Cada solicitud se procesa individualmente.                    |
| 4         | Bloque de condiciones      | Evaluar vencimiento, viabilidad, correo y estado de carta enviada. | Solo continúan los registros que cumplen todos los criterios. |
| 5         | Generación y envío         | Crear carta, adjuntarla al correo y notificar al destinatario.     | La solicitud recibe la comunicación de recordatorio.          |
| 6         | Actualización del elemento | Marcar el registro en SharePoint para evitar reenvíos.             | Queda trazabilidad del envío.                                 |

# **4. Lógica de negocio y condiciones**

El flujo está construido con cuatro filtros consecutivos. Cada condición se evalúa dentro del bloque True de la anterior, lo que reduce envíos innecesarios y conserva la lógica del proceso.

| **Orden** | **Condición**          | **Expresión / valor esperado**               | **Si es True**                                                | **Si es False**                                    |
|-----------|------------------------|----------------------------------------------|---------------------------------------------------------------|----------------------------------------------------|
| 1         | Próximo a vencer       | Valor igual a 1 día.                         | Continúa a validar viabilidad.                                | No ejecuta acciones para ese registro.             |
| 2         | Concepto de viabilidad | Debe ser “En espera”.                        | Continúa a validar el correo.                                 | No se envía carta para estados Viable o No viable. |
| 3         | Correo no vacío        | El campo Correo debe contener una dirección. | Continúa a validar si ya se envió carta.                      | No realiza envío por falta de destinatario.        |
| 4         | Carta no enviada       | CartaProximoVencerEnviada = No / false.      | Genera el documento, envía el correo y actualiza el registro. | Detiene el proceso para evitar reenvíos.           |

# **5. Configuración paso a paso**

## **Paso 1. Disparador “Recurrence”**

-   Configurar la frecuencia de ejecución, por ejemplo diaria, en el horario definido por el área.

-   Este disparador permite revisar automáticamente toda la lista sin intervención de Power Apps.

## **Paso 2. Acción “Obtener elementos”**

-   Seleccionar el sitio SharePoint del componente APSB y la lista Solicitudes.

-   Opcionalmente, se puede optimizar con filtro OData o límite superior para mejorar rendimiento.

## **Paso 3. Acción “Aplicar a cada uno”**

-   Iterar sobre cada elemento devuelto por la lista.

-   Dentro de este bloque se referencian campos del elemento actual, por ejemplo ID, Correo y Próximo a vencer (días).

## **Paso 4. Condiciones de negocio**

-   Primera condición: Próximo a vencer = 1.

-   Segunda condición: Concepto de viabilidad = En espera.

-   Tercera condición: el campo Correo no está vacío.

-   Cuarta condición: CartaProximoVencerEnviada = No.

## **Paso 5. Acción “Rellenar una plantilla de Microsoft Word”**

-   Seleccionar la plantilla ubicada en la biblioteca Documentos.

-   Asignar los controles de contenido definidos en la plantilla, por ejemplo: NumeroRadicadoEntrada, Remitente, Dirección, Teléfono y Correo.

-   Esta acción produce el documento base de la carta que luego será almacenado en SharePoint.

## **Paso 6. Acción “Crear archivo”**

-   Definir la carpeta destino dentro de la biblioteca de documentos, por ejemplo: /Documentos compartidos/CartasRespuesta/Generadas/Solicitud ampliacion.

-   Construir un nombre de archivo claro y único para cada carta.

-   Usar como contenido del archivo la salida del paso de plantilla Word.

## **Paso 7. Acción “Obtener contenido de archivo”**

-   Seleccionar el Id del archivo recién creado.

-   Esta acción permite adjuntar el documento al correo electrónico.

## **Paso 8. Acción “Enviar correo electrónico (V2)”**

-   En el campo A usar la columna Correo del elemento actual.

-   Definir un asunto institucional, por ejemplo: “Carta de recordatorio - solicitud próxima a vencer”.

-   Redactar el cuerpo del mensaje e incorporar el archivo como adjunto.

-   En Datos adjuntos, usar Nombre de Crear archivo y Contenido del archivo de Obtener contenido de archivo.

## **Paso 9. Acción “Actualizar elemento”**

-   Usar el ID del elemento de SharePoint, no el ID del archivo.

-   Actualizar los campos de control para dejar trazabilidad del envío.

-   Se recomienda cambiar CartaProximoVencerEnviada a Sí y conservar el resto de campos críticos del registro.

# **6. Campos clave y mapeo recomendado**

| **Componente**      | **Campo / parámetro**                     | **Origen recomendado**                                  | **Observación**                              |
|---------------------|-------------------------------------------|---------------------------------------------------------|----------------------------------------------|
| Condición 1         | Próximo a vencer (días)                   | Elemento actual de SharePoint                           | Debe evaluarse con valor 1.                  |
| Condición 2         | Concepto de viabilidad                    | Campo de la lista Solicitudes                           | Solo debe pasar el valor En espera.          |
| Condición 3         | Correo                                    | Campo Correo de la lista                                | Debe contener una dirección válida.          |
| Plantilla Word      | NumeroRadicadoEntrada                     | Número de radicado de entrada                           | Control de contenido en el .docx.            |
| Plantilla Word      | Remitente / Dirección / Teléfono / Correo | Campos homónimos de la lista                            | Mapear solo los que existan en la plantilla. |
| Correo (V2)         | A                                         | Correo                                                  | Destinatario principal.                      |
| Correo (V2)         | Adjunto - Nombre                          | Crear archivo &gt; Nombre                               | No usar Path ni DisplayName.                 |
| Correo (V2)         | Adjunto - Contenido                       | Obtener contenido de archivo &gt; Contenido del archivo | Valor binario del adjunto.                   |
| Actualizar elemento | Identificador                             | ID del elemento actual                                  | No usar el ItemId del archivo.               |
| Actualizar elemento | CartaProximoVencerEnviada                 | Sí                                                      | Evita reenvíos del mismo registro.           |

# **7. Recomendaciones y validaciones finales**

<table><tbody><tr class="odd"><td><ul><li><p>Verificar en el comprobador de flujo que no existan errores pendientes antes de activar el flujo.</p></li><li><p>Si se mantiene el uso de Word Online (Business), confirmar licenciamiento disponible para evitar bloqueos por Premium.</p></li><li><p>Probar el flujo con un registro controlado que tenga Próximo a vencer = 1, correo diligenciado, concepto En espera y carta no enviada.</p></li><li><p>Si el proceso no requiere documento adjunto, puede evaluarse una versión simplificada que envíe solo correo y elimine la dependencia de plantilla Word.</p></li></ul></td></tr></tbody></table>

# **Anexo. Vista general del flujo**

La siguiente imagen corresponde a la estructura general observada del flujo en Power Automate:

*(Captura omitida en la versión pública: muestra datos del entorno institucional.)*
