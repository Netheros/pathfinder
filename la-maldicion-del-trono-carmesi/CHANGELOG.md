# Registro de cambios

## 2026-06-14

### Inventario de Netheros

Se añadió una `Poción de restablecimiento menor` al inventario de Netheros, consolidando la entrada existente y dejando la cantidad total en `2`.

## 2026-05-17

### Inventario de Netheros

Se añadió la `Baraja de presagio` a `inventario_netheros.yaml` dentro de `objetos_varios`, con ubicación `mochila`.

Se dejó además una nota narrativa asociada al objeto:
- `Paimon ha sido absorbido por la baraja y ahora habla a través de ella como consejero del grupo.`

También se actualizaron las cargas de la `Varita de proyectil mágico`, que pasan de `16/50` a `14/50`.

## 2026-05-05

### Documentación de referencia

Se añadieron dos documentos auxiliares de consulta basados en la guía de Treantmonk para magos de Pathfinder:

- `treantmonk_guide_wizards_being_a_god.md`
- `treantmonk_guide_wizards_being_a_god.es.md`

Proceso aplicado:
- El Markdown en inglés se regeneró a partir de un HTML aportado por el usuario, en lugar de reutilizar una importación previa menos fiable.
- La estructura del documento se recompuso desde el HTML para conservar mejor títulos, listas, bloques y enlaces.
- Las valoraciones cromáticas del documento original se preservaron como etiquetas semánticas explícitas: `[RED]`, `[ORANGE]`, `[GREEN]` y `[BLUE]`.
- La traducción al castellano se rehizo tomando como base el Markdown inglés limpio.
- Durante esa regeneración de la traducción se corrigieron varias corrupciones heredadas de una versión castellana anterior que había quedado con bloques concatenados o truncados.

Resultado operativo:
- La versión inglesa queda como referencia estructural limpia.
- La versión castellana conserva las mismas etiquetas semánticas de valoración y ya no arrastra los errores de concatenación detectados en bloques como `Sleep`, `Expeditious Retreat`, `Flaming Sphere`, `Veil`, `Incendiary Cloud`, `Circle of Death` y `Maze`.
- Estos documentos se consideran apoyo táctico y de lectura, no fuente de verdad reglada de Pathfinder 1.ª edición.

### Netheros

Se desglosaron los espacios diarios de `ficha_netheros.yaml` por fuente dentro de `lanzamiento_de_conjuros.espacios_por_nivel`, manteniendo los mismos totales finales.

Desglose aplicado:
- `base_clase`
- `bonificacion_atributo_clave`
- `bonificacion_escuela_especialista`
- `total`

Aclaraciones regladas añadidas a la ficha:
- Los trucos de nivel `0` se preparan a diario, pero no se consumen al lanzarlos.
- El espacio adicional de especialista empieza en nivel de conjuro `1`, no en `0`, y debe usarse con conjuros de `Conjuración`.

Fuente reglada utilizada:
- `Reglamento básico`, tabla de conjuros diarios del mago y regla de espacio adicional del mago especialista.

## 2026-05-04

### Netheros

Se normalizó `ficha_netheros.yaml` a un esquema YAML estable bajo `personaje`, que desde entonces sirve como referencia de estilo para personajes de la campaña.

Detalles relevantes fijados en la normalización:
- `Artesanía (escultura)` quedó expresada como `5` rangos + `3` por habilidad de clase.
- `Saber (ingeniería)` conservó el `+8` heredado del YAML previo, pero quedó marcado con notas porque el usuario indicó que ese origen no aparece en la ficha física.

### Inventario de Netheros

Se creó `inventario_netheros.yaml` como fichero separado para riqueza y objetos transportados de Netheros.

Decisiones de esquema y proceso:
- La raíz canónica es `inventario`.
- El fichero separa `riqueza`, `consumibles` y `objetos_varios`.
- `ficha_netheros.yaml` conserva el equipo equipado; el inventario refleja solo mochila, túnica y otras ubicaciones explícitas.
- La riqueza se guarda por totales de moneda (`pp`, `po`, `pa`, `pc`), no como monedas individuales por bolsa o contenedor.

### Jocorax

Se completó la localización al castellano de `ficha_jocorax.yaml` y de la documentación asociada.

Aclaraciones dejadas ya asentadas:
- Jocorax habla `Aurano` como idioma elegido del cuervo familiar.
- El cuervo familiar no habla `Común` por defecto.
- El historial de revisión reglada permanece en `CHANGELOG.md`, no dentro del YAML operativo.

### Grimorio de Netheros

Se generó `grimorio_netheros.yaml` como grimorio canónico de Netheros a partir de los conjuros marcados como conocidos en `SPELLBOOK.xlsx`.

Decisiones de esquema y proceso:
- `SPELLBOOK.xlsx` se usó solo como fuente de migración inicial y dejó de ser necesario después de la conversión.
- El grimorio contiene únicamente conjuros conocidos.
- Cada conjuro conserva `alias_en_ingles`, datos objetivos, `fuente.libro`, `fuente.pagina` cuando pudo verificarse y `verificacion.estado`.
- Los conjuros del `Reglamento básico` se correlacionaron contra el PDF local y se normalizaron al castellano oficial cuando fue posible.
- Los conjuros de `Guía del jugador avanzada` y `Combate definitivo` se correlacionaron con ayuda de `RolRoyce` solo para título y normalización provisional, sin tratar esa web como fuente de verdad.
- La pasada final de normalización dejó el grimorio sin descripciones en inglés y con los campos mecánicos principales unificados en castellano cuando fue posible.
- Después se hizo un saneado estructural adicional para corregir errores de importación que seguían afectando al grimorio canónico y al índice derivado.

