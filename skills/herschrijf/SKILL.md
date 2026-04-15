---
name: herschrijf
description: Herschrijf een tekst voor een ander kanaal, format of doelgroep
allowed-tools: Read Write Edit WebSearch
---

Herschrijf de aangeleverde tekst voor een ander kanaal, format of doelgroep.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus B)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/taal-stijl.md (schrijfstijl)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/genre-eisen.md (genre-eisen)
Raadpleeg de ai-writing-detox skill om AI-patronen te vermijden.

Stel eerst deze verhelderende vragen als ze niet uit de context blijken:
- Wat is het bronmateriaal? (artikel, transcript, persbericht, notities)
- Naar welk kanaal of format? (print → web, lang → kort, tekst → social, vakblad → algemeen publiek)
- Doelgroep? (professional, breed publiek, jongeren, specifieke sector)
- Gewenste lengte?
- Gewenste toon? (zakelijk, persoonlijk, wervend, neutraal)

Pipeline:

1. BRONANALYSE
   - Lees het bronmateriaal volledig
   - Identificeer: kernboodschap, belangrijkste feiten, sterkste citaten, essentiële context
   - Bepaal wat behouden moet blijven (feiten, citaten, nuance) en wat kan vervallen

2. KANAAL-AANPASSING
   - Pas de structuur aan op het doelkanaal:

   | Van → Naar | Structuuraanpassing |
   |-----------|---------------------|
   | Print → Web | Kortere alinea's, tussenkopjes, scanbaar, links waar mogelijk |
   | Lang → Kort | Alleen kern behouden, bijzaken schrappen, max 300 woorden |
   | Vakblad → Algemeen | Jargon vervangen, context toevoegen, concreter |
   | Tekst → Audio-intro | Spreektaal, korte zinnen, 150 woorden/min, hook in eerste zin |
   | Persbericht → Artikel | Omschrijven naar journalistiek, hoor/wederhoor toevoegen, PR-taal verwijderen |

3. HERSCHRIJVEN
   - Behoud de feiten en citaten uit het origineel
   - Pas toon, lengte, structuur en woordkeuze aan
   - Schrijf een nieuwe lead passend bij het doelkanaal
   - Controleer of de kernboodschap intact is
   - Tel het resultaat en vermeld het woordenaantal expliciet

4. VERGELIJKING
   - Korte vergelijking origineel vs. herschreven versie:
     - Wat is behouden?
     - Wat is geschrapt en waarom?
     - Wat is toegevoegd?

Regels:
- De herschreven versie moet op eigen benen staan. De lezer/luisteraar kent het origineel niet.
- Behoud de feitelijke correctheid. Geen feiten toevoegen die niet in het origineel staan.
- Behoud citaten letterlijk, tenzij ingekort (markeer met [...])
- Geen AI-schrijfpatronen: raadpleeg ai-writing-detox

Output format:

## Herschreven versie: [werktitel]

**Origineel:** [bron, genre, lengte]
**Herschreven voor:** [kanaal, doelgroep, format]
**Lengte:** [woordenaantal]

[Herschreven tekst]

### Wijzigingsoverzicht
| Element | Origineel | Herschreven | Reden |
|---------|-----------|-------------|-------|
| Lead | [omschrijving] | [omschrijving] | [motivatie] |
| Structuur | [omschrijving] | [omschrijving] | [motivatie] |
| Toon | [omschrijving] | [omschrijving] | [motivatie] |
| Geschrapt | [wat] | — | [motivatie] |
| Toegevoegd | — | [wat] | [motivatie] |

## Bronstatus
- Lokaal: [n] | Web: [n] | Single-source: [n] | Trainingskennis: [n] | Ongeverifieerd: [n]

## Open verificatiepunten
[Lijst, of "Geen open punten"]

Belangrijk: voeg geen feiten of citaten toe die niet in het origineel staan. Herschrijven betekent transformeren, niet uitbreiden. Als context ontbreekt en aanvulling nodig is: vraag de gebruiker eerst.
