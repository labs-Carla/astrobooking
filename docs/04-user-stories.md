# AstroBooking - User Stories

| Documento | User Stories |
|------------|--------------|
| Proyecto | AstroBooking |
| Versión | 1.0.0 |
| Estado | Draft |
| Autor | Carla Tatiana Valderrama Garzón |
| Fecha | 28/06/2026 |

---

# Tabla de contenido

1. Introducción
2. Convenciones
3. Historias de usuario
4. Definition of Done

---

# 1. Introducción

Este documento contiene las historias de usuario correspondientes al MVP de AstroBooking.

Cada historia describe una necesidad del usuario desde la perspectiva del negocio y servirá como base para el desarrollo, las pruebas y la validación funcional del sistema.

---

# 2. Convenciones

Cada historia de usuario utilizará la siguiente estructura:

- Identificador
- EPIC asociado
- Prioridad
- Historia de usuario
- Criterios de aceptación

## US-2.1 Registro de usuario

| Campo | Valor |
|--------|-------|
| ID | US-2.1 |
| EPIC | EPIC-02 Identity & Access |
| Prioridad | Alta |
| Requerimientos relacionados | FR-01.1, FR-01.2, FR-01.3 |

### Historia

**Como** visitante

**Quiero** registrarme en AstroBooking utilizando mi correo electrónico y una contraseña

**Para** acceder a la plataforma y gestionar reservas como cliente o profesional.

### Criterios de aceptación

#### Escenario 1: Registro exitoso

**Given** que soy un visitante sin una cuenta registrada

**When** completo correctamente el formulario de registro

**Then** el sistema crea una nueva cuenta y confirma el registro.

#### Escenario 2: Correo electrónico existente

**Given** que el correo electrónico ya pertenece a un usuario registrado

**When** intento crear una nueva cuenta utilizando ese mismo correo

**Then** el sistema rechaza el registro e informa que el correo ya está en uso.

## US-2.2 Inicio de sesión

| Campo | Valor |
|--------|-------|
| ID | US-2.2 |
| EPIC | EPIC-02 Identity & Access |
| Prioridad | Alta |
| Requerimientos relacionados | FR-02.1, FR-02.2, FR-02.3 |

### Historia

**Como** usuario registrado

**Quiero** iniciar sesión utilizando mis credenciales

**Para** acceder de forma segura a las funcionalidades de la plataforma.

### Criterios de aceptación

#### Escenario 1: Inicio de sesión exitoso

**Given** que poseo una cuenta válida

**When** ingreso correctamente mi correo electrónico y contraseña

**Then** el sistema autentica mi identidad y concede acceso a la plataforma.

#### Escenario 2: Credenciales inválidas

**Given** que ingreso credenciales incorrectas

**When** intento iniciar sesión

**Then** el sistema deniega el acceso e informa que las credenciales son inválidas.

## US-2.3 Recuperar contraseña

| Campo | Valor |
|--------|-------|
| ID | US-2.3 |
| EPIC | EPIC-02 Identity & Access |
| Prioridad | Alta |
| Requerimientos relacionados | FR-02.5, FR-02.6 |

### Historia

**Como** usuario registrado

**Quiero** recuperar mi contraseña

**Para** restablecer el acceso a mi cuenta cuando la haya olvidado.

### Criterios de aceptación

#### Escenario 1: Solicitud de recuperación

**Given** que poseo una cuenta registrada

**When** solicito recuperar mi contraseña

**Then** el sistema envía un enlace de recuperación al correo electrónico asociado a mi cuenta.

#### Escenario 2: Restablecimiento de contraseña

**Given** que accedo mediante un enlace de recuperación válido

**When** establezco una nueva contraseña

**Then** el sistema actualiza la contraseña y permite iniciar sesión con la nueva credencial.

## US-2.4 Cerrar sesión

| Campo | Valor |
|--------|-------|
| ID | US-2.4 |
| EPIC | EPIC-02 Identity & Access |
| Prioridad | Media |
| Requerimientos relacionados | FR-02.4 |

### Historia

**Como** usuario autenticado

**Quiero** cerrar mi sesión

**Para** finalizar de forma segura mi acceso a la plataforma.

### Criterios de aceptación

#### Escenario 1: Cierre de sesión exitoso

**Given** que tengo una sesión activa

**When** selecciono la opción "Cerrar sesión"

**Then** el sistema finaliza mi sesión y redirige a la pantalla de inicio.

## US-2.5 Actualizar perfil

