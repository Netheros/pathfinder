# Registro de cambios

## 2026-05-03

### Jocorax

Se trasladó fuera de `ficha_jocorax.yaml` el historial de verificación reglada para mantener el YAML como fuente de verdad operativa de la ficha actual.

Fuentes usadas para la corrección:
- `Pathfinder RPG Core Rulebook`, reglas de familiar.
- `Pathfinder RPG Bestiary`, entrada `Familiar, Raven`.

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