Correcciones relevantes del saneado estructural:
- Se eliminaron cabeceras de conjuros adyacentes incrustadas dentro de `descripcion` en múltiples entradas importadas desde PDF.
- Se corrigieron niveles y entradas mal importadas, en especial `Invisibilidad mayor`, `Convocar monstruo III` y `Convocar monstruo IV`.
- Se completaron campos básicos que habían quedado vacíos o mal parseados en conjuros como `Imagen menor`, `Hechizar monstruo`, `Localizar criatura`, `Leer magia` y otros equivalentes.
- Se recuperó la descripción faltante de `Perturbar muertos vivientes`.
- Se normalizaron etiquetas de escuela, tiradas de salvación, resistencia a conjuros, alcances y otros campos objetivos que habían heredado fragmentos de cabeceras del libro.
- Se creó `grimorio_netheros_indice.yaml` como índice compacto, derivado del grimorio canónico, para mejorar la recuperación de conjuros dentro de ChatGPT Projects.

Estado actual del grimorio tras la normalización y el saneado estructural:
- `127` conjuros totales.
- Reparto por nivel: `22` de nivel `0`, `31` de nivel `1`, `34` de nivel `2`, `21` de nivel `3`, `16` de nivel `4` y `3` de nivel `5`.
- `116` con `verificado_pdf_local`.
- `7` con `correlacionado_rolroyce`.
- `4` con `pendiente`.

Pendientes de validación oficial adicional:
- `Haunted Fey Aspect`
- `Negative Reaction`
- `Animal Aspect`
- `Spontaneous Immolation`

### Directrices de campaña

Se amplió `AGENTS.md` para reflejar:
- la separación entre fichas, inventario y grimorio;
- la existencia de un índice derivado del grimorio para ChatGPT Projects;
- la lista cerrada de libros permitidos como fuente de verdad;
- el uso de `RolRoyce` solo como ayuda auxiliar de correlación;
- la política de no commitear PDFs locales, hojas de cálculo de migración ni artefactos temporales de trabajo;
- y la obligación de actualizar `CHANGELOG.md` y `AGENTS.md` cuando un cambio relevante lo requiera.

## 2026-05-03

### Jocorax

Se trasladó fuera de `ficha_jocorax.yaml` el historial de verificación reglada para mantener el YAML como fuente de verdad operativa de la ficha actual.

Fuentes usadas para la corrección:
- `Reglamento básico`, reglas de familiar.
- `Bestiario 1`, estadísticas base del cuervo.

Supuestos e inferencias aplicados:
- El mordisco usa el BBA del amo, la Destreza del cuervo y el modificador de tamaño `Menudo`.
- Las habilidades usan los mejores rangos entre Netheros y el cuervo base.
- El idioma adicional del cuervo familiar elegido por el amo es `Aurano`.
- El cuervo familiar no habla `Común` por defecto; habla un único idioma a elección de su amo.

Elementos confirmados frente al cuervo base y al familiar actual:
- `FUE 2`, `DES 15`, `CON 8`, `SAB 15` y `CAR 7`.
- Iniciativa `+2`.
- Velocidad terrestre `10 pies`.
- Velocidad de vuelo `40 pies (maniobrabilidad regular)`.
- Daño del mordisco `1d3-4`.
- `DMC 10`.
- `Visión en la penumbra`.

Correcciones aplicadas a la ficha:

| Campo | Valor anterior | Valor corregido | Motivo |
| --- | --- | --- | --- |
| Inteligencia | `7` | `10` | A nivel efectivo 9, la Inteligencia del familiar pasa a 10. |
| Puntos de golpe | `20` | `33` | Un familiar tiene la mitad de los PG totales del amo; Netheros tiene 66. |
| CA | `16 / 16 / 14` | `19 / 14 / 17` | El cuervo base es `Menudo` (+2) y a nivel 9 recibe `+5` de armadura natural adicional. |
| Ataque base | `+2` | `+4` | El familiar usa el BBA del amo. |
| Mordisco | `+4 (1d3-4)` | `+8 (1d3-4)` | Usa el BBA del amo, la Destreza del cuervo y el modificador de tamaño `Menudo`. |
| Salvaciones | `FOR +1, REF +4, VOL +6` | `FOR +2, REF +5, VOL +8` | Usa la mejor base entre el familiar y el amo y añade sus modificadores de atributo propios. |
| Maniobras | `BMC 2, DMC 10` | `BMC 4, DMC 10` | Las criaturas `Menudas` usan Destreza para BMC y aplican el modificador especial de tamaño `-2`. |
| Habilidades | Rangos físicos anotados | Totales reglados `Acrobacias +2`, `Nadar +2`, `Percepción +9`, `Sigilo +10`, `Trepar +2`, `Volar +12` | Los totales reglados usan los mejores rangos entre el cuervo base y Netheros, más modificadores propios, tamaño y dotes. |
| Dotes/capacidades | Mezcladas en una sola lista | Separadas entre dotes base del cuervo, beneficios al amo y capacidades del familiar | La ficha física mezclaba dotes base con capacidades obtenidas por ser familiar de nivel 9. |

Clasificación reglada final:
- Dotes base del cuervo: `Soltura con habilidad (Percepción)`, `Sutileza con las armas`.
- Beneficios al amo: `Alerta`, `Cuervo familiar (+3 a Tasación)`.
- Capacidades del familiar: `Evasión mejorada`, `Compartir conjuros`, `Vínculo de empatía`, `Transmitir conjuros de toque`, `Hablar con el amo`, `Hablar con aves`, `Hablar Aurano`.
