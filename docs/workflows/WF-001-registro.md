## WF-001 User Registration

### Objetivo

Permitir que un visitante cree una cuenta en AstroBooking para acceder a las funcionalidades de la plataforma como Cliente o Profesional.

---

### Actores

* **Principal:** Visitante
* **Secundario:** Sistema

---

### Precondiciones

* El visitante no posee una cuenta registrada con el correo electrónico proporcionado.
* El sistema se encuentra disponible.
* El formulario de registro está accesible.

---

### Flujo principal

1. El visitante accede a la pantalla de registro.
2. El sistema muestra el formulario de registro.
3. El visitante ingresa su información personal:

   * Nombre
   * Apellido
   * Correo electrónico
   * Contraseña
   * Confirmación de contraseña
4. El visitante selecciona el tipo de cuenta:

   * Cliente
   * Profesional
5. El visitante acepta los términos y condiciones.
6. El visitante envía el formulario.
7. El sistema valida la información ingresada.
8. El sistema verifica que el correo electrónico no exista.
9. El sistema cifra la contraseña.
10. El sistema crea el usuario con estado **PENDING_EMAIL_VERIFICATION**.
11. El sistema genera un enlace de verificación.
12. El sistema envía el correo electrónico de verificación.
13. El sistema informa que el registro fue exitoso.

---

### Flujos alternativos

#### A1. Correo electrónico ya registrado

1. El sistema detecta que el correo ya existe.
2. El sistema muestra un mensaje indicando que el correo ya se encuentra registrado.
3. El proceso finaliza sin crear la cuenta.

---

#### A2. Información inválida

1. El sistema detecta errores de validación.
2. El sistema muestra los campos con error.
3. El visitante corrige la información.
4. El flujo retorna al paso 6.

---

#### A3. Contraseñas diferentes

1. El sistema detecta que la contraseña y su confirmación no coinciden.
2. El sistema informa el error.
3. El visitante corrige la información.
4. El flujo retorna al paso 6.

---

#### A4. Error al enviar el correo de verificación

1. El usuario es registrado correctamente.
2. El sistema no logra enviar el correo de verificación.
3. El sistema registra el incidente.
4. El usuario permanece con estado **PENDING_EMAIL_VERIFICATION**.

---

### Postcondiciones

* El usuario queda registrado en la base de datos.
* La contraseña queda almacenada de forma cifrada.
* La cuenta queda pendiente de verificación de correo.
* Se registra la fecha de creación del usuario.

---

### Reglas de negocio

* RN-001 El correo electrónico debe ser único.
* RN-002 La contraseña debe almacenarse utilizando un algoritmo de hash seguro.
* RN-003 El rol inicial solo puede ser **Cliente** o **Profesional**.
* RN-004 La cuenta no podrá iniciar sesión hasta verificar el correo electrónico.
* RN-005 El usuario debe aceptar los términos y condiciones antes de completar el registro.

---

### Requerimientos funcionales relacionados

* FR-01 Gestión de usuarios
* FR-02 Autenticación

---

### Historias de usuario relacionadas

* US-001 Registro de usuario
* US-002 Verificación de correo electrónico
