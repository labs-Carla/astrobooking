## WF-009 Reprogramar reserva

### Objetivo

Permitir que un cliente o un profesional cambie la fecha y hora de una reserva previamente confirmada, manteniendo la integridad de la agenda y notificando a las partes involucradas.

---

### Actores

* **Principal:** Cliente o Profesional
* **Secundario:** Sistema

---

### Precondiciones

* Existe una reserva en estado **CONFIRMED**.
* La reserva aún no ha sido completada ni cancelada.
* El profesional dispone de nuevos horarios disponibles.

---

### Flujo principal

1. El cliente o el profesional accede al detalle de la reserva.
2. El sistema muestra la información de la reserva.
3. El usuario selecciona la opción **Reprogramar reserva**.
4. El sistema consulta la disponibilidad actual del profesional.
5. El sistema muestra los horarios disponibles.
6. El usuario selecciona una nueva fecha y hora.
7. El sistema valida que el nuevo horario continúa disponible.
8. El sistema actualiza la fecha y hora de la reserva.
9. El sistema libera el horario anteriormente reservado.
10. El sistema reserva el nuevo horario.
11. El sistema registra la fecha de modificación.
12. El sistema notifica al cliente.
13. El sistema notifica al profesional.
14. El proceso finaliza.

---

### Flujos alternativos

#### A1. El nuevo horario ya no está disponible

1. El sistema detecta que otro cliente reservó el horario.
2. El sistema informa la situación.
3. El usuario selecciona un nuevo horario.
4. El flujo retorna al paso 5.

---

#### A2. La reserva ya fue cancelada

1. El sistema detecta que la reserva se encuentra en estado **CANCELLED**.
2. El sistema informa que no es posible reprogramarla.
3. El proceso finaliza.

---

#### A3. La reserva ya fue completada

1. El sistema detecta que la reserva se encuentra en estado **COMPLETED**.
2. El sistema informa que no es posible reprogramarla.
3. El proceso finaliza.

---

#### A4. Error al enviar las notificaciones

1. La reserva se actualiza correctamente.
2. El sistema no logra enviar una o más notificaciones.
3. El sistema registra el incidente.
4. El proceso finaliza.

---

### Postcondiciones

* La reserva mantiene el estado **CONFIRMED**.
* El horario anterior queda disponible.
* El nuevo horario queda reservado.
* Cliente y profesional reciben una notificación del cambio.

---

### Reglas de negocio

* RN-046 Solo las reservas en estado **CONFIRMED** pueden reprogramarse.
* RN-047 El nuevo horario debe estar disponible antes de confirmar el cambio.
* RN-048 La reprogramación libera automáticamente el horario anterior.
* RN-049 El nuevo horario queda reservado inmediatamente después de la reprogramación.
* RN-050 Toda reprogramación debe generar una notificación para el cliente y el profesional.

---

### Requerimientos funcionales relacionados

* FR-05 Disponibilidad
* FR-06 Reservas
* FR-08 Notificaciones

---

### Historias de usuario relacionadas

* US-013 Reprogramar una reserva.