| Campo | Valor |
|--------|-------|
| ID | US-2.5 |
| EPIC | EPIC-02 Identity & Access |
| Prioridad | Alta |
| Requerimientos relacionados | FR-01.4, FR-01.5 |

### Historia

**Como** usuario autenticado

**Quiero** actualizar mi información personal

**Para** mantener mis datos actualizados.

### Criterios de aceptación

#### Escenario 1: Actualización exitosa

**Given** que he iniciado sesión

**When** modifico mi información personal con datos válidos

**Then** el sistema guarda los cambios y confirma la actualización.

## US-2.6 Cambiar contraseña

| Campo | Valor |
|--------|-------|
| ID | US-2.6 |
| EPIC | EPIC-02 Identity & Access |
| Prioridad | Alta |
| Requerimientos relacionados | FR-01.6 |

### Historia

**Como** usuario autenticado

**Quiero** cambiar mi contraseña

**Para** mantener la seguridad de mi cuenta.

### Criterios de aceptación

#### Escenario 1: Cambio exitoso

**Given** que he iniciado sesión

**When** ingreso mi contraseña actual y una nueva contraseña válida

**Then** el sistema actualiza la contraseña y confirma el cambio.

## US-3.1 Crear perfil profesional

| Campo | Valor |
|--------|-------|
| ID | US-3.1 |
| EPIC | EPIC-03 Professional Profile |
| Prioridad | Alta |
| Requerimientos relacionados | FR-03.1, FR-03.4 |

### Historia

**Como** profesional

**Quiero** crear mi perfil profesional

**Para** ofrecer mis servicios a los clientes dentro de la plataforma.

### Criterios de aceptación

#### Escenario 1: Creación exitosa

**Given** que soy un profesional autenticado

**When** completo la información requerida del perfil

**Then** el sistema crea mi perfil profesional y lo almacena correctamente.

## US-3.2 Editar perfil profesional

| Campo | Valor |
|--------|-------|
| ID | US-3.2 |
| EPIC | EPIC-03 Professional Profile |
| Prioridad | Alta |
| Requerimientos relacionados | FR-03.2 |

### Historia

**Como** profesional

**Quiero** actualizar la información de mi perfil

**Para** mantenerla actualizada para mis clientes.

### Criterios de aceptación

#### Escenario 1: Actualización exitosa

**Given** que poseo un perfil profesional

**When** modifico la información permitida

**Then** el sistema guarda los cambios correctamente.

## US-3.3 Subir fotografía de perfil

| Campo | Valor |
|--------|-------|
| ID | US-3.3 |
| EPIC | EPIC-03 Professional Profile |
| Prioridad | Media |
| Requerimientos relacionados | FR-03.3 |

### Historia

**Como** profesional

**Quiero** subir una fotografía de perfil

**Para** generar mayor confianza en mis clientes.

### Criterios de aceptación

#### Escenario 1: Fotografía cargada correctamente

**Given** que me encuentro editando mi perfil

**When** selecciono una imagen válida

**Then** el sistema almacena la fotografía y la muestra en mi perfil.

## US-3.4 Publicar perfil profesional

| Campo | Valor |
|--------|-------|
| ID | US-3.4 |
| EPIC | EPIC-03 Professional Profile |
| Prioridad | Alta |
| Requerimientos relacionados | FR-03.6, FR-03.7 |

### Historia

**Como** profesional

**Quiero** publicar mi perfil

**Para** que los clientes puedan visualizar mis servicios.

### Criterios de aceptación

#### Escenario 1: Publicación exitosa

**Given** que mi perfil está completo

**When** selecciono la opción "Publicar perfil"

**Then** el sistema hace visible mi perfil para los clientes.

## US-3.5 Consultar perfil profesional

| Campo | Valor |
|--------|-------|
| ID | US-3.5 |
| EPIC | EPIC-03 Professional Profile |
| Prioridad | Alta |
| Requerimientos relacionados | FR-03.7 |

### Historia

**Como** cliente

**Quiero** consultar el perfil de un profesional

**Para** conocer su información antes de realizar una reserva.

### Criterios de aceptación

#### Escenario 1: Consulta exitosa

**Given** que el perfil del profesional está publicado

**When** accedo a su perfil

**Then** el sistema muestra la información pública y los servicios disponibles.

## US-4.1 Configurar disponibilidad

| Campo | Valor |
|--------|-------|
| ID | US-4.1 |
| EPIC | EPIC-04 Availability |
| Prioridad | Alta |
| Requerimientos relacionados | FR-05.1, FR-05.2 |

