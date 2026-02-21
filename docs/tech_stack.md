# Tech Stack

## Frontend (Panel de Control y Administrativo)
- **Framework:** React 18+
- **Lenguaje:** TypeScript (Tipado estricto para reducir errores).
- **Estilos:** Tailwind CSS (Utilidades para diseño rápido y responsivo).
- **Estado/Gestión:** React Context API o Zustand (según complejidad).
- **Routing:** React Router.

## Backend & Base de Datos (Serverless)
- **Plataforma:** Firebase.
- **Base de Datos:** Cloud Firestore (NoSQL, escalable, tiempo real).
- **Autenticación:** Firebase Auth (Email/Password, Social Login).
- **Lógica de Servidor:** Cloud Functions for Firebase (Node.js/TypeScript).
- **Almacenamiento:** Cloud Storage (Imágenes médicas, comprobantes).

## Inteligencia Artificial (AI)
- **Modelos:** OpenAI (GPT-4o) o Google Gemini 1.5 Pro.
- **Implementación:** Cloud Functions actuando como middleware.
- **Técnica:** RAG (Retrieval-Augmented Generation) con búsqueda vectorial para contexto específico de la clínica (precios, doctores, horarios).

## Integraciones Externas
- **Mensajería:** WhatsApp Business API (Cloud API).
- **Pagos:** Stripe, Wompi o MercadoPago (según región).
- **Agenda:** Integración potencial con Google Calendar API.
