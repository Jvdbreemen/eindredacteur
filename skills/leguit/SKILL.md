---
name: leguit
description: Leg een begrip uit in standaardformat: korte uitleg, voorbeeld, bron (APA7), verdieping (3 alinea's)
allowed-tools: Read WebSearch WebFetch
---

Leg het gevraagde begrip uit in een vast format. Deze skill werkt strikt: liever stoppen en vragen dan een verzonnen bron leveren.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus A: strikt)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/taal-stijl.md (schrijfstijl)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/bronnen/OVERZICHT.md (om te zien welk lokaal bronbestand het domein dekt)

## Tweetraps procedure

### Trap 1 - Begripscontext bepalen
1. Identificeer het begrip en het vakgebied waarin het gebruikt wordt.
2. Als het begrip meerdere betekenissen heeft: vraag de gebruiker in welke context.
3. Bepaal het domein (journalistiek, ethiek, digitaal, copy editing, mediageschiedenis, etc.).

### Trap 2 - Bronstrategie kiezen
Bepaal aan de hand van OVERZICHT.md of er een lokale bron bestaat die het domein dekt.

**Pad A - Lokaal gedekt:**
Lees het relevante bronbestand uit `references/bronnen/` volledig in. Schrijf de uitleg op basis van die bron. Markeer met `[BRON-LOKAAL: bestand.md]`.

**Pad B - Niet lokaal gedekt, wel webreikbaar:**
Voer WebSearch uit met minimaal twee onafhankelijke geloofwaardige bronnen. Schrijf de uitleg en markeer met `[BRON-WEB: URL, dd-mm-jjjj]`. Als slechts één bron: voeg `[SINGLE-SOURCE]` toe.

**Pad C - Niets gevonden:**
STOP. Lever geen uitleg. Vraag de gebruiker:
- "Ik kan geen betrouwbare bron vinden voor [begrip]. Heb je bronmateriaal dat ik kan gebruiken? Of wil je dat ik dit als algemene trainingskennis geef met `[TRAININGSKENNIS]` markering, in de wetenschap dat dit niet gecontroleerd is?"

Wacht op antwoord. Verzin nooit een referentie.

## Output format

Houd exact dit format aan:

```
## [Begrip]

**Korte uitleg:** [1-2 zinnen, helder, geen jargon]

**Voorbeeld:** [concreet, herkenbaar, bij voorkeur uit journalistiek of media]

**Bron:** [Volledige APA7 referentie, alleen uit een werkelijk geraadpleegde bron] [BRON-TAG]

### Verdieping

[Alinea 1: achtergrond en context, waar komt het vandaan, waarom relevant]

[Alinea 2: werking en toepassing, hoe werkt het in de praktijk]

[Alinea 3: nuance en discussie, kanttekeningen, veelgemaakte fouten, actuele ontwikkelingen]

## Bronnen
[Volledige APA7 lijst van gebruikte bronnen]

## Bronstatus
- Lokaal: [n]
- Web: [n]
- Single-source: [n]
- Trainingskennis: [n]
- Ongeverifieerd: [n]

## Open verificatiepunten
[Lijst, of "Geen open punten."]
```

## Regels

- Altijd exact dit format, geen afwijkingen.
- Journalistieke schrijfstijl: helder, concreet, geen abstractie.
- Bron altijd in APA7 en alleen uit een daadwerkelijk geraadpleegde bron.
- Voorbeeld bij voorkeur uit journalistiek, media, fotografie of aanverwant.
- Verdieping: precies 3 alinea's, niet meer, niet minder.
- Verzin nooit auteurs, jaartallen, titels, paginanummers of citaten.
- Als geen bron beschikbaar is: stop en vraag, lever niet.
