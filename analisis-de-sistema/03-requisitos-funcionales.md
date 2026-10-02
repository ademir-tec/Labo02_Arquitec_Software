# 03. Requisitos funcionales

La prioridad alta representa el núcleo del MVP; la media corresponde a capacidades complementarias.

| ID | Requisito y comportamiento verificable | Prioridad | Historias |
|---|---|---|---|
| RF-01 | Registrar usuarios, verificar celular, iniciar sesión y gestionar modos de cuenta. Cambiar modo no concede aprobación de conductor. | Alta | HU-01 |
| RF-02 | Registrar moto y documentos, revisar estado y habilitar exclusivamente conductores aprobados. | Alta | HU-02, HU-10 |
| RF-03 | Seleccionar recojo y destino; obtener ruta validada, distancia y tarifa de referencia. | Alta | HU-03 |
| RF-04 | Crear solicitudes y distribuirlas a conductores elegibles por proximidad, aprobación, conexión, disponibilidad y saldo. | Alta | HU-03, HU-04 |
| RF-05 | Aceptar o contraofertar; conservar precio, versión y vencimiento de la oferta vigente. | Alta | HU-04 |
| RF-06 | Confirmar una oferta, asignar un solo conductor y cerrar ofertas competidoras con validación transaccional. | Alta | HU-05 |
| RF-07 | Mantener estados, tiempos y ubicación; comprobar llegada y PIN antes de iniciar. | Alta | HU-06 |
| RF-08 | Gestionar espera, recargo, cancelación y no presentación según reglas del servicio. | Alta | HU-06, HU-08 |
| RF-09 | Ofrecer chat, datos compartibles, contactos de emergencia y SOS con seguimiento de envío y atención. | Alta | HU-07 |
| RF-10 | Finalizar, calcular comisión y registrar un único movimiento de saldo por viaje. | Alta | HU-08 |
| RF-11 | Solicitar recargas, verificar abono y acreditar una sola vez cada referencia externa confirmada. | Alta | HU-09, HU-10 |
| RF-12 | Registrar calificaciones, consultar historial y reportar problemas asociados a viajes propios. | Alta: calificación; media: historial y reclamos | HU-11 |
| RF-13 | Administrar roles, parámetros, sanciones y acciones del personal con auditoría. | Alta | HU-10, HU-12 |
| RF-14 | Mostrar métricas y reportes operativos y financieros según permisos. | Media | HU-12 |

## Reglas del negocio que condicionan el diseño

| Regla | Valor o condición del PDF | Control |
|---|---|---|
| Tarifa de referencia | S/ 2.14 por km; mínimo S/ 3.00. | Backend calcula con distancia de ruta validada. |
| Radio de búsqueda | 1.5 km; ampliación a 2.5 km y luego 3 km. | Servidor filtra cobertura y elegibilidad. |
| Llegada | A 100 m o menos del recojo. | Validar ubicación y estado; conservar evidencia. |
| Espera | Cinco minutos gratuitos; luego S/ 0.50 por minuto. | Tiempo de servidor desde llegada validada. |
| No presentación | Desde tres minutos y a 30 m o menos. | Regla distinta del inicio del recargo. |
| Inicio | PIN de cuatro dígitos; avisar a soporte tras tres intentos fallidos. | Validación en servidor; no exponer PIN en registros técnicos. |
| Comisión | S/ 0.333 por km de distancia planeada, descontada al finalizar. | Identificador único por viaje y redondeo uniforme. |
| Lanzamiento | Comisión puede ser cero. | Conservar monto teórico y promoción aplicada. |
| Cancelación | No genera comisión propia de un viaje terminado ni cobro al pasajero. | Validar transición y motivo. |
| Recarga | Confirmación humana del abono; referencia no reutilizable. | Transacción de referencia, movimiento y saldo. |

Almacenar importes finales en céntimos. La tasa de S/ 0.333 por km necesita precisión intermedia; redondear el resultado monetario final con una política uniforme, sin truncar la tasa a S/ 0.33.

## Parámetros pendientes de especificación

El PDF no fija límites exactos de negociación, duración de ofertas, tratamiento de fracciones de minuto ni nombres de los cinco distritos. Deben acordarse antes de implementar; no se presentan valores inventados como requisitos.

**Fuente:** ENTREGABLE-02_MotoYa.pdf, tabla 3 y flujo de solicitud y ciclo de vida.

[← Historias](02-historias-del-usuario.md) · [Calidad →](04-atributos-de-calidad.md)
