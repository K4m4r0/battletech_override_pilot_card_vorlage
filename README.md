# BattleTech Override - Mech-Pilot-Karte

Die Vorlage erzeugt eine Karte im Standard-Trading-Card-Format von **63,5 x 88,9 mm**.

## Profilbild

1. Lege das gewünschte Bild im Ordner `Bilder` ab, zum Beispiel:
   `Bilder/plissken.png`
2. Trage den Dateinamen in `mechpilot_card.tex` ein:

```latex
\newcommand{\PilotImage}{Bilder/plissken.png}
```

Fehlt das Bild, wird automatisch ein Platzhalter angezeigt.

## Pilotendaten ändern

Alle veränderbaren Angaben stehen am Anfang der Datei `mechpilot_card.tex` im Abschnitt `DATEN DER KARTE`.

## Fertigkeiten auswählen

Alle Fertigkeiten und ihre Beschreibungen liegen gesammelt in:

```text
spa_fertigkeiten.tex
```

In der Karten-Vorlage werden nur noch die gewünschten Kurzbefehle eingetragen:

```latex
\newcommand{\AbilityOne}{\RangeMasterLong}
\newcommand{\AbilityTwo}{\SpeedDemon}
```

Name und vollständige Beschreibung werden automatisch aus dem Katalog übernommen.

### Verfügbare Kurzbefehle

**Ab Slot 1**

```latex
\BloodStalker
\ClusterHitter
\Dodge
\EaglesEyes
\EnvironmentalSpecialist
\ForwardObserver
\ManeuveringAce
\MeleeMaster
\MeleeSpecialist
\MultiTasker
\RangeMasterExtreme
\RangeMasterLong
\RangeMasterMedium
\StandAside
```

**Ab Slot 2**

```latex
\Hopper
\JumpingJack
\Marksman
\SpeedDemon
\Swordsman
```

**Ab Slot 3**

```latex
\HotDog
\NaturalGrace
\ObliqueAttacker
\Sniper
```

## Neue Fertigkeit ergänzen

Neue Einträge werden in `spa_fertigkeiten.tex` nach diesem Schema angelegt:

```latex
\DeclareSPA{Kurzname}{Slot}{Anzeigename}{Beschreibung}
```

Beispiel:

```latex
\DeclareSPA{NeueFertigkeit}{2}{Neue Fertigkeit}{%
Hier steht die vollständige Beschreibung.%
}
```

Danach kann sie in der Vorlage so gewählt werden:

```latex
\newcommand{\AbilityOne}{\NeueFertigkeit}
```

## Kompilieren

Im Terminal im Projektordner:

```bash
pdflatex mechpilot_card.tex
```

Das PDF muss beim Drucken mit **100 % / Tatsächliche Größe** ausgegeben werden, damit das Kartenformat erhalten bleibt.
