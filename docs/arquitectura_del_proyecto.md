# Arquitectura del Proyecto

## Pilares Arquitectónicos

### 1. Atomic Booking (Reserva Atómica)
Para evitar conflictos de agenda y condiciones de carrera, implementamos un flujo transaccional estricto:
1.  **Hold (Bloqueo):** El sistema reserva temporalmente el horario (ej. 10 minutos) mientras el usuario realiza el pago.
2.  **Payment (Pago):** El usuario completa la transacción en la pasarela.
3.  **Confirm (Confirmación):** Al recibir el webhook de éxito, el estado pasa a "Confirmado". Si el tiempo expira sin pago, el slot se libera automáticamente.

### 2. Human-in-the-loop (HITL)
Aunque la IA maneja la mayoría de interacciones, el sistema permite la intervención humana:
- **Máquina de Estados:** Detecta cuando la IA no puede resolver una duda o el sentimiento del usuario es negativo.
- **Handoff:** Transfiere la conversación a un agente humano.
- **Chat Mirror:** El Dashboard permite a los administradores ver las conversaciones de la IA en tiempo real e intervenir si es necesario.

### 3. Multitenancy (Multitenencia)
La arquitectura de datos en Firestore asegura el aislamiento total entre clínicas:
- **Estructura de Datos:** Todo documento pertenece a una ruta raíz `/tenants/{tenantId}/...`.
- **Security Rules:** Las reglas de seguridad de Firebase validan que un usuario autenticado solo pueda leer/escribir en el `tenantId` al que pertenece su `custom claim` o perfil.

## Flujo de Webhooks

### Pagos (Stripe / Wompi)
1.  El usuario inicia el pago -> Se genera una sesión de pago con `metadata` (tenantId, appointmentId).
2.  La pasarela procesa el pago.
3.  La pasarela envía un evento POST a nuestra Cloud Function `handlePaymentWebhook`.
4.  La función valida la firma, actualiza el estado de la cita en Firestore y notifica al usuario por WhatsApp.

### WhatsApp (Cloud API)
1.  El usuario envía un mensaje.
2.  Meta envía un POST a `webhookWhatsApp`.
3.  La función encola el mensaje para procesamiento o respeta el estado "Human Mode" si está activo.
4.  La IA genera la respuesta y se envía de vuelta mediante la API de WhatsApp.
