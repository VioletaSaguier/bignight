# Sistema de estilos

Cada estilo = **estructura** (layout y orden de bloques) + **piel** (tipografías, paleta, ornamentos SVG, forma de botones, textos sugeridos). Implementar como datos (un objeto por estilo) + componentes de estructura reutilizables, para no mantener 33 páginas sueltas.

Todas las estructuras respetan la jerarquía de `docs/producto.md` (confirmar y regalos arriba, barra fija).

## Estructuras base

- `centrada` — todo centrado, ornamento/dibujo arriba (familia a línea, Susurro, Firma).
- `portada-foto` — foto a sangre con degradé y textos encima (Foto · Portada, Romántico).
- `arco` — foto o ilustración en arco (Foto · En arco, Romántico).
- `revista` — foto grande + nombres editoriales + fecha grande (Foto · Revista, Editorial).
- `afiche` — nombres enormes + ilustración (Afiche, Fiesta, La porción).
- `tarjeta` — contenido dentro de un marco (Neo Deco, Gótico, Marco de pinceladas, Marco ondulado).

## Catálogo (33) por categoría

**Con foto (8):** Foto · Portada a sangre, Foto · En arco, Foto · Revista, Foto · Con dibujo a línea, Foto + garabato, Romántico, Editorial minimal, Celestial. (+ versión desktop de portada.)

**Minimalista sin foto (9):** Paisaje a línea, Susurro, Firma roja, Línea · Viñedo, Línea · Ciudad, Línea · Costa, Línea · Estancia, Línea · Capilla, Línea · Rama de olivo.

**Artístico (11):** Gouache, Rayas de toldo, Marco ondulado, Afiche tipográfico, Corazón pintado, Cuaderno ilustrado, Groovy retro, Huerto mediterráneo, Neo Deco, Gótico, Fiesta pop.

**Muñeco de torta (5):** Brindis en rojo, Gouache con cerezas, La porción, Marco de pinceladas, Bola de espejos.

Los HTML de referencia de cada uno están en `design/` (mismo nombre).

## Paletas (estilos minimal)

Cada uno con 5 paletas `[fondo, tinta]`:

- Paisaje a línea: Tinta `#F7F4EC/#2A2A26`, Oliva `#F2F0E4/#4A5A33`, Terracota `#F8EEE4/#9C4528`, Azul toscano `#F1F3F2/#2B4A8C`, Ciruela `#F5EEF0/#6B2E4A`.
- Susurro: Arena `#E3DBCF/#3F3A33`, Niebla `#ECEDEB/#2F3437`, Salvia `#DDE2D3/#34402F`, Rosa seco `#EAD9D3/#5A3A36`, Noche `#23252B/#E7E2D8`.
- Viñedo: Malbec `#F5EFEB/#5E1F2E` + Tinta, Oliva, Terracota, Azul toscano.
- Ciudad: Tinta `#F6F4EF/#22221F`, Azul toscano, Ciruela, Oliva, Noche `#1F2126/#E9E4D8`.
- Costa: Océano `#F1F4F5/#1F4E6E`, Arena `#F4EDE1/#6A5236`, Coral `#FAF0EA/#B4492F`, Salvia `#EEF1E8/#46593F`, Tinta.
- Estancia: Pampa `#F3F0E3/#3E4C2E`, Cuero `#F5ECE0/#7A4A28`, Tinta, Azul toscano, Ciruela.
- Capilla: Marfil `#FAF7F0/#6D5B3E`, Azul noche `#F1F2F5/#1F2D4E`, Salvia, Rosa seco `#F6ECE8/#7A4A45`, Tinta.
- Rama de olivo: Olivo `#F4F3EC/#55633C`, Tinta, Terracota, Azul toscano, Lavanda `#F4F1F6/#5B4A7A`.
- Brindis en rojo: Rojo cereza `#F3EEE6/#C2281E`, Cobalto `#F2F1EC/#2449B8`, Verde botella `#F1EFE4/#2F5A3A`, Rosa `#F8E9EA/#B1335B`.
- Marco de pinceladas: Rojo `#F4EFE7/#C42A20`, Azul `#F3F2EE/#2348B5`, Verde `#F1F0E6/#2F6140`, Bordó `#F5EEEA/#7B1F2B`.

## Nombre sugerido de la sección de regalos por estilo

Regalos (Paisaje, Estancia, Ondas, Foto · Portada, Foto · Arco, La porción) · Regalanos (Firma, Garabato, Gouache, Afiche, Costa, Brindis en rojo, Bola de espejos) · Gift shop (Corazón, Rayas, Ciudad, Foto · Revista, Gouache con cerezas) · Mesa de regalos (Susurro, Viñedo, Capilla, Foto · Con dibujo, Marco de pinceladas) · Lista de regalos (Rama de olivo).

## Tono de voz

| Texto | Formal | Cálido | Descontracturado | Divertido |
|---|---|---|---|---|
| Bienvenida | Tenemos el agrado de invitarte a celebrar nuestro casamiento. | Nos casamos y queremos que estés ahí con nosotros. | ¡Nos casamos! Y obvio que te queremos ahí. | Se viene. Despejá la agenda y prepará las piernas. |
| Pregunta | ¿Asistís? | ¿Nos acompañás? | ¿Venís? | ¿Caés o te lo perdés? |
| Botones | Confirmo asistencia · No podré asistir | Sí, voy · Esta vez no puedo | ¡Voy! · No llego | Obvio · Me lo pierdo (llorando) |
| Recordatorio | Te recordamos confirmar tu asistencia antes del {fecha}. | Nos encantaría saber si venís, ¿nos confirmás antes del {fecha}? | Che, ¿venís o no? Tenés hasta el {fecha}. | El catering nos pregunta por vos. Respondé antes del {fecha}. |
| Invitación a regalar | Si deseás obsequiarnos algo, aquí encontrarás algunas sugerencias. | Si querés hacernos un regalo, armamos esta lista con cariño. | ¿Querés regalarnos algo? Acá van ideas. | Tu presencia es el regalo. Pero si insistís… |
| Gracias | Muchas gracias por tu obsequio. Lo recibimos con mucho afecto. | ¡Gracias! Nos emocionó mucho tu regalo. | ¡Gracias, sos lo más! Ya lo estamos disfrutando en la cabeza. | Gracias. Te debemos un trago (o tres). |

Toda frase fija sale de este diccionario según `events.voice`; el organizador puede sobrescribir cualquiera.
