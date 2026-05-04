# AGENTS.md

## Alcance

Estas directrices aplican a `la-maldicion-del-trono-carmesi/` y a sus subdirectorios.

No deben asumirse como reglas globales del repositorio completo. Otras campañas pueden usar otros sistemas, otros idiomas o convenciones distintas.

## Objetivo

Un agente de IA que trabaje en este directorio debe mantener fichas, notas y documentación de campaña de forma consistente, verificable y alineada con Pathfinder 1.ª edición cuando proceda.

## Artefactos canónicos de campaña

- `ficha_netheros.yaml` y `ficha_jocorax.yaml` son las fichas operativas actuales.
- `inventario_netheros.yaml` es el inventario operativo de Netheros para riqueza y objetos transportados.
- `grimorio_netheros.yaml` es el grimorio operativo y canónico de Netheros.
- `grimorio_netheros_indice.yaml` es un índice derivado y compacto del grimorio, pensado para recuperación rápida en ChatGPT Projects.
- `CHANGELOG.md` recoge el historial significativo de correcciones, migraciones y decisiones sobre fichas, inventario y grimorio.
- `AGENTS.md` fija las reglas de trabajo específicas de esta campaña.

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

- En fichas de personaje y familiar, la raíz del fichero debe ser `personaje`.
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

## Convenciones para inventarios YAML

- La raíz del fichero debe ser `inventario`.
- El inventario solo recoge riqueza y objetos transportados; el equipo equipado sigue en la ficha del personaje.
- Usar `riqueza` con totales por moneda: `pp`, `po`, `pa`, `pc`.
- Usar listas separadas para `consumibles` y `objetos_varios`.
- Cada objeto debe incluir `nombre`, `cantidad` y `ubicacion`.
- `notas` debe usarse solo cuando aporte información mecánica o logística útil, y preferiblemente como lista de cadenas.
- Las ubicaciones deben escribirse en castellano y de forma simple, por ejemplo `tunica`, `mochila` o `casa`.
- No añadir peso, carga, valor detallado ni contenedores anidados salvo petición explícita del usuario.

## Convenciones para grimorios YAML

- La raíz del fichero debe ser `grimorio`.
- El grimorio solo contiene conjuros conocidos; no guarda preparaciones diarias ni presets.
- La lista `conjuros` debe mantenerse ordenada por `nivel` y `nombre`.
- Cada conjuro debe conservar `alias_en_ingles` para trazabilidad con fuentes de importación o correlación.
- Cada conjuro debe registrar datos objetivos de reglas, `fuente.libro`, `fuente.pagina` cuando pueda verificarse, y `verificacion.estado`.
- Los estados de verificación actualmente usados en esta campaña son `verificado_pdf_local`, `correlacionado_rolroyce` y `pendiente`.
- `nombre` debe quedar en castellano cuando exista verificación oficial o correlación fiable; si no hay correlación segura, puede mantenerse temporalmente en inglés.
- Cuando Netheros aprenda un conjuro nuevo, debe añadirse directamente al grimorio desde una fuente oficial permitida.
- `grimorio_netheros_indice.yaml` es derivado, no canónico: debe regenerarse o actualizarse cada vez que cambie materialmente el grimorio.
- El índice derivado debe permanecer alineado con el grimorio en cantidad total de conjuros y reparto por nivel.

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

### Fuentes auxiliares no canónicas permitidas solo como apoyo

- `RolRoyce` puede usarse únicamente como ayuda de correlación o traducción provisional de nombres de conjuros cuando el libro oficial permitido no esté disponible localmente.
- `RolRoyce` no puede usarse como fuente de verdad de texto reglado. Si se utiliza como apoyo, el conjuro debe quedar marcado como `correlacionado_rolroyce` o `pendiente` hasta validación oficial.
- Los PDF locales de libros permitidos pueden usarse para verificación, pero no deben añadirse al repositorio salvo petición explícita del usuario.

## Convenciones específicas ya fijadas en esta campaña

- `ficha_netheros.yaml` usa un esquema normalizado y sirve como referencia principal de estilo para personajes.
- `ficha_jocorax.yaml` usa el mismo enfoque, adaptado a un familiar.
- `inventario_netheros.yaml` usa raíz `inventario`, separa `riqueza`, `consumibles` y `objetos_varios`, y deja el equipo equipado en `ficha_netheros.yaml`.
- `grimorio_netheros.yaml` es el grimorio canónico de Netheros. Usa solo conjuros conocidos y conserva `alias_en_ingles`, `fuente` y `verificacion`.
- `grimorio_netheros_indice.yaml` existe para facilitar consultas en ChatGPT Projects y no sustituye al grimorio canónico.
- En familiares:
  - usar una sección `familiar` para la relación con el amo y las reglas base aplicadas;
  - separar beneficios para el amo de capacidades propias del familiar cuando aporte claridad;
  - aplicar reglas oficiales aunque la ficha física original discrepe.
- `CHANGELOG.md` de esta campaña recoge el historial de cambios significativos sobre fichas, inventario y grimorio.

## Higiene de repositorio

- No commitear PDFs locales de consulta.
- No commitear hojas de cálculo temporales de migración una vez volcada su información al YAML canónico.
- No commitear documentos de especificación o plan generados para trabajo puntual, ni scripts o tests ad hoc de migración, salvo petición explícita del usuario.
- Los ficheros canónicos de campaña deben ser los YAML y Markdown operativos de la propia campaña.

## Mantenimiento documental

- Cuando un cambio modifique de forma relevante una ficha, un inventario, un grimorio o un índice derivado operativo, debe actualizarse `CHANGELOG.md`.
- Cuando un cambio establezca o altere una convención duradera de la campaña, una política de fuentes, una regla de verificación o el papel de un fichero, debe actualizarse también `AGENTS.md`.
- Si el grimorio cambia materialmente, el índice derivado `grimorio_netheros_indice.yaml` debe revisarse o regenerarse en el mismo cambio.

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
6. Si el cambio afecta a inventario o grimorio, mantener separados el estado operativo actual y el historial de migración o revisión.
7. Si se importa información desde una fuente auxiliar no canónica, dejar claro el estado de verificación en el YAML y en el `CHANGELOG.md` cuando el cambio sea significativo.
8. Si el cambio altera reglas de trabajo duraderas de la campaña, actualizar `AGENTS.md` en la misma intervención.

## Verificación mínima tras cambios

- Validar que el YAML parsea correctamente.
- Ejecutar `git diff --check` para evitar espacios sobrantes y otros problemas de formato.
- Revisar que no se haya perdido información relevante durante la normalización.
- Comprobar que los totales calculados siguen siendo coherentes con sus desgloses.
- Si se han tocado reglas de Pathfinder, revisar que la corrección esté alineada con la regla oficial aplicable.
- En grimorios, comprobar además que `fuente.libro`, `verificacion.estado` y `alias_en_ingles` siguen siendo coherentes.
- En grimorios con índice derivado, comprobar además que `grimorio_netheros_indice.yaml` sigue alineado con el grimorio canónico.
- En inventarios, comprobar que el equipo equipado no se haya duplicado dentro del inventario transportado.

## Qué evitar

- No dejar secciones históricas extensas dentro del YAML operativo.
- No mezclar castellano e inglés sin motivo.
- No conservar valores erróneos solo por fidelidad a la ficha física si contradicen reglas oficiales.
- No cambiar el esquema de una ficha de forma arbitraria si rompe la consistencia con el resto de fichas de la campaña.
- No borrar información sin reubicarla cuando una normalización requiera moverla.
- No elevar una fuente auxiliar no canónica a fuente de verdad.