### Historia

**Como** profesional

**Quiero** configurar mis horarios de atención

**Para** controlar cuándo los clientes pueden realizar reservas.

### Criterios de aceptación

#### Escenario 1: Configuración exitosa

**Given** que soy un profesional autenticado

**When** configuro mis horarios de atención

**Then** el sistema guarda la disponibilidad correctamente.

## US-4.2 Modificar disponibilidad

| Campo | Valor |
|--------|-------|
| ID | US-4.2 |
| EPIC | EPIC-04 Availability |
| Prioridad | Alta |
| Requerimientos relacionados | FR-05.6 |

### Historia

**Como** profesional

**Quiero** modificar mi disponibilidad

**Para** mantener mi agenda actualizada.

### Criterios de aceptación

#### Escenario 1: Actualización exitosa

**Given** que ya tengo una disponibilidad configurada

**When** realizo cambios en mis horarios

**Then** el sistema actualiza la disponibilidad correctamente.

## US-4.3 Bloquear fechas

| Campo | Valor |
|--------|-------|
| ID | US-4.3 |
| EPIC | EPIC-04 Availability |
| Prioridad | Media |
| Requerimientos relacionados | FR-05.3 |

### Historia

**Como** profesional

**Quiero** bloquear fechas específicas

**Para** evitar reservas cuando no estaré disponible.

### Criterios de aceptación

#### Escenario 1: Bloqueo exitoso

**Given** que tengo una agenda configurada

**When** bloqueo una fecha

**Then** el sistema impide nuevas reservas para ese período.

## US-5.1 Reservar una cita

| Campo | Valor |
|--------|-------|
| ID | US-5.1 |
| EPIC | EPIC-05 Booking |
| Prioridad | Alta |
| Requerimientos relacionados | FR-06.1, FR-06.2, FR-06.3 |

### Historia

**Como** cliente

**Quiero** reservar una cita

**Para** agendar un servicio con un profesional.

### Criterios de aceptación

#### Escenario 1: Reserva exitosa

**Given** que existe un horario disponible

**When** selecciono una fecha y hora válidas

**Then** el sistema crea la reserva y confirma la cita.

## US-5.2 Cancelar una reserva

| Campo | Valor |
|--------|-------|
| ID | US-5.2 |
| EPIC | EPIC-05 Booking |
| Prioridad | Alta |
| Requerimientos relacionados | FR-06.5, FR-06.6 |

### Historia

**Como** cliente o profesional

**Quiero** cancelar una reserva

**Para** liberar el horario correspondiente.

### Criterios de aceptación

#### Escenario 1: Cancelación exitosa

**Given** que existe una reserva activa

**When** solicito su cancelación

**Then** el sistema cambia el estado de la reserva y libera la disponibilidad cuando corresponda.

## US-5.3 Reprogramar una reserva

| Campo | Valor |
|--------|-------|
| ID | US-5.3 |
| EPIC | EPIC-05 Booking |
| Prioridad | Alta |
| Requerimientos relacionados | FR-06.7 |

### Historia

**Como** cliente

**Quiero** reprogramar una reserva

**Para** cambiar la fecha u hora de mi cita.

### Criterios de aceptación

#### Escenario 1: Reprogramación exitosa

**Given** que tengo una reserva activa

**When** selecciono un nuevo horario disponible

**Then** el sistema actualiza la reserva y libera el horario anterior.

## US-6.1 Registrar un pago

| Campo | Valor |
|--------|-------|
| ID | US-6.1 |
| EPIC | EPIC-06 Payments |
| Prioridad | Alta |
| Requerimientos relacionados | FR-07.1, FR-07.2 |

### Historia

**Como** cliente

**Quiero** realizar el pago de una reserva

**Para** confirmar la contratación del servicio.

### Criterios de aceptación

#### Escenario 1: Pago exitoso

**Given** que tengo una reserva pendiente de pago

**When** realizo correctamente el pago

**Then** el sistema registra la transacción y actualiza el estado de la reserva.

## US-6.2 Consultar historial de pagos

| Campo | Valor |
|--------|-------|
| ID | US-6.2 |
| EPIC | EPIC-06 Payments |
| Prioridad | Media |
| Requerimientos relacionados | FR-07.4 |

### Historia

**Como** cliente

**Quiero** consultar mis pagos realizados

**Para** llevar un registro de mis transacciones.

