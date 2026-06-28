## WF-006 Procesar pago

### Objetivo

Permitir que un cliente complete el pago de una reserva utilizando una pasarela de pagos, garantizando la actualización del estado de la reserva y del pago.

---

### Actores

* **Principal:** Cliente
* **Secundario:** Sistema
* **Servicio Externo:** Pasarela de pagos

---

### Precondiciones

* Existe una reserva con estado **PENDING_PAYMENT**.
* El monto del pago corresponde al valor del servicio.
* La reserva no ha expirado.

---

### Flujo principal

1. El sistema redirige al cliente a la pasarela de pagos.
2. El cliente selecciona el método de pago.
3. El cliente completa la información requerida por la pasarela.
4. La pasarela procesa la transacción.
5. La pasarela notifica el resultado al sistema.
6. El sistema registra el pago.
7. El sistema actualiza el estado del pago a **PAID**.
8. El sistema actualiza la reserva a estado **CONFIRMED**.
9. Si corresponde a una consulta en vivo, el sistema confirma definitivamente el horario reservado.
10. Si corresponde a un informe PDF, la solicitud queda disponible para que el profesional inicie su elaboración.
11. El sistema genera la notificación de confirmación.
12. El sistema finaliza el proceso.

---

### Flujos alternativos

#### A1. Pago rechazado

1. La pasarela rechaza la transacción.
2. El sistema registra el intento de pago.
3. El pago queda con estado **FAILED**.
4. La reserva permanece en estado **PENDING_PAYMENT** hasta que expire el tiempo de bloqueo o el cliente intente nuevamente.

---

#### A2. Pago cancelado por el cliente

1. El cliente abandona el proceso de pago.
2. El sistema mantiene la reserva en estado **PENDING_PAYMENT**.
3. El proceso finaliza.

---

#### A3. Reserva expirada

1. El sistema detecta que la reserva expiró antes de finalizar el pago.
2. El sistema cancela el proceso.
3. El sistema informa al cliente que debe realizar una nueva reserva.

---

#### A4. Error de comunicación con la pasarela

1. El sistema no recibe confirmación de la transacción.
2. El sistema registra el incidente.
3. La reserva permanece en estado **PENDING_PAYMENT** hasta recibir una confirmación o expirar.

---

### Postcondiciones

* El pago queda registrado.
* La reserva cambia a **CONFIRMED** cuando el pago es exitoso.
* El cliente recibe una confirmación de la compra.
* El profesional puede visualizar la nueva reserva.

---

### Reglas de negocio

* RN-031 Todo pago debe estar asociado a una única reserva.
* RN-032 Solo las reservas en estado **PENDING_PAYMENT** pueden procesar pagos.
* RN-033 Un pago exitoso cambia automáticamente la reserva a **CONFIRMED**.
* RN-034 Una reserva expirada no puede recibir pagos.
* RN-035 El sistema debe registrar el resultado de cada intento de pago.

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
