---
name: interviewprep
description: Interview voorbereiding met vragenlijst en research-briefing
allowed-tools: Read WebSearch WebFetch
---

Maak een interviewvoorbereiding voor de opgegeven gesprekspartner en/of onderwerp. Deze skill werkt strikt: research-briefing wordt alleen gegeven als de informatie verifieerbaar is. Geen gokken op CV-gegevens, functies of citaten.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus A: strikt)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/ethiek.md (ethische richtlijnen)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/bronnen/OVERZICHT.md (lokale bronnen voor achtergrond op het onderwerp)

Stel eerst deze verhelderende vragen als ze niet uit de context blijken:
- Wie is de gesprekspartner? (naam, functie, organisatie)
- Wat is het onderwerp of de aanleiding?
- Welk genre wordt het? (nieuwsinterview, portret, achtergrond, confronterend)
- Hoeveel tijd heb je? (5 min, 15 min, 30+ min)
- Publicatiekanaal? (print, online, audio, video)

Pipeline:

1. RESEARCH-BRIEFING (strikt geverifieerd)
   - Zoek via WebSearch naar recente informatie over de gesprekspartner en het onderwerp.
   - Verifieer elk biografisch feit (functie, organisatie, leeftijd, eerdere uitspraken) tegen minimaal twee onafhankelijke bronnen.
   - Bij elke zin in de briefing: zet de bronstatus tag direct achter de zin (`[BRON-WEB: URL, dd-mm-jjjj]` of `[BRON-LOKAAL: bestand.md]`).
   - Geen verifieerbare informatie? STOP de research-briefing en vraag de gebruiker om bronmateriaal of een eigen briefing. Lever geen gegokte feiten over een echt persoon.
   - Samenvatting in max 200 woorden: wie is deze persoon, wat is de actuele context, wat zijn mogelijke gevoeligheden.
   - Noteer alle geraadpleegde bronnen in APA7.

2. VRAGENLIJST
   - Pas het aantal vragen aan op de beschikbare tijd:
     - 5 min: 3-5 vragen (alleen kern)
     - 15 min: 8-10 vragen (opening + kern + afsluiting)
     - 30+ min: 12-15 vragen (alle blokken)
   - Genereer vragen gestructureerd in blokken:
     - **Opening** (1-2 vragen): laagdrempelig, vertrouwen opbouwen
     - **Kern** (5-8 vragen): de inhoudelijke hoofdvragen
     - **Verdieping** (2-3 vragen): doorvragen, tegenwerpen, nuance
     - **Afsluiting** (1-2 vragen): reflectie, vooruitblik, ruimte voor toevoeging
   - Bij elk blok: korte notitie over de intentie (wat wil je hiermee bereiken?)
   - Markeer vragen die gevoelig kunnen liggen met ⚠️
   - Markeer must-ask vragen met ★ (de 3-5 vragen die je sowieso wilt stellen, ook bij tijdnood)

3. DOORVRAAGSUGGESTIES
   - Per kernvraag: 1-2 doorvraagsuggesties voor als het antwoord vaag, ontwijkend of verrassend is
   - Formuleer als: "Als [situatie], vraag dan: [doorvraag]"

4. ETHISCHE AANDACHTSPUNTEN
   - Check op basis van ethiek.md:
     - Kwetsbare gesprekspartner? (minderjarig, slachtoffer, afhankelijke positie)
     - Gevoelige onderwerpen waar informed consent extra van belang is?
     - Privacy-afwegingen: wat publiceer je wel/niet?
   - Noteer concrete aandachtspunten voor dit interview

5. PRAKTISCHE TIPS
   - Genre-specifieke tips (portret: observeer de omgeving; confronterend: bewijs bij de hand)
   - Valkuilen voor dit specifieke interview

Output format:

## Interviewvoorbereiding: [naam gesprekspartner]

### Research-briefing
[max 200 woorden samenvatting + bronnen]

### Vragenlijst
**Opening**
1. [vraag] — *intentie: [korte notitie]*
...

**Kern**
...

**Verdieping**
...

**Afsluiting**
...

### Doorvraagsuggesties
[per kernvraag]

### Ethische aandachtspunten
[concrete aandachtspunten voor dit interview]

### Praktische tips
[genre-specifiek + valkuilen]

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
