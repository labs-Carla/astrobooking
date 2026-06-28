## WF-003 Password Recovery

### Objetivo

Permitir que un usuario restablezca su contraseña de forma segura mediante un enlace de recuperación enviado a su correo electrónico.

---

### Actores

* **Principal:** Usuario
* **Secundario:** Sistema
* **Servicio Externo:** Proveedor de correo electrónico

---

### Precondiciones

* El usuario accede a la opción "¿Olvidaste tu contraseña?".
* El sistema se encuentra disponible.

---

### Flujo principal

1. El usuario accede a la pantalla de recuperación de contraseña.
2. El sistema muestra el formulario de recuperación.
3. El usuario ingresa su correo electrónico.
4. El usuario envía la solicitud.
5. El sistema valida el formato del correo electrónico.
6. El sistema genera un token de recuperación de un solo uso con tiempo de expiración.
7. El sistema envía un correo electrónico con el enlace de recuperación.
8. El sistema informa que, si el correo está registrado, recibirá instrucciones para restablecer su contraseña.
9. El usuario accede al enlace recibido en el correo.
10. El sistema valida que el token sea válido y no haya expirado.
11. El sistema muestra el formulario para establecer una nueva contraseña.
12. El usuario ingresa y confirma la nueva contraseña.
13. El sistema valida la información.
14. El sistema cifra la nueva contraseña.
15. El sistema actualiza la contraseña del usuario.
16. El sistema invalida el token de recuperación.
17. El sistema informa que la contraseña fue actualizada correctamente.

---

### Flujos alternativos

#### A1. Correo electrónico inválido

1. El sistema detecta un formato de correo inválido.
2. El sistema informa el error.
3. El usuario corrige la información.
4. El flujo retorna al paso 4.

---

#### A2. Token inválido

1. El sistema detecta que el token no existe o fue alterado.
2. El sistema informa que el enlace no es válido.
3. El proceso finaliza.

---

#### A3. Token expirado

1. El sistema detecta que el token expiró.
2. El sistema informa que debe solicitar un nuevo enlace de recuperación.
3. El proceso finaliza.

---

#### A4. Contraseñas diferentes

1. El sistema detecta que la contraseña y su confirmación no coinciden.
2. El sistema informa el error.
3. El usuario corrige la información.
4. El flujo retorna al paso 13.

---

### Postcondiciones

* La contraseña del usuario queda actualizada.
* La contraseña se almacena utilizando un algoritmo de hash seguro.
* El token de recuperación queda invalidado.
* El usuario puede iniciar sesión utilizando la nueva contraseña.

---

### Reglas de negocio

* RN-011 El sistema no debe revelar si un correo electrónico se encuentra registrado.
* RN-012 El enlace de recuperación debe ser de un solo uso.
* RN-013 El token de recuperación debe tener un tiempo de expiración.
* RN-014 La nueva contraseña debe almacenarse utilizando un algoritmo de hash seguro.
* RN-015 El token debe invalidarse inmediatamente después de utilizarse.

---

### Requerimientos funcionales relacionados

* FR-02 Autenticación

---

### Historias de usuario relacionadas

* US-005 Recuperación de contraseña.
