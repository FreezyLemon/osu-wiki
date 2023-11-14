---
tags:
  - leadin
  - lead in
  - AudioLeadIn
  - Vorlauf
  - Einleitung
---

# Vorlaufzeit

*Siehe auch: [Offset](/wiki/Offset)*

Die **Vorlaufzeit** ist die Zeit, die vor dem ersten [Hit-Objekt](/wiki/Gameplay/Hit_object) einer [Beatmap](/wiki/Beatmap) eingefügt wird, um dem Spieler mehr Reaktionszeit zu geben. Sie kann von [Mappern](/wiki/Beatmapping) angepasst werden, indem das Feld `AudioLeadIn` in der [`.osu`-Datei](/wiki/Client/File_formats/osu_(file_format)) des jeweiligen [Beatmap-Schwierigkeitsgrads](/wiki/Beatmap/Difficulty) bearbeitet wird. Das Feld gibt die Vorlaufzeit in Millisekunden an.

## Verhalten

Die minimale Vorlaufzeit, die von osu! automatisch vergeben werden kann, beträgt 1,8 Sekunden. Bei der niedrigsten [Approach-Rate](/wiki/Beatmap/Approach_rate) von 0 ist ein Hit-Objekt für diesen Zeitraum sichtbar, bevor es angeklickt werden muss. Ein [Storyboard](/wiki/Storyboard) oder Video, welches vor dem ersten Hit-Objekt beginnt, kann die Vorlaufzeit verlängern.

Wenn eine Epilepsiewarnung eingesetzt wird und die ersten Hit-Objekte einer Beatmap überdeckt, muss die Vorlaufzeit laut [Ranking-Kriterien](/wiki/Ranking_criteria#general) angepasst werden.
