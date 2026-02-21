# Asignación de Roles y Tareas: Modelo FullStack por Módulos

Para maximizar el aprendizaje y la propiedad de las funcionalidades, hemos adoptado un **Modelo de Desarrollo por Módulos (FullStack)**. En lugar de dividir por capas (Frontend vs Backend), cada desarrollador será dueño de una funcionalidad completa, desde la base de datos hasta la interfaz de usuario.

---

## 🏗️ Eje Transversal (Semana 1): Cimientos del Proyecto
**Participantes:** Developer A & Developer B (Pair Programming)

El objetivo es establecer la base sólida sobre la cual ambos trabajarán.
- **Definición de Esquema:** Diseño conjunto de colecciones en Firestore y configuración del proyecto en Firebase Console.
- **Setup Inicial:** Configuración del repositorio, Vite + React + TypeScript y Tailwind CSS.
- **Layout Base:** Creación de componentes compartidos: Navbar y Sidebar responsivos.

---

## 📅 Developer A: Módulo de Gestión y Agenda (FullStack)
**Objetivo:** Crear la herramienta donde el médico ve su trabajo.

#### Frontend (React)
- **Calendar UI:** Implementar la interfaz de agenda (vistas diaria, semanal, mensual).
- **Dashboard:** Maquetar la vista principal de métricas.

#### Backend (Firebase)
- **Autenticación:** Configurar Login de médicos (Firebase Auth).
- **Seguridad:** Escribir reglas de Firestore (`firestore.rules`) para aislar datos entre médicos (Multitenancy).

#### Lógica de Negocio
- **Bloqueo Manual:** Función para que el médico bloquee horarios no disponibles desde la web.

---

## 🤖 Developer B: Módulo de Comunicación e IA (FullStack)
**Objetivo:** Crear el "cerebro" que interacúa con los pacientes.

#### Backend (Node.js/Cloud Functions)
- **Webhook WhatsApp:** Configurar endpoint para recibir mensajes de la API de Meta.
- **IA Core:** Lógica inicial para conectar OpenAI/Gemini y procesar mensajes entrantes.

#### Frontend (React)
- **Chat Mirror:** Interfaz en tiempo real que refleja los mensajes de WhatsApp usando `onSnapshot` de Firestore.

#### Lógica de Negocio
- **RAG Simple:** Implementar sistema de recuperación de información (lectura de JSON/PDF) para que la IA conozca los servicios de la clínica.

---

## 💳 Developer A: Módulo de Pagos y Liquidación (FullStack)
**Objetivo:** Automatizar el recaudo y conciliación financiera.

#### Backend (Cloud Functions)
- **Webhook Pagos:** Endpoint para recibir confirmaciones de Wompi/Stripe.

#### Frontend (React)
- **Vista de Finanzas:** Tabla de pagos exitosos y pendientes con filtros.

#### Lógica de Negocio
- **Trigger de Confirmación:** Función (`onUpdate` o `onCreate`) que cambia el estado de la cita de "Pendiente" a "Confirmada" automáticamente al recibir el pago.

---

## 🚨 Developer B: Módulo de Comunicación e IA (FullStack) - Parte 2: Triaje
**Objetivo:** Priorizar pacientes y asegurar la asistencia.

#### Backend (Cloud Functions)
- **Triaje IA:** Refinar el prompt para asignar un `TriageScore` (Urgencia/Valor) a cada conversación.

#### Frontend (React)
- **Notificaciones Push:** Implementar Firebase Cloud Messaging (FCM) para alertas de "Alta Prioridad" o "Pago Recibido".

#### Lógica de Negocio
- **Recordatorios:** Cron job o task programado para enviar WhatsApp recordatorio 2 horas antes de la cita.

---

## 💡 ¿Por qué este orden es más conveniente?

1.  **Propiedad de la Feature:** Si algo falla en la "Agenda", el Developer A conoce todo el flujo, desde el CSS hasta la consulta en la base de datos. Elimina el "peloteo" de culpas.
2.  **Aprendizaje Real FullStack:** Ambos aprenden a conectar el Front con el Back, enfrentando los retos de integración reales.
3.  **Orden Lógico de Construcción:**
    *   **Primero:** Se crea la casa (Layout/Auth).
    *   **Segundo:** Se crea el sistema de citas (Agenda) y el bot que las llena (IA).
    *   **Tercero:** Se asegura el flujo de dinero (Pagos).
    *   **Cuarto:** Se optimiza la operación (Triaje/Notificaciones).
