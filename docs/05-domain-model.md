# AstroBooking - Domain Model

| Documento | Domain Model |
|------------|--------------|
| Proyecto | AstroBooking |
| Versión | 1.0.0 |
| Estado | Draft |
| Autor | Carla Tatiana Valderrama Garzón |
| Fecha | 28/06/2026 |

---

# Tabla de contenido

1. Introducción
2. Objetivos
3. Entidades del dominio
4. Relaciones
5. Reglas de negocio
6. Definition of Done

---

# 1. Introducción

Este documento describe el modelo de dominio del MVP de AstroBooking.

El modelo de dominio representa los principales conceptos del negocio y las relaciones entre ellos, independientemente de su implementación técnica.

Servirá como base para el diseño de la base de datos, la arquitectura del sistema y la implementación de las entidades del dominio.

---

# 2. Objetivos

Los objetivos del modelo de dominio son:

- Identificar las entidades principales del negocio.
- Definir las relaciones entre las entidades.
- Establecer las reglas de negocio del dominio.
- Servir como base para el diseño de la arquitectura y la persistencia.

## User

Representa cualquier usuario registrado en AstroBooking.

### Responsabilidades

- Autenticarse.
- Administrar su información personal.
- Gestionar su cuenta.

### Atributos principales

- id
- firstName
- lastName
- email
- password
- role
- status
- createdAt
- updatedAt

## ProfessionalProfile

Representa el perfil público de un profesional.

### Responsabilidades

- Mostrar información pública.
- Publicar servicios.
- Configurar información profesional.

### Atributos principales

- id
- biography
- profileImage
- contactInformation
- isPublished

## Service

Representa un servicio ofrecido por un profesional.

### Responsabilidades

- Definir el servicio ofrecido.
- Establecer precio y duración.
- Permitir su publicación.

### Atributos principales

- id
- name
- description
- duration
- price
- status

## Availability

Representa la disponibilidad configurada por un profesional para ofrecer sus servicios.

### Responsabilidades

- Definir los horarios de atención.
- Gestionar los días disponibles.
- Bloquear fechas específicas.
- Controlar la disponibilidad para nuevas reservas.

### Atributos principales

- id
- professionalProfileId
- dayOfWeek
- startTime
- endTime
- isAvailable

## Booking

Representa una reserva realizada por un cliente para un servicio específico.

### Responsabilidades

- Registrar una reserva.
- Gestionar su estado.
- Permitir cancelaciones y reprogramaciones.

### Atributos principales

- id
- clientId
- professionalProfileId
- serviceId
- bookingDate
- startTime
- endTime
- status
- createdAt

## Payment

Representa el pago asociado a una reserva.

### Responsabilidades

- Registrar transacciones.
- Asociar pagos a reservas.
- Gestionar el estado del pago.

### Atributos principales

- id
- bookingId
- amount
- paymentMethod
- paymentStatus
- transactionDate

## Notification

Representa una notificación enviada por el sistema a un usuario.

### Responsabilidades

- Informar eventos importantes.
- Enviar recordatorios.
- Confirmar operaciones realizadas.

### Atributos principales

- id
- userId
- type
- title
- message
- status
- sentAt

# 4. Relaciones

| Entidad | Relación | Entidad |
|----------|----------|----------|
| User | 1 : 1 | ProfessionalProfile |
| ProfessionalProfile | 1 : N | Service |
| ProfessionalProfile | 1 : N | Availability |
| ProfessionalProfile | 1 : N | Booking |
| User (Cliente) | 1 : N | Booking |
| Service | 1 : N | Booking |
| Booking | 1 : 1 | Payment |
| User | 1 : N | Notification |

# 5. Reglas de negocio

| ID | Regla |
|----|--------|
| BR-01 | Un correo electrónico solo puede estar asociado a un usuario. |
| BR-02 | Un profesional debe tener un perfil publicado para aceptar reservas. |
| BR-03 | Un cliente solo puede reservar horarios disponibles. |
| BR-04 | Una reserva no puede existir sin un servicio asociado. |
| BR-05 | Una reserva solo puede tener un pago asociado en el MVP. |
| BR-06 | Una reserva cancelada libera automáticamente el horario correspondiente. |
| BR-07 | Solo los usuarios autenticados pueden gestionar reservas. |
| BR-08 | Un profesional solo puede administrar sus propios servicios y disponibilidad. |

# 6. Definition of Done

Este documento se considera terminado cuando se cumplan los siguientes criterios:

- [x] Se identificaron las entidades principales del dominio.
- [x] Se definieron las responsabilidades de cada entidad.
- [x] Se documentaron los atributos principales.
- [x] Se establecieron las relaciones entre entidades.
- [x] Se documentaron las reglas de negocio del MVP.
- [x] El documento cumple con el estándar de documentación del proyecto.
- [x] El documento está versionado en Git.
- [x] El documento está asociado a la tarea ASTRO-1.5 en ClickUp.