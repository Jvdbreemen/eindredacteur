---
name: invalshoek
description: Genereer 3-5 invalshoeken met pitch-varianten voor een onderwerp
allowed-tools: Read WebSearch WebFetch
---

Genereer invalshoeken en pitch-varianten voor het opgegeven onderwerp.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus B: markeer en lever af)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/genre-eisen.md (genremogelijkheden)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/bronnen/OVERZICHT.md (om relevante lokale bron te kiezen)

Stel eerst deze verhelderende vragen als ze niet uit de context blijken:
- Wat is het onderwerp of de aanleiding?
- Voor welke publicatie of redactie is het bedoeld?
- Zijn er formats of genres waar je aan denkt? (tekst, audio, video, combinatie)
- Deadline?

Pipeline:

1. ONDERWERP-ANALYSE
   - Volg de bronvolgorde uit verificatie.md: lokaal eerst (OVERZICHT.md), web tweede.
   - Zoek via WebSearch naar actuele context rond het onderwerp. Verifieer minimaal twee onafhankelijke bronnen per claim.
   - Identificeer: wat is er al over geschreven of gemaakt? Waar zit de witte vlek?
   - Noteer 2-3 actuele ontwikkelingen die als aanleiding kunnen dienen, elk met een bronstatus tag.
   - Vermeld bronnen in APA7 (auteur, jaar, titel, uitgever of URL met datum). Verzin nooit een referentie. Bij twijfel: markeer met `[ONGEVERIFIEERD]` en zet de claim op de lijst Open verificatiepunten.

2. INVALSHOEKEN
   - Genereer 3-5 invalshoeken, elk vanuit een ander perspectief:
     - Persoonlijk/menselijk (wie wordt geraakt?)
     - Systemisch/structureel (welk groter probleem speelt hier?)
     - Data/cijfers (wat zeggen de getallen?)
     - Historisch/vergelijkend (is dit eerder gebeurd? hoe zit het elders?)
     - Toekomstgericht (wat staat er op het spel?)
   - Niet elke categorie is altijd relevant. Kies de 3-5 sterkste.

3. PITCH-VARIANTEN
   - Per invalshoek een pitch van 2-3 zinnen:
     - Zin 1: de kern (wat is het verhaal?)
     - Zin 2: de relevantie (waarom nu, waarom hier?)
     - Zin 3: de aanpak (welk genre, welke bronnen, welk format?)
   - Suggereer per pitch het meest geschikte genre en format

4. BRONNENVOORSTEL
   - Per invalshoek: 2-3 mogelijke bronnen (type persoon, niet per se naam)
   - Suggesties voor data of documenten die het verhaal kunnen onderbouwen

Output format:

## Invalshoeken: [onderwerp]

### Actuele context
[2-3 zinnen + bronnen]

### Invalshoek 1: [titel]
**Perspectief:** [persoonlijk / systemisch / data / historisch / toekomst]
**Pitch:** [2-3 zinnen]
**Genre/format:** [suggestie]
**Mogelijke bronnen:** [2-3 suggesties]
**Haalbaarheid bronnen:** [makkelijk/gemiddeld/lastig benaderbaar + korte toelichting]

### Invalshoek 2: [titel]
...

### Aanbeveling
[Welke invalshoek is het sterkst en waarom? Welke combinatie levert het rijkste verhaal op?]

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
