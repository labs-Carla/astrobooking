# AstroBooking - Functional Requirements

| Documento | Functional Requirements |
|------------|-------------------------|
| Proyecto | AstroBooking |
| Versión | 1.0.0 |
| Estado | Draft |
| Autor | Carla Tatiana Valderrama Garzón |
| Fecha | 28/06/2026 |

---
# Tabla de contenido

1. Introducción
2. Convenciones
3. Actores
4. FR-01 Gestión de usuarios
5. FR-02 Autenticación
6. FR-03 Perfil profesional
7. FR-04 Servicios
8. FR-05 Disponibilidad
9. FR-06 Reservas
10. FR-07 Pagos
11. FR-08 Notificaciones
12. FR-09 Panel profesional
13. FR-10 Panel cliente

---

# 1. Introducción

Este documento describe los requerimientos funcionales del MVP de AstroBooking.

Los requerimientos funcionales especifican el comportamiento esperado del sistema desde la perspectiva del negocio y constituyen la base para el diseño del modelo de dominio, la arquitectura del software, la implementación y las pruebas.

Todos los requerimientos definidos en este documento corresponden al alcance establecido para el MVP del proyecto.

---

# 2. Convenciones

Para la identificación de los requerimientos funcionales se utilizará la siguiente nomenclatura:

- **FR**: Functional Requirement.
- **FR-XX**: Identificador único del módulo funcional.
- **FR-XX.X**: Requerimiento específico dentro del módulo.

Ejemplo:

- FR-01 Gestión de usuarios
- FR-01.1 Registrar usuario
- FR-01.2 Actualizar información del usuario

---

# 3. Actores

Los actores que interactúan con el sistema son:

| Actor | Descripción |
|--------|-------------|
| Visitante | Usuario que aún no ha iniciado sesión. |
| Cliente | Usuario que agenda servicios ofrecidos por un profesional. |
| Profesional | Usuario que ofrece servicios mediante la plataforma. |
| Administrador | Usuario responsable de la administración del sistema. |

---

# 4. FR-01 Gestión de usuarios

## Descripción

Este módulo define las funcionalidades relacionadas con la administración de los usuarios de la plataforma, incluyendo su registro, consulta, actualización y desactivación de la cuenta.

### Requerimientos

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-01.1 | El sistema deberá permitir el registro de nuevos usuarios. | Alta |
| FR-01.2 | El sistema deberá permitir registrar usuarios con el rol de Profesional o Cliente. | Alta |
| FR-01.3 | El sistema deberá validar que el correo electrónico sea único dentro del sistema. | Alta |
| FR-01.4 | El sistema deberá permitir consultar la información del perfil del usuario autenticado. | Alta |
| FR-01.5 | El sistema deberá permitir actualizar la información personal del usuario. | Alta |
| FR-01.6 | El sistema deberá permitir cambiar la contraseña del usuario autenticado. | Alta |
| FR-01.7 | El sistema deberá permitir desactivar una cuenta sin eliminar su información histórica. | Media |
| FR-01.8 | El sistema deberá registrar la fecha de creación y la fecha de última actualización de cada usuario. | Media |

# 5. FR-02 Autenticación

## Descripción

Este módulo define las funcionalidades relacionadas con la autenticación, autorización y gestión de sesiones de los usuarios de AstroBooking.

Su objetivo es garantizar que únicamente usuarios válidos puedan acceder a las funcionalidades correspondientes a su rol dentro de la plataforma.

### Requerimientos

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-02.1 | El sistema deberá permitir a un usuario autenticarse mediante correo electrónico y contraseña. | Alta |
| FR-02.2 | El sistema deberá validar las credenciales antes de conceder acceso al sistema. | Alta |
| FR-02.3 | El sistema deberá impedir el acceso cuando las credenciales sean inválidas. | Alta |
| FR-02.4 | El sistema deberá permitir cerrar la sesión del usuario autenticado. | Media |
| FR-02.5 | El sistema deberá permitir solicitar la recuperación de contraseña mediante correo electrónico. | Alta |
| FR-02.6 | El sistema deberá permitir establecer una nueva contraseña utilizando un enlace de recuperación válido. | Alta |
| FR-02.7 | El sistema deberá restringir el acceso a las funcionalidades según el rol del usuario. | Alta |
| FR-02.8 | El sistema deberá mantener la sesión autenticada hasta su expiración o cierre manual. | Media |
| FR-02.9 | El sistema deberá registrar los intentos fallidos de autenticación para fines de auditoría y seguridad. | Baja |

