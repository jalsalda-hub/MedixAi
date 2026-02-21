# Sistema de Diseño

## Filosofía
- **Mobile-First:** Dado que muchos usuarios (tanto pacientes como personal médico) acceden desde móviles, la interfaz debe priorizar la experiencia en pantallas pequeñas.
- **Clean & Professional:** Estética minimalista, que transmita confianza, higiene y profesionalismo médico.
- **Accesibilidad:** Contraste adecuado y tamaños de fuente legibles.

## Herramientas
- **Tailwind CSS:** Se utilizará exclusivamente para el estilizado. Evitar CSS personalizado a menos que sea estrictamente necesario.

## Convenciones

### Paleta de Colores (Tokens)
Se definen colores semánticos para mantener consistencia:
- **Primary:** Azules médicos o Verde azulado (Teal/Cyan). Transmiten calma y salud.
    - `bg-primary-500`, `text-primary-600`
- **Secondary:** Grises neutros para fondos y estructuras.
    - `bg-gray-50`, `border-gray-200`
- **Actions/Success:** Verde para confirmaciones y pagos exitosos.
    - `text-green-600`
- **Alert/Error:** Rojo suave para cancelaciones o errores.
    - `text-red-500`

### Tipografía
- **Fuente Principal:** Sans-serif moderna (ej. Inter, Roboto o Lato).
- **Jerarquía:**
    - `text-3xl`: Títulos de página.
    - `text-xl`: Encabezados de sección.
    - `text-sm` o `text-base`: Cuerpo de texto.

### Espaciado
- Uso consistente de la escala de Tailwind (p-4, m-2, gap-6).
- Los componentes deben "respirar" (whitespace generoso).
