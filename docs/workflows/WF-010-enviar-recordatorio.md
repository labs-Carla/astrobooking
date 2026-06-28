## WF-010 Enviar recordatorios automáticos

### Objetivo

Enviar recordatorios automáticos a clientes y profesionales sobre las reservas próximas a realizarse, reduciendo ausencias y mejorando la experiencia de uso de la plataforma.

---

### Actores

* **Principal:** Sistema
* **Secundario:** Cliente
* **Secundario:** Profesional

---

### Precondiciones

* Existe una reserva en estado **CONFIRMED**.
* La reserva corresponde a una consulta en vivo.
* La fecha y hora de la reserva se encuentran dentro del período configurado para el envío del recordatorio.

---

### Flujo principal

1. El sistema ejecuta el proceso programado de recordatorios.
2. El sistema identifica las reservas próximas a realizarse.
3. El sistema genera el contenido del recordatorio.
4. El sistema envía una notificación al cliente.
5. El sistema envía una notificación al profesional.
6. El sistema registra el envío del recordatorio.
7. El proceso finaliza.

---

### Flujos alternativos

#### A1. La reserva fue cancelada

1. El sistema detecta que la reserva se encuentra en estado **CANCELLED**.
2. El sistema omite el envío del recordatorio.
3. El proceso finaliza.

---

#### A2. Error al enviar la notificación

1. El sistema detecta un error durante el envío.
2. El sistema registra el incidente.
3. El proceso finaliza.

---

#### A3. La reserva ya fue completada

1. El sistema detecta que la reserva ya se realizó.
2. El sistema no envía recordatorios.
3. El proceso finaliza.

---

### Postcondiciones

* El cliente recibe un recordatorio de su reserva.
* El profesional recibe un recordatorio de la sesión programada.
* El sistema registra el envío de las notificaciones.

---

### Reglas de negocio

* RN-051 Solo las reservas en estado **CONFIRMED** generan recordatorios.
* RN-052 Los recordatorios solo aplican a servicios de tipo **LIVE_SESSION**.
* RN-053 El sistema debe registrar cada recordatorio enviado.
* RN-054 Una reserva no debe recibir recordatorios después de ser completada o cancelada.
* RN-055 El envío de recordatorios debe ejecutarse mediante un proceso automático programado.

---

### Requerimientos funcionales relacionados

* FR-06 Reservas
* FR-08 Notificaciones

---

### Historias de usuario relacionadas

* US-014 Recibir recordatorios de una reserva.