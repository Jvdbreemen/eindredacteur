---
name: montage
description: Montage-opbouw en shotlist op basis van script of itemsheet
allowed-tools: Read Write Edit
---

Maak een montage-opbouw en shotlist op basis van een aangeleverd script, itemsheet of ruwe beschrijving.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus B)

Stel eerst deze verhelderende vragen als ze niet uit de context blijken:
- Is er een script of itemsheet beschikbaar?
- Welk format? (reportage, portret, explainer, nieuwsitem)
- Gewenste duur?
- Is het materiaal al opgenomen, of is dit voorbereiding voor een draaidag?
- Welke apparatuur is beschikbaar? (camera, drone, audio)

Pipeline:

1. MATERIAAL ANALYSE
   - Lees het aangeleverde script, itemsheet of beschrijving
   - Inventariseer beschikbare elementen: interviews, b-roll, sfeerbeelden, grafiek, tekst-op-beeld, muziek
   - Identificeer ontbrekende elementen die nog opgenomen of gemaakt moeten worden

2. MONTAGE-OPBOUW
   - Vertaal het script naar een visuele/auditieve structuur
   - Per segment: wat ziet/hoort de kijker, hoe lang, welk tempo
   - Let op ritme: wissel tussen voice-over, citaat, sfeer, stilte
   - Let op spanningsboog: opbouw naar een kern of climax, daarna afronding
   - Markeer overgangen: harde cut, crossfade, fade to black, J-cut, L-cut

3. SHOTLIST (als voorbereiding voor draaidag)
   - Per locatie: welke shots zijn nodig
   - Per shot: type (wide/medium/close-up/detail), onderwerp, beweging (statisch/pan/tilt/tracking), doel in montage
   - Prioriteer: welke shots zijn essentieel, welke zijn nice-to-have
   - Groepeer per locatie voor efficiënt draaien

4. TECHNISCHE NOTEN
   - Framerate en resolutie suggesties indien relevant
   - Audio-aandachtspunten (windgeluid, galm, omgevingsgeluid)
   - Audio-mixsuggesties: geef per segmenttype een indicatie van de verhouding (bijv. "VO prominent, muziek -12dB", "nat. geluid vol, geen VO", "citaat vol, sfeer zacht onder")
   - Grafiek of tekst-op-beeld die gemaakt moet worden

Output format:

## Montage-opbouw: [werktitel]

**Format:** [type]
**Geschatte duur:** [minuten]

### Montage-structuur

| # | Tijdcode | Segment | Beeld | Geluid | Duur | Overgang |
|---|----------|---------|-------|--------|------|----------|
| 1 | 0:00 | Opening | [omschrijving] | [omschrijving] | 0:15 | — |
| 2 | 0:15 | Intro voice-over | [omschrijving] | [VO + sfeer] | 0:20 | Cut |
| ... | | | | | | |

### Shotlist

| # | Locatie | Type shot | Onderwerp | Beweging | Doel in montage | Prioriteit |
|---|---------|-----------|-----------|----------|-----------------|------------|
| 1 | [locatie] | Wide | [onderwerp] | Statisch | Establishing | Essentieel |
| 2 | [locatie] | Close-up | [onderwerp] | Tracking | B-roll detail | Nice-to-have |
| ... | | | | | | |

### Ontbrekend materiaal
[Lijst van elementen die nog opgenomen, gemaakt of aangeleverd moeten worden]

### Technische noten
[Audio, grafiek, overige aandachtspunten]

## Bronstatus
- Materiaal werkelijk beschikbaar volgens aanlevering: [n shots/segmenten]
- Materiaal aangenomen of nog op te nemen: [n]

## Open verificatiepunten
[Lijst van aannames over beschikbaar materiaal die de gebruiker zelf moet bevestigen, of "Geen open punten"]

Belangrijk: verzin geen shots die er niet zijn. Als materiaal ontbreekt: meld het in "Ontbrekend materiaal", maak het niet "alsof".
