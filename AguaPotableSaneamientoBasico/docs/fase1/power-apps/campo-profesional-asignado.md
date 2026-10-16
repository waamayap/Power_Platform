**Configuración del campo Profesional asignado**

*Power Apps conectado a SharePoint*

# Objetivo

Documentar la configuración utilizada para que el campo Profesional asignado muestre correctamente el nombre del usuario seleccionado en Power Apps.

La configuración se basa únicamente en la función **Choices** de SharePoint y en la propiedad **DisplayFields** del ComboBox.

# 1. Contexto

El campo **Profesional asignado** corresponde a una columna de SharePoint de tipo **Persona o grupo** dentro de la lista **Solicitudes**.

En Power Apps, este campo se representa mediante un control de selección tipo ComboBox. La finalidad es que el usuario pueda seleccionar el profesional asignado y que el formulario muestre el nombre de la persona, no el identificador técnico ni el valor Claims.

# 2. Configuración aplicada

## 2.1 Propiedad Items

En el control del campo Profesional asignado, se configuró la propiedad Items con la siguiente fórmula:

> Choices(\[@Solicitudes\].'Profesional asignado')

Esta fórmula toma directamente las opciones de usuario disponibles desde la columna Persona o grupo de SharePoint.

## 2.2 Propiedad DisplayFields

En el mismo control, se configuró la propiedad DisplayFields así:

> \["DisplayName"\]

Esta propiedad indica que Power Apps debe mostrar el nombre visible del usuario seleccionado.

# 3. Resumen de propiedades

|                                        |               |                                                  |
|----------------------------------------|---------------|--------------------------------------------------|
| **Elemento**                           | **Propiedad** | **Valor configurado**                            |
| Control del campo Profesional asignado | Items         | Choices(\[@Solicitudes\].'Profesional asignado') |
| Control del campo Profesional asignado | DisplayFields | \["DisplayName"\]                                |

# 4. Resultado esperado

-   El campo Profesional asignado carga usuarios desde la columna de SharePoint.

-   El formulario muestra el nombre del profesional seleccionado.

-   Se evita que aparezca el valor técnico en formato Claims, por ejemplo: i:0\#.f\|membership\|correo@dominio.com.

-   La información seleccionada queda lista para ser guardada en la lista Solicitudes.

# 5. Nota de control

Si el control muestra un texto similar a:

> i:0\#.f\|membership\|correo@dominio.com

se debe revisar la propiedad DisplayFields.

Para esta configuración, DisplayFields debe quedar exactamente así:

> \["DisplayName"\]*(Captura omitida en la versión pública: muestra datos del entorno institucional.)*