# 6. FR-03 Perfil profesional

## Descripción

Este módulo define las funcionalidades relacionadas con la administración del perfil público del profesional, incluyendo la información que será visible para los clientes al momento de consultar sus servicios.

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-03.1 | El sistema deberá permitir al profesional crear su perfil profesional. | Alta |
| FR-03.2 | El sistema deberá permitir actualizar la información del perfil profesional. | Alta |
| FR-03.3 | El sistema deberá permitir registrar una fotografía de perfil. | Media |
| FR-03.4 | El sistema deberá permitir registrar una biografía profesional. | Alta |
| FR-03.5 | El sistema deberá permitir configurar los datos de contacto visibles para los clientes. | Media |
| FR-03.6 | El sistema deberá permitir publicar o despublicar el perfil profesional. | Alta |
| FR-03.7 | El sistema deberá permitir visualizar el perfil público del profesional. | Alta |

# 7. FR-04 Servicios

## Descripción

Este módulo permite al profesional administrar los servicios que ofrece dentro de la plataforma.

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-04.1 | El sistema deberá permitir crear un servicio. | Alta |
| FR-04.2 | El sistema deberá permitir editar un servicio existente. | Alta |
| FR-04.3 | El sistema deberá permitir eliminar o desactivar un servicio. | Media |
| FR-04.4 | El sistema deberá permitir definir el nombre del servicio. | Alta |
| FR-04.5 | El sistema deberá permitir definir la descripción del servicio. | Alta |
| FR-04.6 | El sistema deberá permitir establecer la duración del servicio. | Alta |
| FR-04.7 | El sistema deberá permitir establecer el precio del servicio. | Alta |
| FR-04.8 | El sistema deberá permitir consultar el listado de servicios disponibles. | Alta |

# 8. FR-05 Disponibilidad

## Descripción

Este módulo administra la disponibilidad del profesional para permitir la reserva de citas.

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-05.1 | El sistema deberá permitir configurar horarios de atención. | Alta |
| FR-05.2 | El sistema deberá permitir definir días laborables. | Alta |
| FR-05.3 | El sistema deberá permitir bloquear fechas específicas. | Media |
| FR-05.4 | El sistema deberá impedir reservas fuera del horario disponible. | Alta |
| FR-05.5 | El sistema deberá actualizar automáticamente la disponibilidad cuando una cita sea reservada. | Alta |
| FR-05.6 | El sistema deberá permitir modificar la disponibilidad existente. | Alta |

# 9. FR-06 Reservas

## Descripción

Este módulo define las funcionalidades relacionadas con la creación, gestión y seguimiento de las reservas realizadas por los clientes.

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-06.1 | El sistema deberá permitir a un cliente reservar un servicio disponible. | Alta |
| FR-06.2 | El sistema deberá validar la disponibilidad antes de confirmar una reserva. | Alta |
| FR-06.3 | El sistema deberá impedir reservas en horarios ocupados o bloqueados. | Alta |
| FR-06.4 | El sistema deberá generar una confirmación de la reserva. | Alta |
| FR-06.5 | El sistema deberá permitir al cliente cancelar una reserva según las políticas establecidas. | Alta |
| FR-06.6 | El sistema deberá permitir al profesional cancelar una reserva. | Alta |
| FR-06.7 | El sistema deberá permitir reprogramar una reserva manteniendo la disponibilidad del profesional. | Alta |
| FR-06.8 | El sistema deberá registrar el estado de cada reserva (Pendiente, Confirmada, Cancelada, Completada). | Alta |
| FR-06.9 | El sistema deberá permitir consultar el historial de reservas de un usuario. | Media |

