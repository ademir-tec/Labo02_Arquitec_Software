# MotoYa: análisis del caso y arquitectura de software

**Autor:** Alvaro Ademir Ayala Arango  
**Universidad:** Universidad Nacional de San Cristóbal de Huamanga  
**Escuela Profesional:** Ingeniería de Sistemas  
**Curso:** Arquitectura de Software  
**Docente:** Ing. Lizbeth Jaico Quispe  
**Entrega:** Entregable 02, 1 de octubre de 2026

## Descripción y problemática

MotoYa es una plataforma de transporte en moto lineal para Huamanga, Ayacucho. Conecta pasajeros con conductores verificados, permite negociar el precio antes del servicio y registra su desarrollo. La solución comprende una app Flutter con modos pasajero y conductor y un panel Flutter Web para soporte y administración.

La búsqueda presencial y negociación informal generan incertidumbre sobre disponibilidad, precio e identidad. La ausencia de registros dificulta atender incidentes y construir reputación. MotoYa propone solicitudes a conductores cercanos, aprobación documental, PIN de inicio, seguimiento, calificaciones y SOS.

El pasajero paga directamente al conductor fuera de la aplicación. MotoYa descuenta una comisión del saldo que el conductor recarga por adelantado; soporte comprueba el abono real antes de acreditar.

**Flujo principal:** verificar cuenta, solicitar ruta y precio, negociar, seleccionar conductor, validar llegada, iniciar con PIN, realizar viaje, finalizar y registrar comisión.

## Alcance de la entrega

Este repositorio contiene análisis y diseño académico basado en `ENTREGABLE-02_MotoYa.pdf`. No contiene todavía una app ejecutable ni un backend desplegado. Se sigue la organización del [repositorio de referencia](https://github.com/ademir-tec/Marketplace-arquitSoft-02-alvaro), adaptando el contenido al negocio de MotoYa.

Primera versión Android 8.0 o superior, cobertura inicial en cinco distritos de Huamanga y stack Flutter, Firebase y Google Maps Platform. No se incluyen encomiendas, mototaxis de tres ruedas, otras ciudades ni pagos integrados.

## Documentos

| Parte | Archivo |
|---|---|
| Actores y permisos | [01. Actores](analisis-de-sistema/01-actores.md) |
| Necesidades y criterios de aceptación | [02. Historias de usuario](analisis-de-sistema/02-historias-del-usuario.md) |
| Funciones, prioridades y reglas del negocio | [03. Requisitos funcionales](analisis-de-sistema/03-requisitos-funcionales.md) |
| Escenarios medibles y pruebas | [04. Atributos de calidad](analisis-de-sistema/04-atributos-de-calidad.md) |
| Límites de la primera versión | [05. Restricciones](analisis-de-sistema/05-restricciones.md) |
| Necesidades que condicionan el diseño | [06. Drivers arquitectónicos](analisis-de-sistema/06-driver-arquitectonicos.md) |
| Capas, componentes, datos, flujos y validación | [Arquitectura inicial](arquitectura/arquitectura-inicial.md) |
| Vista gráfica | [Diagrama SVG](arquitectura/motoya-arquitectura.svg) |

## Arquitectura seleccionada

Cliente-servidor con Backend como Servicio y funciones serverless. Cloud Functions mantiene autoridad sobre asignación, estados, aprobaciones y dinero. Firestore conserva datos, Auth verifica identidad, Storage protege documentos y FCM/proveedor SMS envían avisos.

Dentro de la solución se separan presentación, aplicación, dominio, acceso a datos e infraestructura. Riverpod organiza el estado del cliente; repositorios y adaptadores aíslan proveedores. Las capas son lógicas y no requieren cinco servidores ni microservicios independientes por capacidad.

![Vista general de MotoYa](arquitectura/motoya-arquitectura.svg)

## Cómo revisar

Leer los seis documentos de análisis en orden y luego la arquitectura. GitHub visualiza las tablas, el SVG y los bloques Mermaid. Los identificadores HU, RF, R y DA conservan los del PDF; AC identifica los escenarios de calidad del repositorio.

Las metas de latencia, disponibilidad y carga son objetivos pendientes de pruebas. Las decisiones adicionales de implementación se señalan como propuestas. El PDF no enumera los cinco distritos ni fija todos los parámetros de negociación; esos puntos se conservan como pendientes.

## Fuente

`ENTREGABLE-02_MotoYa.pdf`, «Análisis de caso y arquitectura», proporcionado para esta entrega. El documento fuente determina actores, reglas, restricciones y stack; el marketplace se utiliza como referencia de estructura.
