# 05. Restricciones del sistema

Una restricción limita las opciones de diseño; un atributo de calidad expresa un comportamiento que debe medirse.

| ID | Tipo | Restricción del PDF | Consecuencia arquitectónica |
|---|---|---|---|
| R-01 | Plataforma | Primera versión Android 8.0 o superior; iOS posterior. | Priorizar Android y aislar dependencias del dispositivo. |
| R-02 | Geografía | Operación inicial en cinco distritos definidos de Huamanga. | Cobertura configurable, validada en servidor; el PDF no enumera esos distritos. |
| R-03 | Negocio | Pasajero paga directamente al conductor fuera de la aplicación. | Sin pasarela del pago del viaje ni almacenamiento de tarjetas en el MVP. |
| R-04 | Saldo | Comisión del saldo prepagado; recargas revisadas por soporte. | Libro de movimientos, referencia única y confirmación humana del abono. |
| R-05 | Tecnología | Flutter, Firebase y Google Maps Platform. | Flutter móvil y Web, Riverpod, Auth, Functions, Firestore, Storage y FCM; proveedores detrás de interfaces. |
| R-06 | Conectividad | Datos móviles variables y equipos de recursos limitados. | Reconciliar estado al reconectar y distinguir pendiente de confirmado. |
| R-07 | Operación | Conductores requieren aprobación; personal actúa dentro de permisos. | Autorización efectiva en servidor, por rol y recurso. |
| R-08 | Alcance | Sin encomiendas, mototaxis de tres ruedas, otras ciudades ni pagos integrados. | Concentrar MVP en viajes de moto lineal y soporte. |
| R-09 | Información | Documentos privados y retención diferenciada. | Separar datos, acceso temporal autorizado y depuración programada. |

## Retención y operación

| Categoría | Retención del PDF |
|---|---|
| Chat | 90 días |
| Historial de recorrido | 12 meses |
| Auditoría | Dos años |
| Copias de seguridad | 30 días, con copias diarias |

La posición actual y el historial de recorrido cumplen propósitos distintos. Eliminar posiciones históricas no elimina el costo ya generado por escrituras o lecturas. La política de eliminación de cuentas debe respetar finalidad y retención.

Pruebas y producción deben usar proyectos Firebase independientes. Las cuentas del panel son diferenciadas, con segundo factor y cierre por inactividad. Las credenciales del servidor permanecen fuera del cliente.

## Límites de la propuesta

GraphHopper y Photon aparecen como adaptadores alternativos en infraestructura propia, sujetos a evaluación; no están desplegados. La confirmación automatizada de recargas mediante una pasarela no sustituye la revisión humana prevista en esta entrega.

**Fuente:** ENTREGABLE-02_MotoYa.pdf, tabla 5, seguridad y despliegue.

[← Calidad](04-atributos-de-calidad.md) · [Drivers →](06-driver-arquitectonicos.md)
