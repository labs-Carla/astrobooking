# AstroBooking - Business Workflows

| Documento | Business Workflows              |
| --------- | ------------------------------- |
| Proyecto  | AstroBooking                    |
| Versión   | 1.0.0                           |
| Estado    | Draft                           |
| Autor     | Carla Tatiana Valderrama Garzón |
| Fecha     | 28/06/2026                      |

---

# Tabla de contenido

1. Introducción
2. Objetivos
3. Actores
4. Convenciones
5. Workflows
6. Decisiones de diseño
7. Definition of Done

---

# 1. Introducción

Este documento describe los principales flujos de negocio del MVP de AstroBooking.

Cada workflow representa una secuencia de actividades ejecutadas por los usuarios y el sistema para completar un proceso de negocio.

Estos flujos servirán como base para la definición de casos de uso, servicios de aplicación, endpoints REST e implementación del backend.

---

# 2. Objetivos

* Documentar el comportamiento del negocio.
* Definir la interacción entre usuarios y sistema.
* Identificar los eventos principales del dominio.
* Servir como base para los casos de uso.
* Mantener la trazabilidad entre requerimientos e implementación.

---

# 3. Actores

| Actor            | Descripción                                            |
| ---------------- | ------------------------------------------------------ |
| Visitante        | Usuario que aún no ha iniciado sesión.                 |
| Cliente          | Usuario que agenda y compra servicios.                 |
| Profesional      | Usuario que ofrece servicios mediante la plataforma.   |
| Sistema          | Plataforma AstroBooking.                               |
| Pasarela de Pago | Servicio externo encargado del procesamiento de pagos. |

---

# 4. Convenciones

Cada workflow incluirá la siguiente información:

* Objetivo
* Actores involucrados
* Precondiciones
* Flujo principal
* Flujos alternativos
* Resultado esperado
* User Stories relacionadas

---

# 5. Workflows

Se documentarán los siguientes procesos del negocio:

* WF-001 Registro de usuario
* WF-002 Inicio de sesión
* WF-003 Recuperación de contraseña
* WF-004 Crear reserva (Consulta en vivo)
* WF-005 Comprar informe PDF
* WF-006 Procesar pago
* WF-007 Confirmar reserva
* WF-008 Cancelar reserva
* WF-009 Reprogramar reserva
* WF-010 Enviar recordatorios automáticos
* WF-011 Entregar informe PDF

Cada workflow será documentado en detalle en las siguientes secciones del documento.

---

# 6. Decisiones de diseño

Durante el análisis del dominio se definieron las siguientes decisiones:

* Una reserva puede representar una consulta en vivo o la solicitud de un informe PDF.
* Los pagos siempre estarán asociados a una reserva.
* Las notificaciones serán generadas como consecuencia de eventos del dominio.
* Booking almacenará un snapshot del servicio para preservar el historial.
* El comportamiento del sistema será modelado mediante workflows antes de definir los casos de uso.

---

# 7. Definition of Done

Este documento se considera terminado cuando:

* [x] Los workflows principales fueron identificados.
* [x] Los actores fueron definidos.
* [x] Las decisiones de negocio fueron documentadas.
* [x] Existe trazabilidad con los requerimientos funcionales y las historias de usuario.
* [x] El documento sigue el estándar de documentación del proyecto.
* [x] Está versionado en Git.
* [x] Está asociado a la tarea ASTRO-1.8.
