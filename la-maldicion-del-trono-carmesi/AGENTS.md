# AGENTS.md

## Alcance

Estas directrices aplican a `la-maldicion-del-trono-carmesi/` y a sus subdirectorios.

No deben asumirse como reglas globales del repositorio completo. Otras campañas pueden usar otros sistemas, otros idiomas o convenciones distintas.

## Objetivo

Un agente de IA que trabaje en este directorio debe mantener fichas, notas y documentación de campaña de forma consistente, verificable y alineada con Pathfinder 1.ª edición cuando proceda.

## Principios de trabajo

- La ficha operativa actual debe vivir en YAML.
- El YAML debe ser la fuente de verdad del estado actual, no del historial.
- El historial de correcciones, migraciones o decisiones debe ir en `CHANGELOG.md`, no incrustado dentro de la ficha.
- Si una ficha física contradice las reglas oficiales de Pathfinder 1.ª edición, prevalecen las reglas oficiales.
- Si un dato no está en la ficha física pero puede derivarse de reglas oficiales o de otros valores ya confirmados, puede inferirse.
- Si un dato no está confirmado ni puede derivarse con seguridad, no debe inventarse: hay que preguntarlo o dejarlo fuera.

## Idioma

- El idioma por defecto en esta campaña es castellano.
- Las claves del YAML, los nombres de secciones, las notas y la documentación auxiliar deben escribirse en castellano.
- Los nombres propios del juego pueden mantenerse en su forma habitual si eso evita ambigüedad.
- Si un valor estaba en inglés y existe un equivalente claro en castellano, debe normalizarse al castellano.

## Convenciones para fichas YAML

- La raíz del fichero debe ser `personaje`.
- Usar una estructura homogénea y estable entre fichas comparables.
- No perder información al normalizar un fichero. Si una reestructuración mueve contenido, debe conservarse en el nuevo esquema o trasladarse explícitamente al `CHANGELOG.md`.
- Preferir nombres de bloques como:
  - `identidad`
  - `clase` o `familiar`, según corresponda
  - `atributos`
  - `combate`
  - `salvaciones`
  - `lanzamiento_de_conjuros`, si aplica
  - `aptitudes`
  - `equipo`
  - `habilidades`
  - `idiomas`
- En atributos, usar `valor` y `modificador`.
- En secciones numéricas derivadas, usar nombres explícitos como `base`, `bonificadores`, `modificador_atributo`, `subtotal` y `total`.
- En `clase_de_armadura`, desglosar al menos `base`, `bonificadores`, `total`, `toque` y `desprevenido`.
- En habilidades, mantener un formato consistente por habilidad:
  - `atributo`
  - `rangos` cuando aplique
  - `subtotal` si hay suma intermedia útil
  - `bonificadores`
  - `modificador_atributo`
  - `total`
- Las listas de dotes y capacidades deben distinguir, cuando sea relevante, entre dotes base, capacidades de clase, capacidades de familiar y beneficios al amo.
- Las unidades deben expresarse de forma legible y consistente, por ejemplo `10 pies`, `40 pies`, `20 pies`.

## Pathfinder 1.ª edición

- Cuando una ficha dependa de reglas de Pathfinder 1.ª edición, usar fuentes oficiales de esa edición para corregir o completar valores.
- En esta campaña, las únicas fuentes de verdad permitidas son los libros aprobados explícitamente para `la-maldicion-del-trono-carmesi/`.
- No mezclar reglas caseras con reglas oficiales sin dejarlo explícito.
- Si una corrección reglada modifica números de una ficha física, actualizar la ficha operativa y registrar el cambio en `CHANGELOG.md`.
- Si una capacidad, idioma, bonificador o estadística se deduce por reglas de familiar, clase, dote o equipo, debe quedar reflejado de forma clara en la ficha final.

### Libros permitidos como fuente de verdad

Solo puede usarse contenido que esté en alguno de estos libros:

- `Reglamento básico`
- `Combate definitivo`
- `Bestiario 1`
- `Guía del jugador avanzada`
- `Bestiario 2`
- `Guía del mar interior`
- `La maldición del trono carmesí`
- `Magia definitiva`

Todo lo que no esté en esos libros queda fuera del canon utilizable para esta campaña y no debe emplearse para completar, corregir o justificar fichas, reglas, objetos, dotes, conjuros, criaturas, capacidades o trasfondo.

## Convenciones específicas ya fijadas en esta campaña

- `ficha_netheros.yaml` usa un esquema normalizado y sirve como referencia principal de estilo para personajes.
- `ficha_jocorax.yaml` usa el mismo enfoque, adaptado a un familiar.
- En familiares:
  - usar una sección `familiar` para la relación con el amo y las reglas base aplicadas;
  - separar beneficios para el amo de capacidades propias del familiar cuando aporte claridad;
  - aplicar reglas oficiales aunque la ficha física original discrepe.
- `CHANGELOG.md` de esta campaña recoge el historial de cambios significativos sobre las fichas.

## Flujo recomendado al editar

1. Leer la ficha actual y cualquier entrada relevante en `CHANGELOG.md`.
2. Identificar si el cambio es:
   - transcripción de datos,
   - normalización de esquema,
   - corrección reglada,
   - o ampliación con datos derivados.
3. Mantener la ficha YAML limpia como estado actual.
4. Mover explicaciones históricas, discrepancias y correcciones largas a `CHANGELOG.md`.
5. Si hay una discrepancia entre papel y reglas, corregir el YAML a la versión reglada y documentar el ajuste en el changelog.

## Verificación mínima tras cambios

- Validar que el YAML parsea correctamente.
- Revisar que no se haya perdido información relevante durante la normalización.
- Comprobar que los totales calculados siguen siendo coherentes con sus desgloses.
- Si se han tocado reglas de Pathfinder, revisar que la corrección esté alineada con la regla oficial aplicable.

## Qué evitar

- No dejar secciones históricas extensas dentro del YAML operativo.
- No mezclar castellano e inglés sin motivo.
- No conservar valores erróneos solo por fidelidad a la ficha física si contradicen reglas oficiales.
- No cambiar el esquema de una ficha de forma arbitraria si rompe la consistencia con el resto de fichas de la campaña.
- No borrar información sin reubicarla cuando una normalización requiera moverla.
