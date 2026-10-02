# 01. Actores del sistema MotoYa

MotoYa conecta pasajeros con conductores de moto lineal en Huamanga, Ayacucho. Una aplicación Flutter ofrece dos modos de uso; el personal utiliza un panel Flutter Web con cuentas independientes.

| Actor | Objetivo y responsabilidades | Acceso y límites |
|---|---|---|
| Pasajero | Solicitar un viaje, negociar, elegir conductor, seguir el servicio, activar SOS y calificar. | Consulta sus solicitudes, ofertas y viajes; no modifica saldo ni aprobaciones. |
| Conductor | Presentar identidad, moto y documentos; conectarse, aceptar o contraofertar, ejecutar viajes y solicitar recargas. | Solo opera con registro aprobado, disponibilidad y saldo suficiente. No aprueba sus propias recargas. |
| Agente de soporte | Revisar documentos y abonos; atender SOS, reclamos y sanciones autorizadas. | Acceso limitado por rol y caso; conserva motivo y evidencia de cada decisión. |
| Administrador | Supervisar operación, agentes, incidencias y métricas. | No dispone automáticamente de todos los controles del dueño. |
| Dueño | Gestionar tarifas, comisión, administradores, finanzas y decisiones sensibles. | Autenticación reforzada y auditoría de cambios. |
| Contador | Consultar y exportar reportes financieros. | Rol opcional de consulta, sin edición operativa. |
| Servicio de mapas | Proporcionar mapa, ruta, distancia y búsqueda de direcciones. | Se integra mediante adaptadores; no determina la tarifa de MotoYa. |
| Servicios de avisos | Enviar notificaciones push y SMS de verificación o emergencia. | FCM y proveedor SMS; entregar un aviso no equivale a atender un SOS. |

## Relaciones y autorización

La identidad común es Usuario. Cambiar al modo conductor no concede autorización mientras la revisión permanezca pendiente. Los permisos combinan identidad, rol y relación con el recurso: ser participante del viaje, propietario del documento o personal autorizado para el caso.

El pasajero paga directamente al conductor fuera de la plataforma. Soporte comprueba el abono real de las recargas antes de acreditar saldo. La evidencia visual por sí sola no acredita una transferencia.

**Fuente:** ENTREGABLE-02_MotoYa.pdf, secciones «Actores del sistema» e «Identidad, reglas y persistencia».

[Historias de usuario →](02-historias-del-usuario.md)
