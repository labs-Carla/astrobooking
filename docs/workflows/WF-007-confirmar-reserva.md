## WF-007 Confirmar reserva

### Objetivo

Confirmar una reserva una vez que el pago ha sido procesado exitosamente, notificando al cliente y al profesional, y dejando la reserva lista para su ejecución.

---

### Actores

* **Principal:** Sistema
* **Secundario:** Cliente
* **Secundario:** Profesional

---

### Precondiciones

* Existe una reserva con estado **PENDING_PAYMENT**.
* El pago fue procesado exitosamente.
* La reserva no se encuentra expirada.

---

### Flujo principal

1. El sistema recibe la confirmación del pago.
2. El sistema valida que la transacción fue aprobada.
3. El sistema actualiza el estado del pago a **PAID**.
4. El sistema cambia el estado de la reserva a **CONFIRMED**.
5. Si la reserva corresponde a una consulta en vivo:

   * El horario queda confirmado definitivamente.
6. Si la reserva corresponde a un informe PDF:

   * La solicitud queda disponible para que el profesional inicie su elaboración.
7. El sistema genera una notificación para el cliente.
8. El sistema genera una notificación para el profesional.
9. El sistema registra la fecha de confirmación.
10. El proceso finaliza.

---

### Flujos alternativos

#### A1. El pago no fue aprobado

1. El sistema detecta que el pago fue rechazado.
2. La reserva permanece en estado **PENDING_PAYMENT**.
3. El proceso finaliza.

---

#### A2. La reserva expiró antes de recibir la confirmación del pago

1. El sistema detecta que la reserva cambió al estado **EXPIRED**.
2. El sistema registra el incidente.
3. El proceso finaliza.

---

#### A3. Error al enviar las notificaciones

1. La reserva queda confirmada correctamente.
2. El sistema no logra enviar una o más notificaciones.
3. El sistema registra el incidente.
4. El proceso finaliza.

---

### Postcondiciones

* La reserva queda en estado **CONFIRMED**.
* El pago queda registrado como **PAID**.
* El cliente recibe la confirmación de la compra.
* El profesional visualiza la nueva reserva en su panel.

---

### Reglas de negocio

* RN-036 Solo un pago aprobado puede confirmar una reserva.
* RN-037 Una reserva confirmada no puede regresar al estado **PENDING_PAYMENT**.
* RN-038 El sistema debe notificar tanto al cliente como al profesional.
* RN-039 La confirmación de una consulta en vivo bloquea definitivamente el horario seleccionado.
* RN-040 Una solicitud de informe PDF queda disponible para ser atendida por el profesional una vez confirmada.

---

### Requerimientos funcionales relacionados

* FR-06 Reservas
* FR-07 Pagos
* FR-08 Notificaciones

---

### Historias de usuario relacionadas

* US-008 Reservar una consulta en vivo.
* US-009 Comprar un informe PDF.
* US-010 Realizar el pago de un servicio.
* US-011 Recibir la confirmación de una reserva.
