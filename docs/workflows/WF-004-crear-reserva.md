## WF-004 Crear reserva de una consulta en vivo

### Objetivo

Permitir que un cliente reserve una sesión en vivo con un profesional seleccionando un servicio, una fecha y una hora disponibles.

---

### Actores

* **Principal:** Cliente
* **Secundario:** Sistema
* **Secundario:** Profesional

---

### Precondiciones

* El cliente ha iniciado sesión.
* La cuenta del cliente se encuentra activa.
* El perfil del profesional está publicado.
* El servicio seleccionado se encuentra activo.
* El profesional tiene disponibilidad para la fecha y hora seleccionadas.

---

### Flujo principal

1. El cliente accede al perfil del profesional.
2. El sistema muestra los servicios disponibles.
3. El cliente selecciona un servicio de tipo **LIVE_SESSION**.
4. El sistema muestra la descripción, duración y precio del servicio.
5. El cliente selecciona una fecha disponible.
6. El sistema consulta la disponibilidad del profesional.
7. El sistema muestra los horarios disponibles.
8. El cliente selecciona un horario.
9. Si el servicio requiere datos natales, el sistema solicita:

   * Fecha de nacimiento.
   * Hora de nacimiento.
   * Lugar de nacimiento.
10. El cliente puede agregar notas adicionales para el profesional.
11. El cliente confirma la reserva.
12. El sistema valida nuevamente que el horario continúe disponible.
13. El sistema crea la reserva con estado **PENDING_PAYMENT**.
14. El sistema bloquea temporalmente el horario seleccionado durante **15 minutos**.
15. El sistema almacena un snapshot del servicio (nombre, precio, duración y tipo de entrega).
16. El sistema redirige al cliente al proceso de pago.

---

### Flujos alternativos

#### A1. El horario ya no se encuentra disponible

1. El sistema detecta que otro cliente reservó el horario.
2. El sistema informa que el horario ya no está disponible.
3. El cliente selecciona un nuevo horario.
4. El flujo retorna al paso 7.

---

#### A2. El servicio ya no se encuentra disponible

1. El sistema detecta que el servicio fue desactivado.
2. El sistema informa la situación.
3. El proceso finaliza.

---

#### A3. Datos natales incompletos

1. El sistema detecta que faltan datos obligatorios.
2. El sistema informa los campos requeridos.
3. El cliente completa la información.
4. El flujo retorna al paso 11.

---

#### A4. Expiración de la reserva

1. El cliente no completa el pago dentro de los 15 minutos establecidos.
2. El sistema cambia el estado de la reserva a **EXPIRED**.
3. El sistema libera automáticamente el horario reservado.
4. El proceso finaliza.

---

### Postcondiciones

* Se crea una nueva reserva.
* La reserva queda en estado **PENDING_PAYMENT** hasta completar el pago.
* El horario queda bloqueado temporalmente.
* La reserva almacena un snapshot del servicio seleccionado.
* Se inicia el proceso de pago.

---

### Reglas de negocio

* RN-016 Solo los servicios de tipo **LIVE_SESSION** requieren selección de fecha y hora.
* RN-017 El horario seleccionado debe estar disponible al momento de crear la reserva.
* RN-018 Si el servicio requiere datos natales, estos son obligatorios.
* RN-019 La reserva debe almacenar un snapshot del servicio.
* RN-020 Toda reserva inicia con estado **PENDING_PAYMENT**.
* RN-021 Una reserva en estado **PENDING_PAYMENT** bloqueará el horario seleccionado durante un máximo de **15 minutos**.
* RN-022 Durante el tiempo de bloqueo, ningún otro cliente podrá reservar el mismo horario para el mismo profesional.
* RN-023 Si el pago se completa antes de finalizar el tiempo de bloqueo, la reserva cambiará al estado **CONFIRMED**.
* RN-024 Si el pago no se completa dentro de los 15 minutos, la reserva cambiará automáticamente al estado **EXPIRED** y el horario volverá a estar disponible.

---

### Requerimientos funcionales relacionados

* FR-04 Servicios
* FR-05 Disponibilidad
* FR-06 Reservas

---

### Historias de usuario relacionadas

* US-006 Consultar servicios.
* US-007 Consultar disponibilidad.
* US-008 Reservar una consulta en vivo.
