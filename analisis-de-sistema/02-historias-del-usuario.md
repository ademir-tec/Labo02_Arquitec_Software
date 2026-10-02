# 02. Historias de usuario

Los identificadores conservan la trazabilidad del documento fuente. Los criterios deben comprobarse en servidor cuando involucren permisos, estados o dinero.

| ID | Historia | Criterio de aceptación | Requisitos |
|---|---|---|---|
| HU-01 | Como usuario, quiero verificar mi celular para acceder a una cuenta personal. | Un código válido activa la cuenta; uno incorrecto no permite el acceso. | RF-01 |
| HU-02 | Como conductor, quiero enviar identidad, moto y documentos para ser habilitado. | El registro queda en revisión; solo la aprobación permite operar. | RF-02 |
| HU-03 | Como pasajero, quiero elegir origen y destino y consultar un precio orientativo para proponer mi oferta. | Ruta válida, distancia y tarifa de referencia; oferta dentro de límites configurados. | RF-03, RF-04 |
| HU-04 | Como conductor, quiero aceptar o contraofertar solicitudes cercanas. | Solo recibe solicitudes elegibles y vigentes; la respuesta conserva precio y vencimiento. | RF-04, RF-05 |
| HU-05 | Como pasajero, quiero elegir una oferta para confirmar a mi conductor. | Se asigna un solo conductor y las ofertas restantes dejan de ser seleccionables. | RF-06 |
| HU-06 | Como pasajero, quiero seguir al conductor e iniciar mediante PIN. | Se muestra estado y última ubicación; llegada exige proximidad y PIN incorrecto impide inicio. | RF-07, RF-08 |
| HU-07 | Como participante, quiero chatear y activar SOS para comunicarme y pedir ayuda. | Chat solo para participantes; SOS conserva alerta y resultado de envío, separado de atención humana. | RF-09 |
| HU-08 | Como conductor, quiero finalizar y consultar la comisión para conocer mi saldo. | Finalizar repetidamente genera como máximo un descuento; cancelar no genera comisión de finalización. | RF-08, RF-10 |
| HU-09 | Como conductor, quiero solicitar una recarga para disponer de saldo. | Conserva monto, referencia y evidencia; solo se acredita tras comprobar el abono real. | RF-11 |
| HU-10 | Como agente, quiero revisar recargas y registros para aprobar los válidos. | Verifica permiso y registra decisión, motivo, actor y fecha; notifica al usuario. | RF-02, RF-11, RF-13 |
| HU-11 | Como participante, quiero calificar y reportar problemas del viaje. | Reseña y reclamo vinculados al viaje y a un autor autorizado. | RF-12 |
| HU-12 | Como dueño, quiero gestionar roles y parámetros para controlar la operación. | Cada cambio exige permiso y conserva valores anteriores y nuevos; reportes respetan el rol. | RF-13, RF-14 |

## Ejemplos de validación

- Dos selecciones simultáneas sobre una solicitud: solo una asignación puede confirmarse.
- Reintentar una finalización tras perder la respuesta: devuelve el resultado anterior, sin otro descuento.
- Reutilizar una referencia externa de recarga: no acredita un segundo movimiento.
- Activar SOS: crear la alerta y enviar push no permite marcarla automáticamente como atendida.

**Fuente:** ENTREGABLE-02_MotoYa.pdf, tabla 2 y plan de validación.

[← Actores](01-actores.md) · [Requisitos →](03-requisitos-funcionales.md)
