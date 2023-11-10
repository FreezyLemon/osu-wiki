---
tags:
  - accuracy
  - hit window
  - OD
  - spinner difficulty
---

# Overall Difficulty

*Für empfohlene OD-Werte, siehe: [Ranking-Kriterien](/wiki/Ranking_criteria)*

Die **Overall Difficulty** (***OD***) bestimmt, wie schwer eine hohe [Genauigkeit](/wiki/Gameplay/Accuracy) in einer [Beatmap](/wiki/Beatmap) erspielbar ist. Der OD-Wert liegt zwischen 0 und 10, und ein höherer Wert bedeutet, dass mehr Genauigkeit und Präzision erforderlich sind. Da eine hohe Genauigkeit auch für das Erhalten von [Gesundheit](/wiki/Gameplay/Health) wichtig ist, wird es durch eine höhere OD schwieriger, eine Beatmap erfolgreich zu beenden.

## Timing

Ein höherer OD-Wert führt dazu, dass die Zeitfenster sowohl zum Anklicken eines [Hit-Objektes](/wiki/Gameplay/Hit_object) überhaupt als auch zum Erreichen hoher [Punktzahlen](/wiki/Gameplay/Score) kleiner werden. Die maximal erlaubte zeitliche Abweichung vom korrekten Zeitpunkt eines Hit-Objektes in den Spielmodi [osu!](/wiki/Game_mode/osu!) und [osu!mania](/wiki/Game_mode/osu!mania) wird in den folgenden Tabellen definiert.

Man beachte, dass diese Zeitfenster in der stable-Version von osu! in den Spielmodi osu! und [osu!taiko](/wiki/Game_mode/osu!taiko) am Anfang und Ende jeweils bis zu 0.5 ms kürzer sein können als in den Formeln angegeben. In osu!mania kann das Zeitfenster am Anfang und Ende jeweils bis zu 0.5 ms größer sein. Dies liegt an technischen Unterschieden zwischen den Spielmodi; in osu! und osu!taiko ist ein Klick gültig, solange `abweichung < gerundet(zeitfenster)` gilt, während die Voraussetzung in osu!mania `abweichung <= gerundet(zeitfenster)` ist.[^judgement-rounding-ref]

Zum Beispiel ist das Zeitfenster für ein Great in osu!taiko bei einem OD-Wert von 5 (kurz: OD 5) ±34.5 ms statt des Tabellenwertes ±35 ms. In osu!mania ist das Zeitfenster für ein MAX ±16.5 ms, nicht ±16 ms.

Die korrekten Zeitfenster für die Bewertung von Hit-Objekten können immer eingesehen werden, indem man mit dem Cursor über die [Beatmap-Informationen in der Songauswahl](/wiki/Client/Interface#beatmap-informationen) fährt.

### osu!

| Bewertung | Zeitfenster (ms) |
| --: | :-- |
| 300 | `80 - 6 * OD` |
| 100 | `140 - 8 * OD` |
| 50 | `200 - 10 * OD` |

![](/wiki/shared/ODTable.png "Vergleich von verschiedenen Kombinationen aus OD-Werten und Spielmodifikationen. Für Kombinationen mit Half Time und Double Time gilt, dass die angezeigten OD-Werte nur für 300er-Bewertungen gültig sind und für 50er und 100er unterschiedlich wären.")

### osu!taiko

| Bewertung | Zeitfenster (ms) |
| --: | :-- |
| Great |  `35 - (35 - 50) * (5 - OD) / 5` wenn OD < 5, `35 + (20 - 35) * (OD - 5) / 5` wenn OD > 5, sonst `35` |
| Ok | `80 - (80 - 120) * (5 - OD) / 5` wenn OD < 5, `80 + (50 - 80) * (OD - 5) / 5` wenn OD > 5, sonst `80` |
| Miss | `95 - (95 - 135) * (5 - OD) / 5` wenn OD < 5, `95 + (70 - 95) * (OD - 5) / 5` wenn OD > 5, sonst `95` |

### osu!mania

| Bewertung | Zeitfenster (ms) |
| --: | :-- |
| MAX | `16` |
| 300 | `64 - 3 * OD` |
| 200 | `97 - 3 * OD` |
| 100 | `127 - 3 * OD` |
| 50 | `188 - 3 * OD` |

Wenn der Spieler außerhalb des 50er-Zeitfensters klickt, wird das Objekt als Miss bewertet. Sollten sich die Zeitfenster von zwei Hit-Objekten überlappen, kann das zweite Hit-Objekt wegen [Notelock](/wiki/Gameplay/Judgement/Notelock) nicht angeklickt werden, bis das erste verschwindet.

## Sliders und Spinners

In [osu!](/wiki/Game_mode/osu!) werden [Slider](/wiki/Gameplay/Hit_object/Slider) mit einer 300 bewertet, solange sie im 50er-Zeitfenster angeklickt werden. Dieses Verhalten wird manchmal "Slider leniency" genannt und wurde in [ScoreV2](/wiki/Gameplay/Game_modifier/ScoreV2) entfernt.

Die Overall Difficulty wirkt sich auch auf [Spinner](/wiki/Gameplay/Hit_object/Spinner) aus. Ein höherer OD-Wert führt dazu, dass ein Spinner häufiger gedreht werden muss. In [osu!taiko](/wiki/Game_mode/osu!taiko) benötigt das denden bei einem höheren OD-Wert mehr Schläge <!-- TODO: double-check the preceding sentence --> Die pro Sekunde benötigten Umdrehungen lassen sich durch die folgende Formel berechnen:

- OD < 5: `5 - 2 * (5 - OD) / 5`
- OD = 5: `5`
- OD > 5: `5 + 2.5 * (OD - 5) / 5`

## Auswirkungen von Mods auf die OD

Es gibt vier [Mods](/wiki/Gameplay/Game_modifier), die sich auf die OD auswirken:

- [Easy](/wiki/Gameplay/Game_modifier/Easy) halbiert den OD-Wert.
- [Hard Rock](/wiki/Gameplay/Game_modifier/Hard_Rock) multipliziert den OD-Wert mit 1.4 bis maximal 10.
- [Double Time](/wiki/Gameplay/Game_modifier/Double_Time) ändert den OD-Wert nicht. Da die Spielgeschwindigkeit um 50% erhöht wird, sind alle Zeitfenster aber um 33% kleiner.
- [Half Time](/wiki/Gameplay/Game_modifier/Half_Time) ändert den OD-Wert nicht. Da die Spielgeschwindigkeit um 25% verringert wird, sind alle Zeitfenster aber um 33% größer.

Half Time und Double Time ändern zwar nicht den OD-Wert, aufgrund der Geschwindigkeitsänderung wirken sie sich aber auf die Zeitfenster aus. Da die Skalierung der Zeitfenster mit dem OD-Wert für jede Bewertung (50, 100, 300) unterschiedlich ist, führt DT für die Bewertungen 50 und 100 zu unerwartet kleinen (strengen) Zeitfenstern, während HT zu unerwartet großen (einfachen) Zeitfenstern führt.

## osu!catch

Der OD-Wert ist in den Beatmap-Informationen sichtbar, hat aber keine Auswirkungen aufs Gameplay.

## Anmerkungen

[^judgement-rounding-ref]: [Discord-Nachricht von spaceman_atlas (2022-05-06) in #osu-wiki im osu!-Discordserver](https://discord.com/channels/188630481301012481/218677502141399041/972241866382798889)
