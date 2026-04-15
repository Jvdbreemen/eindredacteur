---
name: script
description: Schrijf een voicetrack of scriptvoorstel voor audio of video
allowed-tools: Read Write Edit WebSearch WebFetch
---

Schrijf een voicetrack of scriptvoorstel op basis van aangeleverd materiaal.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus B: markeer en lever af)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/taal-stijl.md (schrijfstijl)

Stel eerst deze verhelderende vragen als ze niet uit de context blijken:
- Welk medium? (audio/podcast of video)
- Welk format? (reportage, explainer, portret, nieuwsitem)
- Gewenste duur? (dit bepaalt de woordentelling: ~150 woorden per minuut voor voice-over)
- Is er een itemsheet of invalshoek beschikbaar?
- Welke bronnen/citaten zijn beschikbaar? (transcript, artikel, notities)
- Toon? (zakelijk, persoonlijk, verhalend)

Pipeline:

1. MATERIAAL INVENTARISEREN
   - Lees het aangeleverde materiaal (transcript, artikel, notities, itemsheet)
   - Identificeer bruikbare citaten, feiten, scenes
   - Bepaal de verhaallijn: wat is het begin, het midden, het einde?

2. STRUCTUUR BEPALEN
   - Kies een structuur passend bij het format:
     - **Nieuwsitem:** kern → context → citaat → achtergrond → slot
     - **Reportage:** scene → context → ontwikkeling → reflectie → kicker
     - **Explainer:** vraag → uitleg stap 1 → stap 2 → stap 3 → conclusie
     - **Portret:** beeld → introductie → verhaal → reflectie → kicker
   - Bereken de woordentelling op basis van gewenste duur (~150 woorden/min)

3. SCRIPT SCHRIJVEN
   - Schrijf in twee kolommen:
     - Links: BEELD (video) of GELUID (audio) — wat ziet/hoort de kijker/luisteraar
     - Rechts: TEKST — voice-over of presentatietekst
   - Markeer citaten/inserts apart: [CITAAT: spreker, tijdcode indien bekend]
   - Markeer sfeergeluid/ambiance: [SFX: omschrijving]
   - Markeer muziek: [MUZIEK: omschrijving of verwijzing]
   - Markeer bewuste stilte/pauze: [PAUZE: duur] — gebruik als vertelmiddel na emotionele momenten of voor tempo
   - Schrijf voor het oor: korte zinnen, actief, concreet, geen bijzinnen
   - Spreektaal, geen schrijftaal: "drieduizend" niet "3.000"

4. TIMING
   - Geef per segment een geschatte duur
   - Tel het totaal op en check tegen de gewenste duur
   - Pas aan als het te lang of te kort is

Regels:
- Voice-overtekst is geen artikel. Schrijf alsof je het hardop vertelt.
- Laat ruimte voor citaten en sfeer. Een script dat alleen uit voice-over bestaat is te vol.
- Vuistregel: minimaal 30% van de duur moet citaat, sfeer of beeld zonder voice-over zijn
- Wees specifiek in beeldbeschrijvingen: niet "beelden van de stad" maar "wide shot van de Rijn bij de Arnhemse kade, ochtendlicht"
- **Feitendiscipline:** elke feitelijke uitspraak in de voice-over moet komen uit het aangeleverde materiaal of een geverifieerde bron. Verzin geen cijfers, namen, jaartallen, locaties of citaten. Markeer onverifieerde claims met `[ONGEVERIFIEERD]` en zet ze op de lijst Open verificatiepunten.
- Citaten alleen letterlijk uit het aangeleverde transcript of materiaal. Geen bijgemaakte of gladgestreken quotes.

Output format:

## Script: [werktitel]

**Format:** [reportage/explainer/portret/nieuwsitem]
**Medium:** [audio/video]
**Geschatte duur:** [minuten]
**Woordentelling voice-over:** [aantal]

| # | Duur | Beeld/Geluid | Tekst |
|---|------|-------------|-------|
| 1 | 0:00-0:15 | [omschrijving] | [voice-over of aanwijzing] |
| 2 | 0:15-0:30 | [CITAAT: spreker] | "[citaat]" |
| 3 | 0:30-0:45 | [SFX: ambiance] | — |
| ... | | | |

### Noten
[Opmerkingen over ontbrekend materiaal, alternatieve structuur, suggesties]

## Bronnen
[Volledige APA7 lijst van gebruikte bronnen, indien van toepassing]

## Bronstatus
- Lokaal: [n]
- Web: [n]
- Single-source: [n]
- Trainingskennis: [n]
- Ongeverifieerd: [n]

## Open verificatiepunten
[Lijst van feitelijke claims die de gebruiker zelf moet checken, of "Geen open punten."]
