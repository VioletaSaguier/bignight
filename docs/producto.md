# Producto

## Usuarios

- **Organizadores:** la pareja o quien hace el evento. Arman y pagan la página.
- **Invitados:** abren el link desde WhatsApp, casi siempre en el celular. Sus tareas principales: confirmar y regalar.

## Página del invitado — jerarquía (todas los estilos)

1. Portada: nombres, fecha, lugar (con foto en los estilos "Con foto"; B&N por defecto, también Color o Sepia).
2. Fecha límite para confirmar, visible ("Confirmá antes del 30 de mayo · faltan 46 días").
3. Dos botones del mismo peso: **Confirmar** y **{nombre de la sección de regalos}**.
4. Regalos destacados (3 o 4, con precio) + "Ver todos". Aclaración "El 100% va a {nombres} · pesos o dólares".
5. Cuándo y dónde (con mapa), cronograma, dress code (con explicación), preguntas frecuentes.
6. Bloques opcionales que se activan en el panel: alojamiento sugerido (con links de reserva), playlist de Spotify, "volvé seguro".
7. Barra fija abajo con Confirmar y Regalos siempre a mano. Si el invitado ya confirmó, Confirmar pasa a "Ya confirmaste ✓" y Regalos queda como principal.

## Confirmación de asistencia

- En un toque, sin salir de la página. Sin Google Forms, sin cuenta.
- **Por grupo:** una sola respuesta con varias personas (nombre + restricción alimentaria cada una), "+ Sumar otra persona", WhatsApp de contacto.
- Pantalla final: "¡Nos vemos ahí!", botón **Agregar al calendario** (.ics), acceso a regalos, resumen práctico (dress code, alojamiento, playlist).
- **No puedo ir:** pide nombre y mensaje opcional para los novios. Queda registrado en el panel (Confites y los sitios hechos a medida no lo registran). Ofrece regalar igual.
- Preguntas propias configurables (V1: comida; V2: preguntas libres).

## Lista de regalos (invitado, mobile)

- Header con nombre del destino o tema, línea "El 100% de lo que regales va a {nombres}".
- Buscador, chips por rango de precio (Todos / Hasta 150 mil / 150–300 mil / 300 mil–1 M / Más de 1 M), orden por precio asc/desc.
- Vista lista (filas compactas con miniatura) o grilla de 2 columnas.
- Botón + / ✓ por ítem; barra de carrito fija con cantidad y total.
- Regalo compartido: barra de progreso y "% juntado".

## Checkout del invitado (3 pasos + gracias)

1. Tu regalo: ítems del carrito; en compartidos se elige el aporte (50 mil / 100 mil / 200 mil / otro). Total + "El 100% va a {nombres}".
2. Unas palabras: nombre, dedicatoria (con vista previa de cómo la verán), email opcional para comprobante, mostrar u ocultar monto a los novios.
3. Cómo pagás: Mercado Pago (cuotas, débito, dinero en cuenta) / Transferencia (alias con copiar + botón "Ya transferí") / Tarjeta del exterior (USD; pasarela a definir, en V1 datos de cuenta USD).
4. Gracias: confirmación, progreso del compartido, invitación a confirmar asistencia si no lo hizo.

## Panel de organizadores

- **Evento:** nombres, tipo de evento, fecha, lugares, cronograma, dress code, FAQ, bloques opcionales, fecha límite de confirmación.
- **Diseño:**
  - Subir invitación (V1: se extrae paleta y se sugieren estilos; generación completa más adelante).
  - Navegador de estilos por categoría con vista previa en vivo (celular / computadora).
  - Paleta (en estilos que la tengan), foto y filtro, tono de voz, nombre de la sección de regalos, ajuste con palabras (más adelante).
- **Regalos:**
  - Rango de precios y cantidad.
  - Lista predeterminada o personalizada: textarea con intereses → se generan ítems con los mismos precios que la lista genérica pero otros contenidos (ej. "Masaje en Manuel Antonio" en lugar de "Sesión de masajes"). Cada ítem editable/quitable; se pueden agregar propios.
  - Dónde reciben la plata: vincular Mercado Pago, alias para transferencias, cuenta USD.
- **Invitados:** quién confirmó (con grupo y comida), quién no va (con mensaje), exportar.
- **Regalos recibidos:** quién regaló qué, dedicatoria, monto (si el invitado lo permitió), estado de transferencias a confirmar.

## Alta y cobro

1. Registro gratis, arma la página en modo borrador (vista previa compartible con la pareja; invitados no pueden confirmar ni regalar).
2. "Publicar" → Checkout Pro de Mercado Pago por $ 150.000 con `external_reference = event_id`.
3. Webhook de pago aprobado → evento `published`, aviso por mail/WhatsApp con el link.

## Fuera de V1

- Invitados con link personalizado y recordatorios por WhatsApp (**V2, confirmado**).
- Álbum de fotos de invitados por QR, lista de agradecimientos.
- Apertura animada tipo sobre (idea disruptiva), estilos animados.
- Ajuste del estilo describiéndolo con palabras; diseño generado completo desde la invitación.
- Pasarela internacional para tarjetas en USD.