### Criterios de aceptación

#### Escenario 1: Consulta exitosa

**Given** que he realizado pagos anteriormente

**When** accedo al historial de pagos

**Then** el sistema muestra todas las transacciones asociadas a mi cuenta.

## US-7.1 Recibir confirmación de reserva

| Campo | Valor |
|--------|-------|
| ID | US-7.1 |
| EPIC | EPIC-07 Notifications |
| Prioridad | Alta |
| Requerimientos relacionados | FR-08.1 |

### Historia

**Como** cliente

**Quiero** recibir una confirmación cuando reserve una cita

**Para** asegurarme de que la reserva fue creada correctamente.

### Criterios de aceptación

#### Escenario 1: Confirmación enviada

**Given** que una reserva fue creada exitosamente

**When** la reserva queda registrada

**Then** el sistema envía una notificación de confirmación.

## US-7.2 Recibir recordatorios

| Campo | Valor |
|--------|-------|
| ID | US-7.2 |
| EPIC | EPIC-07 Notifications |
| Prioridad | Alta |
| Requerimientos relacionados | FR-08.3 |

### Historia

**Como** cliente

**Quiero** recibir recordatorios antes de mi cita

**Para** no olvidar la reserva programada.

### Criterios de aceptación

#### Escenario 1: Recordatorio enviado

**Given** que tengo una reserva próxima

**When** se acerca la fecha y hora de la cita

**Then** el sistema envía un recordatorio automáticamente.

## US-8.1 Consultar próximas reservas

| Campo | Valor |
|--------|-------|
| ID | US-8.1 |
| EPIC | EPIC-08 Customer Portal |
| Prioridad | Alta |
| Requerimientos relacionados | FR-10.1 |

### Historia

**Como** cliente

**Quiero** consultar mis próximas reservas

**Para** conocer las citas que tengo programadas.

### Criterios de aceptación

#### Escenario 1: Consulta exitosa

**Given** que tengo reservas activas

**When** ingreso a mi panel

**Then** el sistema muestra mis próximas citas.

## US-8.2 Consultar historial de reservas

| Campo | Valor |
|--------|-------|
| ID | US-8.2 |
| EPIC | EPIC-08 Customer Portal |
| Prioridad | Media |
| Requerimientos relacionados | FR-10.2 |

### Historia

**Como** cliente

**Quiero** consultar mi historial de reservas

**Para** revisar las citas realizadas anteriormente.

### Criterios de aceptación

#### Escenario 1: Historial disponible

**Given** que he realizado reservas anteriormente

**When** accedo al historial

**Then** el sistema muestra todas mis reservas anteriores.

## US-9.1 Consultar panel profesional

| Campo | Valor |
|--------|-------|
| ID | US-9.1 |
| EPIC | EPIC-09 Professional Dashboard |
| Prioridad | Alta |
| Requerimientos relacionados | FR-09.1 |

### Historia

**Como** profesional

**Quiero** visualizar un resumen de mi actividad

**Para** administrar mi negocio desde un único lugar.

### Criterios de aceptación

#### Escenario 1: Panel cargado correctamente

**Given** que soy un profesional autenticado

**When** ingreso al panel principal

**Then** el sistema muestra el resumen de reservas, pagos y próximos servicios.

## US-9.2 Consultar indicadores del negocio

| Campo | Valor |
|--------|-------|
| ID | US-9.2 |
| EPIC | EPIC-09 Professional Dashboard |
| Prioridad | Media |
| Requerimientos relacionados | FR-09.6 |

### Historia

**Como** profesional

**Quiero** visualizar indicadores de mi actividad

**Para** conocer el desempeño de mi negocio.

### Criterios de aceptación

#### Escenario 1: Indicadores disponibles

**Given** que existen reservas registradas

**When** consulto mi panel

**Then** el sistema muestra indicadores básicos como número de reservas e ingresos generados.

# 4. Definition of Done

Este documento se considera terminado cuando se cumplan los siguientes criterios:

- [x] Se documentaron las historias de usuario del MVP.
- [x] Todas las historias tienen un identificador único.
- [x] Cada historia está asociada a un EPIC.
- [x] Cada historia referencia los requerimientos funcionales correspondientes.
- [x] Todas las historias incluyen criterios de aceptación en formato Given / When / Then.
- [x] El documento cumple con el estándar de documentación del proyecto.
- [x] El documento está versionado en Git.
- [x] El documento está asociado a la tarea ASTRO-1.4 en ClickUp.