# Alcance del Proyecto: MedixAi

## Visión del Proyecto
MedixAi es una plataforma SaaS diseñada para clínicas médicas/esteticas/odontologicas que buscan automatizar la facturación, el triaje y la gestión deg citas a través de WhatsApp e Inteligencia Artificial. Nuestro objetivo es reducir la carga administrativa, mejorar la experiencia del paciente mediante respuestas inmediatas y asegurar el recaudo financiero antes de la consulta.

## Características Clave (Key Features)

### 1. AI Triage & Agendamiento
- **Interacción Natural:** Uso de Modelos de Lenguaje (LLMs) para entender la intención del paciente (agendar, cancelar, consultar precios).
- **Pre-diagnóstico Básico:** Recolección de síntomas preliminares para asignar el especialista adecuado o la duración de la cita.
- **Gestión de Agenda:** Verificación de disponibilidad en tiempo real y bloqueo de slots.

### 2. Fintech & Recaudo Automatizado
- **Cobro Anticipado:** Enlaces de pago generados automáticamente (Stripe/Wompi) dentro del chat de WhatsApp.
- **Conciliación:** Confirmación automática de citas solo tras la verificación exitosa del pago.
- **Manejo de Reembolsos:** Políticas claras y flujos automatizados para cancelaciones.

### 3. Disponibilidad en Tiempo Real
- Sincronización bidireccional con calendarios médicos.
- Prevención de "double-booking" mediante bloqueos atómicos temporales.

### 4. Dashboard de Analítica
- Visualización de métricas clave: Tasa de conversión, tiempo de respuesta, ingresos por día/médico.
- Reportes de citas completadas vs. canceladas.

### 5. Almacenamiento HIPAA-Ready
- **Seguridad:** Encriptación de datos sensibles en tránsito y en reposo.
- **Compliance:** Estructura de datos diseñada para facilitar el cumplimiento de normativas de privacidad médica.

### 6. Escalabilidad Multitenant
- Arquitectura diseñada para soportar múltiples clínicas (tenants) con aislamiento de datos estricto.
- Personalización de perfiles y configuraciones por clínica.

## Fases del Proyecto

### Fase 1: Documentación y Maquetación (Actual)
- Definición de alcance y arquitectura.
- Diseño de UI/UX (Mockups).
- Implementación de estructura estática con HTML/CSS y Tailwind.

### Fase 2: Integración React + TypeScript
- Migración de maquetas a componentes React interactivos.
- Configuración de rutas y estado global.
- Lógica de frontend sin persistencia real (mock data).

### Fase 3: Integración Firebase + AI
- Conexión con Firebase (Firestore, Auth, Functions).
- Desarrollo de Cloud Functions para la lógica de negocio.
- Integración de API de WhatsApp y Modelos de IA.
- Implementación de pasarelas de pago.
