# 06. Drivers arquitectónicos

Se mantienen DA-01 a DA-08 del PDF. Los identificadores AC corresponden a la tabla de calidad de este repositorio.

| ID | Driver | Origen trazable | Prioridad | Respuesta arquitectónica | Compromiso y validación |
|---|---|---|---|---|---|
| DA-01 | Consistencia del viaje | RF-06, RF-07, RF-10; HU-05, HU-08; AC-05 | Alta | Functions y transacciones para una asignación compatible, estados válidos y una comisión por viaje. | Requiere servidor; probar carreras y reintentos. |
| DA-02 | Coordinación en tiempo real | RF-04, RF-05, RF-07; AC-01, AC-02 | Alta | Firestore, suscripciones acotadas y FCM; versiones y vencimientos decididos en servidor. | Push no confirma una asignación; medir recepción y antigüedad GPS. |
| DA-03 | Privacidad y permisos | RF-02, RF-09, RF-13; AC-06; R-07, R-09 | Alta | Auth, autorización por recurso, documentos privados, roles y auditoría. | Functions debe verificar permisos explícitamente; probar cuentas adversarias. |
| DA-04 | Integridad financiera | RF-10, RF-11; HU-08, HU-09; R-03, R-04 | Alta | Libro de movimientos, céntimos, referencia externa única e idempotencia. Pago del viaje externo. | Comprobar abono real y conciliación; captura no basta. |
| DA-05 | Continuidad con red variable | AC-05, AC-08; R-01, R-06 | Alta | Recuperar viaje al reconectar; confirmar acciones críticas solo con servidor. | Mostrar pendientes; probar respuesta perdida tras commit. |
| DA-06 | Evolución de proveedores | AC-09; R-05 | Media | Capas, repositorios, puertos y adaptadores para mapas, persistencia y avisos. | Añade contratos; probar sustitución sin modificar pantallas. |
| DA-07 | Crecimiento y consumo | AC-03, AC-04, AC-02 | Media | Separar posición y recorrido, limitar listeners, indexar consultas y medir carga/costos. | Frecuencia GPS incrementa escrituras y lecturas; carga progresiva. |
| DA-08 | Operación de soporte | RF-02, RF-09, RF-11, RF-13; HU-10 | Alta | Panel web, colas de revisión, alertas asignables y registros de atención. | Envío automático no asegura atención humana; ensayar protocolo SOS. |

## Decisión integradora

Cliente-servidor con Backend como Servicio y funciones serverless, organizado en capas y módulos por capacidad. Las reglas sensibles se ejecutan en Cloud Functions; la app y el panel coordinan interacción, sin autoridad sobre saldo, aprobación o asignación.

No se exige un microservicio independiente por función del MVP. Una capa lógica tampoco equivale a un servidor independiente.

**Fuente:** ENTREGABLE-02_MotoYa.pdf, tabla 6 y estilo arquitectónico seleccionado.

[← Restricciones](05-restricciones.md) · [Arquitectura →](../arquitectura/arquitectura-inicial.md)
