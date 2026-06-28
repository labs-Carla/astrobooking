## WF-008 Cancelar reserva

### Objetivo

Permitir que un cliente o un profesional cancele una reserva previamente confirmada, liberando los recursos asociados y notificando a las partes involucradas.

---

### Actores

* **Principal:** Cliente o Profesional
* **Secundario:** Sistema

---

### Precondiciones

* Existe una reserva registrada.
* La reserva se encuentra en estado **CONFIRMED**.
* La reserva aún no ha sido completada ni cancelada.

---

### Flujo principal

1. El cliente o el profesional accede al detalle de la reserva.
2. El sistema muestra la información de la reserva.
3. El usuario selecciona la opción **Cancelar reserva**.
4. El sistema solicita la confirmación de la cancelación.
5. El usuario confirma la acción.
6. El sistema valida que la reserva puede ser cancelada.
7. El sistema cambia el estado de la reserva a **CANCELLED**.
8. Si corresponde a una consulta en vivo, el sistema libera el horario reservado.
9. El sistema registra la fecha de cancelación.
10. El sistema genera una notificación para el cliente.
11. El sistema genera una notificación para el profesional.
12. El proceso finaliza.

---

### Flujos alternativos

#### A1. La reserva ya fue cancelada

1. El sistema detecta que la reserva ya se encuentra cancelada.
2. El sistema informa la situación.
3. El proceso finaliza.

---

#### A2. La reserva ya fue completada

1. El sistema detecta que la reserva se encuentra en estado **COMPLETED**.
2. El sistema informa que no es posible cancelar la reserva.
3. El proceso finaliza.

---

#### A3. Error al enviar las notificaciones

1. La reserva se cancela correctamente.
2. El sistema no logra enviar una o más notificaciones.
3. El sistema registra el incidente.
4. El proceso finaliza.

---

### Postcondiciones

* La reserva queda en estado **CANCELLED**.
* El horario vuelve a estar disponible cuando aplica.
* El cliente y el profesional son notificados.

---

### Reglas de negocio

* RN-041 Solo las reservas en estado **CONFIRMED** pueden cancelarse.
* RN-042 Una reserva cancelada no puede volver al estado **CONFIRMED**.
* RN-043 La cancelación de una consulta en vivo libera automáticamente el horario reservado.
* RN-044 El sistema debe registrar la fecha de cancelación.
* RN-045 Toda cancelación debe generar una notificación para las partes involucradas.

---

### Requerimientos funcionales relacionados

* FR-06 Reservas
* FR-08 Notificaciones

---

### Historias de usuario relacionadas

* US-012 Cancelar una reserva.
