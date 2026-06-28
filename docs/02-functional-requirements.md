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

| ID | Requerimiento |
|----|---------------|
| FR-02.1 | El sistema deberá permitir a un usuario autenticarse mediante correo electrónico y contraseña. |
| FR-02.2 | El sistema deberá validar las credenciales antes de conceder acceso al sistema. |
| FR-02.3 | El sistema deberá impedir el acceso cuando las credenciales sean inválidas. |
| FR-02.4 | El sistema deberá permitir cerrar la sesión del usuario autenticado. |
| FR-02.5 | El sistema deberá permitir solicitar la recuperación de contraseña mediante correo electrónico. |
| FR-02.6 | El sistema deberá permitir establecer una nueva contraseña utilizando un enlace de recuperación válido. |
| FR-02.7 | El sistema deberá restringir el acceso a las funcionalidades según el rol del usuario. |
| FR-02.8 | El sistema deberá mantener la sesión autenticada hasta su expiración o cierre manual. |
| FR-02.9 | El sistema deberá registrar los intentos fallidos de autenticación para fines de auditoría y seguridad. |