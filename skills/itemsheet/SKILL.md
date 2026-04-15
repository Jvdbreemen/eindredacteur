---
name: itemsheet
description: Genereer een ingevuld itemsheet voor een audio- of video-item
allowed-tools: Read WebSearch WebFetch
---

Maak een itemsheet voor een audio- of video-productie.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus B)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/genre-eisen.md (genremogelijkheden)

Stel eerst deze verhelderende vragen als ze niet uit de context blijken:
- Wat is het onderwerp?
- Welk format? (reportage, interview, explainer, portret, nieuwsitem)
- Welk medium? (audio/podcast, video, of beide)
- Gewenste duur?
- Publicatiekanaal en doelgroep?
- Deadline?

Pipeline:

1. BASISGEGEVENS
   - Vul de metadata in op basis van de opgegeven informatie

2. INHOUD
   - Formuleer de invalshoek en de kernvraag
   - Beschrijf het verhaal in 3-5 zinnen (de pitch)
   - Benoem de gewenste boodschap of conclusie (als die er is)

3. BRONNEN EN GESPREKSPARTNERS
   - Stel 2-4 bronnen voor (type persoon + waarom relevant)
   - Per bron: welke rol in het item (hoofdpersoon, expert, tegengeluid, ervaringsdeskundige)

4. DRAAIPLAN (video) of OPNAMEPLAN (audio)
   - Per scene of segment: locatie, wie, wat, geschatte duur
   - Bij video: type shots (interview, b-roll, establishing, detail)
   - Bij audio: type geluid (interview, sfeer/ambiance, voice-over, muziek)

5. LOGISTIEK
   - Benodigde afspraken, locaties, apparatuur
   - Aandachtspunten (toestemming, gevoeligheden, toegang)

Output format:

## Itemsheet: [werktitel]

| Veld | Invulling |
|------|-----------|
| Werktitel | [titel] |
| Format | [reportage/interview/explainer/portret/nieuwsitem] |
| Medium | [audio/video/beide] |
| Duur | [geschat] |
| Maker(s) | [naam/namen] |
| Publicatie | [kanaal] |
| Doelgroep | [omschrijving] |
| Deadline | [datum] |

### Invalshoek en kernvraag
[invalshoek + kernvraag in 1-2 zinnen]

### Rode draad
[De narratieve lijn die het item bij elkaar houdt — in 1 zin. Bijv. "We volgen Thijs van repetitie naar podium, met de bergwandeling als metafoor."]

### Pitch
[3-5 zinnen]

### Bronnen en gesprekspartners
| # | Type | Rol in item | Waarom |
|---|------|-------------|--------|
| 1 | [persoon/type] | [hoofdpersoon/expert/tegengeluid] | [motivatie] |
| ... | | | |

### Draaiplan / Opnameplan
| # | Segment | Locatie | Wie | Wat | Duur item | Opnametijd (geschat) | Type shots/geluid |
|---|---------|---------|-----|-----|-----------|---------------------|-------------------|
| 1 | [segment] | [locatie] | [wie] | [wat] | [min] | [min] | [type] |
| ... | | | | | | |

### Logistiek en aandachtspunten
[opsomming]

## Bronstatus
- Lokaal: [n] | Web: [n] | Single-source: [n] | Trainingskennis: [n] | Ongeverifieerd: [n]

## Open verificatiepunten
[Lijst van te checken aannames over locaties, beschikbaarheid van bronnen, feitelijke claims in de pitch, of "Geen open punten"]

Belangrijk: voorgestelde gesprekspartners en locaties zijn voorstellen, geen bevestigde afspraken. Markeer ze als zodanig en verzin geen namen of telefoonnummers.
