# BigNight

Plataforma web (mobile primero, también desktop) para que quien organiza un evento —casamientos sobre todo, pero también cumpleaños, aniversarios, 15, bautismos— arme una página para sus invitados: información del evento, confirmación de asistencia y lista de regalos con pago.

Inspiración directa y competidor: Confites (confites.com). Lo que BigNight hace distinto:
1. **Estilos de verdad, no una plantilla.** 33 estilos en 4 categorías, cada uno con layout, tipografía, ornamento y tono propios. Varios con paletas elegibles.
2. **Regalos que hablan de los novios.** Lista predeterminada o personalizada a partir de un texto con sus intereses, con los mismos rangos de precio.
3. **Regalos con la misma jerarquía que la confirmación.** No escondidos al final.
4. **Mobile cómodo.** Lista compacta en filas, filtros por rango de precio, orden, carrito fijo. Confites muestra un círculo gigante por pantalla.
5. **Confirmación sin fricción.** Un toque, por grupo, sin salir de la página.

Documentos de detalle en `docs/`:
- `docs/producto.md` — decisiones de producto, alcance V1 y V2.
- `docs/arquitectura.md` — stack, modelo de datos, flujos de pago.
- `docs/estilos.md` — sistema de estilos (estructuras × pieles), catálogo, paletas, tono de voz.
- `design/` — tableros de diseño de referencia exportados del canvas (HTML). Son la fuente visual de verdad para cada pantalla.

## Decisiones cerradas

- **Nombre:** BigNight.
- **Modelo de negocio:** plan único de **$ 150.000 ARS**, pago único. Se paga con Mercado Pago; la cuenta se habilita sola cuando Mercado Pago confirma el pago (webhook). No hay link de pago fijo: se genera una preferencia de pago por evento con el id del evento en `external_reference`.
- **Sin comisión sobre regalos.** El 100% de lo que paga el invitado va a los organizadores. Mostrarlo explícito en cada regalo y en el checkout: "El 100% de lo que regales va a {nombres}".
- **Pagos de regalos:** Mercado Pago (la pareja conecta su propia cuenta por OAuth; cuotas, débito, dinero en cuenta) + transferencia por alias/CVU con botón de copiar + datos de cuenta en USD para invitados de afuera. Precios siempre en pesos, aclarando que también se puede pagar en dólares.
- **Regalo compartido** con barra de progreso.
- **Estilos:** todos los diseñados, mostrados en 4 categorías: Con foto, Minimalista sin foto, Artístico, Muñeco de torta.
- **Nombre de la sección de regalos** configurable: Regalos, Regalanos, Gift shop, Mesa de regalos, Lista de regalos u otro. Cada estilo trae uno sugerido.
- **Tono de voz** elegible: Formal ("¿Asistís?"), Cálido, Descontracturado ("¿Venís?"), Divertido.
- **V2 (no en la primera versión, pero va):** invitados cargados con link personalizado ("Hola Sofi, te reservamos 2 lugares") y recordatorios por WhatsApp.

## Stack

Next.js (App Router, TypeScript) · Supabase (Postgres, Auth, Storage para fotos) · Mercado Pago (Checkout Pro + webhooks; OAuth marketplace para cuentas de los novios) · Vercel.

## Convenciones

- Todo el texto de la interfaz en español rioplatense (vos).
- Mobile primero: diseñar a 390 px de ancho y escalar.
- Botones y objetivos táctiles de al menos 44 px. Contraste 4.5:1.
- Accesibilidad: `<button>`, `<a href>`, `<label>` reales; nada de `onClick` en `div`.
- Credenciales siempre en variables de entorno (`.env.local`, nunca commiteado). Ver `.env.example`.
- Montos en centavos (enteros) en la base; formatear con `Intl.NumberFormat('es-AR')`.
