# 04. Atributos de calidad

Estas metas provienen del PDF y son objetivos de validación, no resultados medidos ni garantías del proveedor. Se asignan identificadores AC para facilitar trazabilidad.

| ID | Atributo | Escenario y medida de respuesta | Mecanismo y validación |
|---|---|---|---|
| AC-01 | Rendimiento | Una solicitud llega a conductores cercanos en menos de 3 s. | Consultas acotadas y avisos; medir desde aceptación por backend hasta recepción en dispositivos, con redes representativas. |
| AC-02 | Tiempo real | Durante el viaje, actualizar ubicación cada 3–5 s. | Suscripciones limitadas al viaje; medir intervalo y antigüedad, mostrando aviso si la ubicación está desactualizada. |
| AC-03 | Disponibilidad | Disponibilidad mensual objetivo de 99.5 %. | Supervisar flujos críticos y dependencias; medir fallos e indisponibilidad con criterio acordado. |
| AC-04 | Escalabilidad | Hasta 2,000 conductores y 300 viajes simultáneos como capacidad inicial objetivo. | Índices, posición actual separada del recorrido y listeners acotados; carga progresiva y medición de costos. |
| AC-05 | Continuidad | Un corte breve no pierde ni duplica viaje, asignación o descuento. | Estado autoritativo, reconciliación e idempotencia; cortar red antes y después de confirmar operaciones. |
| AC-06 | Seguridad | Identidad y rol limitan cada recurso; TLS 1.2 o superior y documentos privados. | Reglas y validación backend; intentar leer viajes ajenos, aprobar recargas propias y modificar saldo desde cliente. |
| AC-07 | Usabilidad y accesibilidad | Solicitud en tres toques o menos desde pantalla principal, botones de al menos 48 dp y contraste AA. | Ensayos de tareas y revisión de interfaz; definir precondiciones de origen/destino para contar los toques. |
| AC-08 | Compatibilidad | Android 8.0 o superior; apertura menor de 4 s en Android 9 con 2 GB de RAM. | Probar dispositivos de gama baja, inicio y consumo de memoria. |
| AC-09 | Mantenibilidad | Cambiar mapas o persistencia sin rehacer pantallas. | Puertos, adaptadores y repositorios; sustituir implementaciones en pruebas de contratos. |
| AC-10 | Respaldo y trazabilidad | Copias diarias, retención de 30 días, restauración mensual y auditoría sensible. | Simular restauración y comprobar integridad de viajes, movimientos, actor y cambios. |

## Escenarios críticos

**Concurrencia:** dos pasajeros intentan asignar al mismo conductor, o un pasajero selecciona dos ofertas. La transacción debe dejar una sola asignación compatible y un viaje activo por conductor.

**Integridad financiera:** varios reintentos de finalización o aprobación de recarga deben conservar un único movimiento por origen. La consulta de saldo debe concordar con el libro de movimientos.

**Emergencia:** un SOS se registra antes de enviar avisos externos. Deben distinguirse alerta creada, aviso enviado, atención asignada y cierre humano. Sin red, mostrar la limitación y acceso a llamadas.

## Carga y consumo

Con 300 viajes y una posición cada cinco segundos se generan aproximadamente 60 escrituras de posición por segundo; a tres segundos, 100. Son volúmenes teóricos y excluyen lecturas, recorrido, chat y avisos. Medirlos en pruebas antes de afirmar que la capacidad está alcanzada.

Métricas: latencia de solicitudes, errores, antigüedad GPS, conflictos de asignación, referencias duplicadas rechazadas, recargas pendientes y SOS abiertos. Las tasas de entrega push dependen también del dispositivo y la red.

**Fuente:** ENTREGABLE-02_MotoYa.pdf, tabla 4, decisiones y riesgos y plan de validación.

[← Requisitos](03-requisitos-funcionales.md) · [Restricciones →](05-restricciones.md)
