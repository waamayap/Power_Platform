# Esquema de listas de SharePoint
Columnas que usa la app en cada lista (sin URL ni identificadores reales).

## Solicitudes
| Columna | Tipo |
|---|---|
| ID | integer |
| Title | string |
| SolicitudID | string |
| Origen del radicado | object |
| Numero radicado entrada | string |
| Dirección | string |
| Correo | string |
| Teléfono | string |
| Remitente | string |
| Asunto | string |
| Detalle de la solicitud | string |
| Comuna | object |
| Fecha de radicado | string |
| Fecha de ingreso a la Subsecretaría de Servicios Públicos | string |
| Tiene visita técnica | object |
| Fecha de visita técnica | string |
| Concepto de la visita | string |
| Fecha de vencimiento | string |
| Próximo a vencer (días) | number |
| Vencimiento | string |
| Responsable | string |
| Profesional asignado | object |
| CorreoNotificadoProfesional | string |
| Número de radicado de la respuesta | string |
| Fecha de radicado de respuesta | string |
| Resultado del análisis | string |
| Tipo de Respuesta | object |
| Gestión | object |
| Concepto de viabilidad | object |
| RutaCartaRespuesta | string |
| NombreCartaRespuesta | string |
| EstadoCartaRespuesta | object |
| DetalleErrorCartaRespuesta | string |
| FechaGeneracionCarta | string |
| CartaProximoVencerEnviada | boolean |
| RutaCartaProximoVencer | string |
| FechaEnvioCartaProximoVencer | string |
| Etiqueta de color | string |
| Id. de activo de cumplimiento normativo | string |
| Informe de visita técnica | string |
| Nombre | string |
| Modificado | string |
| Creado | string |
| Creado por | object |
| Modificado por | object |

## BancoProyectos
| Columna | Tipo |
|---|---|
| ID | integer |
| Title | string |
| Numero radicado entrada | string |
| Fecha de priorización | string |
| Priorizado por | string |
| Nombre del proyecto | string |
| Tipo de sistema | object |
| Comuna | object |
| Calidad del agua | object |
| Puntaje calidad del agua | string |
| Continuidad | object |
| Puntaje continuidad | string |
| Cobertura | object |
| Puntaje cobertura | string |
| Estudios técnicos | object |
| Puntaje estudios técnicos | string |
| Estudios técnicos pendientes | array |
| Condición jurídica de priorización | array |
| Gestión jurídica predial | object |
| Puntaje gestión jurídica predial | string |
| Trámites jurídicos por gestionar | array |
| Clasificación del POT | object |
| Puntaje clasificación POT | string |
| Trámites Ambientales | object |
| Puntaje trámites ambientales | string |
| Trámites ambientales por gestionar | array |
| Impacto en costos de prestación | object |
| Puntaje impacto en costos | string |
| Participación ciudadana y legitimidad social | object |
| Puntaje participación ciudadana | string |
| Cobertura viviendas a beneficiar | object |
| Puntaje cobertura viviendas | string |
| Costo/Beneficio | object |
| Puntaje costo beneficio | string |
| Resultado de evaluación de criterios (%) | string |
| Concepto final | object |
| Observaciones técnicas | string |
| Fecha de entrega del diseño | string |
| Proveedor del diseño | string |
| Responsable | string |
| Tipo de proyecto | object |
| Etiqueta de color | string |
| Id. de activo de cumplimiento normativo | string |
| Modificado | string |
| Creado | string |
| Creado por | object |
| Modificado por | object |

## RepositorioProyectos
| Columna | Tipo |
|---|---|
| ID | integer |
| Title | string |
| Código proyecto | string |
| Numero radicado entrada | string |
| Fecha estimada entrega | string |
| Etapa | object |
| Tipo de intervención | object |
| Tipo de sistema | object |
| Tipo de contrato | object |
| Nombre del proyecto | string |
| Descripción del proyecto | string |
| Comuna - Corregimiento | object |
| Beneficiarios | number |
| Clase de beneficiarios | object |
| Número de contrato | string |
| Contratista | string |
| Fecha firma contrato | string |
| Presupuesto | number |
| Etiqueta de color | string |
| Id. de activo de cumplimiento normativo | string |
| Modificado | string |
| Creado | string |
| Creado por | object |
| Modificado por | object |

## SistemaGestionProyectos
| Columna | Tipo |
|---|---|
| ID | integer |
| Título | string |
| IDRepositorio | number |
| Numero radicado entrada | string |
| FaseID | number |
| ActividadID | number |
| Fecha de seguimiento | string |
| Número de contrato | string |
| Meta Beneficiarios | number |
| Beneficiarios Ejecutados | number |
| Avance Beneficiarios % | string |
| Fecha estimada entrega | string |
| Días de ampliación | number |
| Fecha real entrega | string |
| Presupuesto | number |
| Adición Presupuesto | number |
| Ejecución Pagos | number |
| Avance Pagos % | string |
| Planeación % | number |
| Consultoría y Diseño % | number |
| Contratación % | number |
| Supervisión % | number |
| Cierre y Liquidación % | number |
| Alerta | boolean |
| Observaciones | string |
| Etiqueta de color | string |
| Id. de activo de cumplimiento normativo | string |
| Modificado | string |
| Creado | string |
| Creado por | object |
| Modificado por | object |

## Fases
| Columna | Tipo |
|---|---|
| ID | integer |
| Título | string |
| Numero radicado entrada | string |
| FaseID | number |
| Nombre de la Fase | object |
| Estado | object |
| Orden | number |
| Fecha de Inicio | string |
| Fecha de Finalización Estimada | string |
| Fecha final Real | string |
| Porcentaje de Avance | number |
| Etiqueta de color | string |
| Id. de activo de cumplimiento normativo | string |
| Nombre del  Área | object |
| ProyectoID | string |
| Modificado | string |
| Creado | string |
| Creado por | object |
| Modificado por | object |

## Actividades
| Columna | Tipo |
|---|---|
| ID | integer |
| Título | string |
| Numero radicado entrada | string |
| AreaID | number |
| FaseID | number |
| Nombre de la Actividad | string |
| Estado | object |
| Responsable | object |
| Rol Responsable | object |
| Fecha estimada | string |
| Bloqueada | boolean |
| Observaciones | string |
| Etiqueta de color | string |
| Id. de activo de cumplimiento normativo | string |
| Modificado | string |
| Creado | string |
| Creado por | object |
| Modificado por | object |
