# Arquitectura

## Stack

- **Next.js** (App Router, TypeScript, Server Actions / Route Handlers). Estilos con CSS Modules o Tailwind; los estilos de evento usan variables CSS por tema (ver `docs/estilos.md`).
- **Supabase:** Postgres + Row Level Security, Auth (email mágico para organizadores), Storage (fotos de portada e invitaciones).
- **Mercado Pago:**
  - Cobro del plan: Checkout Pro con preferencia por evento, `external_reference = event_id`, `notification_url` → `/api/webhooks/mercadopago`.
  - Regalos: OAuth para que la pareja conecte su cuenta (modelo marketplace sin `marketplace_fee`, el 100% va a la pareja). Preferencias creadas con el access token de la pareja.
- **Vercel** para deploy.

## Rutas

- `/` — landing de BigNight.
- `/e/[slug]` — página pública del evento (invitado).
- `/e/[slug]/regalos` — lista de regalos.
- `/e/[slug]/regalar` — checkout de regalo.
- `/e/[slug]/gracias` — confirmación de pago.
- `/panel` — panel del organizador (protegido).
- `/panel/[eventId]/diseno`, `/regalos`, `/invitados`, `/recibidos`, `/publicar`.
- `/api/webhooks/mercadopago` — webhook (plan y regalos).
- `/api/ics/[slug]` — archivo de calendario.

## Modelo de datos (borrador)

```
events
  id uuid pk
  owner_id uuid -> auth.users
  slug text unique
  status text  -- draft | pending_payment | published
  event_type text  -- casamiento | cumpleanos | aniversario | quince | otro
  hosts_display text  -- "Lu y Fran"
  date timestamptz
  rsvp_deadline date
  style_id text  -- ej. 'linea-paisaje'
  palette_id text
  voice text  -- formal | calido | descontracturado | divertido
  gifts_label text  -- 'Regalos' | 'Regalanos' | 'Gift shop' | ...
  cover_photo_path text
  cover_photo_filter text  -- bw | color | sepia
  content jsonb  -- lugares, cronograma, dress code, faq, bloques opcionales
  bank_alias text, bank_holder text, usd_account text
  mp_user_id text, mp_access_token_enc text, mp_refresh_token_enc text
  plan_paid_at timestamptz, plan_payment_id text
  created_at, updated_at

gifts
  id uuid pk
  event_id uuid -> events
  title text
  note text  -- "por qué lo elegimos"
  place text
  price_cents bigint
  category text
  is_group boolean
  image_path text
  sort int

rsvps
  id uuid pk
  event_id uuid
  attending boolean
  contact_phone text
  message text  -- para "no puedo ir"
  created_at

rsvp_people
  id uuid pk
  rsvp_id uuid -> rsvps
  full_name text
  diet text

gift_orders
  id uuid pk
  event_id uuid
  giver_name text
  dedication text
  giver_email text
  show_amount boolean
  method text  -- mercadopago | transfer | usd
  status text  -- pending | approved | transfer_claimed | confirmed | rejected
  total_cents bigint
  mp_preference_id text, mp_payment_id text
  created_at

gift_order_items
  order_id uuid -> gift_orders
  gift_id uuid -> gifts
  amount_cents bigint  -- en compartidos, el aporte
```

Progreso de un regalo compartido = suma de `amount_cents` de ítems con orden `approved|confirmed` / `price_cents`.

## Flujos de pago

**Plan ($ 150.000):** panel → `POST /api/plan/checkout` crea preferencia (credenciales de BigNight) → redirect a Mercado Pago → webhook `payment` → `GET /v1/payments/{id}` → si `approved` y `external_reference` = event → `events.status = 'published'`, `plan_paid_at = now()`.

**Regalo con Mercado Pago:** checkout → `POST /api/gifts/checkout` crea `gift_order` pending + preferencia con el token de la pareja → webhook → actualiza orden.

**Transferencia:** crea `gift_order` con `method=transfer`, invitado toca "Ya transferí" → `transfer_claimed`; la pareja confirma en el panel → `confirmed`.

Validar siempre la firma del webhook (`x-signature`) y re-consultar el pago a la API antes de cambiar estados.

## Variables de entorno

Ver `.env.example`.