# 10. FR-07 Pagos

## Descripción

Este módulo administra el procesamiento y registro de los pagos asociados a las reservas realizadas dentro de la plataforma.

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-07.1 | El sistema deberá permitir registrar el pago de una reserva. | Alta |
| FR-07.2 | El sistema deberá asociar cada pago a una reserva. | Alta |
| FR-07.3 | El sistema deberá registrar el estado del pago (Pendiente, Pagado, Reembolsado, Fallido). | Alta |
| FR-07.4 | El sistema deberá permitir consultar el historial de pagos. | Media |
| FR-07.5 | El sistema deberá permitir registrar la fecha y el método de pago utilizado. | Media |
| FR-07.6 | El sistema deberá impedir confirmar una reserva que requiera pago cuando la transacción no haya sido completada. | Alta |

# 11. FR-08 Notificaciones

## Descripción

Este módulo gestiona el envío de notificaciones automáticas relacionadas con las reservas y la actividad de los usuarios.

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-08.1 | El sistema deberá enviar una notificación cuando una reserva sea creada. | Alta |
| FR-08.2 | El sistema deberá enviar una notificación cuando una reserva sea cancelada. | Alta |
| FR-08.3 | El sistema deberá enviar recordatorios antes de la fecha de la reserva. | Alta |
| FR-08.4 | El sistema deberá notificar cambios en el estado de una reserva. | Media |
| FR-08.5 | El sistema deberá permitir al usuario configurar sus preferencias de notificación. | Baja |

# 12. FR-09 Panel profesional

## Descripción

Este módulo proporciona al profesional una vista centralizada para administrar su actividad dentro de AstroBooking.

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-09.1 | El sistema deberá mostrar al profesional un panel con un resumen de su actividad. | Alta |
| FR-09.2 | El sistema deberá mostrar las próximas reservas programadas. | Alta |
| FR-09.3 | El sistema deberá permitir consultar el historial de reservas. | Media |
| FR-09.4 | El sistema deberá mostrar el estado de los pagos asociados a las reservas. | Media |
| FR-09.5 | El sistema deberá permitir acceder a la gestión de servicios, disponibilidad y perfil desde un único panel. | Alta |
| FR-09.6 | El sistema deberá mostrar indicadores básicos del negocio, como número de reservas e ingresos generados. | Baja |

# 13. FR-10 Panel cliente

## Descripción

Este módulo proporciona al cliente un espacio donde puede gestionar sus reservas y consultar la información relacionada con los servicios contratados.

### Requerimientos

| ID | Requerimiento | Prioridad |
|----|---------------|-----------|
| FR-10.1 | El sistema deberá mostrar al cliente sus próximas reservas. | Alta |
| FR-10.2 | El sistema deberá permitir consultar el historial de reservas. | Media |
| FR-10.3 | El sistema deberá permitir cancelar una reserva según las políticas establecidas. | Alta |
| FR-10.4 | El sistema deberá permitir reprogramar una reserva cuando exista disponibilidad. | Alta |
| FR-10.5 | El sistema deberá permitir consultar el estado de los pagos asociados a sus reservas. | Media |
| FR-10.6 | El sistema deberá permitir actualizar la información básica de su perfil. | Media |

---

# 14. Trazabilidad

La siguiente tabla muestra la relación entre los módulos funcionales definidos en este documento y los EPICs del backlog del proyecto.

| Módulo | EPIC |
|--------|------|
| FR-01 Gestión de usuarios | EPIC-02 Identity & Access |
| FR-02 Autenticación | EPIC-02 Identity & Access |
| FR-03 Perfil profesional | EPIC-03 Professional Profile |
| FR-04 Servicios | EPIC-03 Professional Profile |
| FR-05 Disponibilidad | EPIC-04 Availability |
| FR-06 Reservas | EPIC-05 Booking |
| FR-07 Pagos | EPIC-06 Payments |
| FR-08 Notificaciones | EPIC-07 Notifications |
| FR-09 Panel profesional | EPIC-09 Professional Dashboard |
| FR-10 Panel cliente | EPIC-08 Customer Portal |