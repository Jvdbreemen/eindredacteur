---
name: transcriptie
description: Transcriptie opschonen en corrigeren naar leesbaar Nederlands
allowed-tools: Read Write Edit WebSearch WebFetch
---

Schoon de aangeleverde transcriptie op naar leesbaar, correct Nederlands.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/SKILL.md
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus B)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/taal-stijl.md

Pipeline:

1. FORMATDETECTIE
   - Herken of het een AI-transcriptie is (Whisper, Otter, Descript), handmatige transcriptie, of platte tekst
   - Herken tijdcodes en sprekerslabels
   - Herken sessieovergangen: als tijdcodes resetten (bijv. van 28:44 terug naar 0:00) is er sprake van meerdere opnamesessies. Markeer elke sessie apart met een duidelijk label (Sessie 1, Sessie 2) en eigen tijdcodereeks
   - Gebruik structuur uit de interview-transcription skill (jamditis) als referentie

2. SPREKERSIDENTIFICATIE
   - Als er "Spreker 1, Spreker 2" labels zijn: zoek in de tekst naar namen, introducties, rolverwijzingen
   - Koppel labels aan namen waar mogelijk
   - Vraag bevestiging als onzeker

3. VOORPRAATJE EN OFF-RECORD PASSAGES
   - Herken niet-inhoudelijke delen: smalltalk, technische setup (camera, microfoon), off-topic gesprekken (politiek, weer, andere projecten) die voor het interview plaatsvinden of tussendoor opduiken
   - Scheid deze van de inhoudelijke interviewpassages
   - Vat het voorpraatje kort samen (1-2 zinnen) maar neem het niet op in de schone transcriptie
   - Let op uitspraken als "dat is misschien niet goed om te publiceren", "off the record", "zet even uit": markeer de bijbehorende passage als potentieel off-record

4. TAALCORRECTIE
   - Corrigeer spelling, grammatica, interpunctie
   - Bij DIRECTE CITATEN: behoud de spreekstijl van de spreker (woordkeuze, toon), verwijder eh's en herhalingen
   - Bij INDIRECTE PASSAGES: herschrijf journalistiek naar correct Nederlands
   - Verwijder false starts en overbodige herhalingen
   - Maak zinnen af die halverwege stoppen (markeer met [aangevuld])

5. STRUCTURERING
   - Verdeel in logische alinea's op basis van onderwerp/thema
   - Behoud tijdcodes als referentie
   - Markeer onverstaanbare passages als [onverstaanbaar, HH:MM:SS]
   - Voeg tussenkopjes toe bij langere transcripties (>1000 woorden)

6. QUOTELIJST (optioneel, lever als de transcriptie interviewmateriaal bevat)
   - Extraheer bruikbare citaten
   - Per citaat: tijdcode, spreker, de quote, en een korte context-notitie
   - Sorteer op nieuwswaarde/bruikbaarheid

7. VERIFICATIELIJST
   Lever een expliciete lijst van punten die de journalist moet controleren:
   - Naamspellingen: vergelijk namen in het transcript met eventueel bijbehorend artikel of andere bronnen. Probeer namen te verifiëren via WebSearch (social media, conservatorium-sites, bandpagina's). Meld afwijkingen tussen transcript en artikel.
   - Feitelijke claims: functies, organisatienamen, opleidingen, locaties die in het transcript worden genoemd
   - Gevoelige passages: persoonlijke onthullingen, medische informatie, uitspraken die de geïnterviewde mogelijk niet gepubliceerd wil zien. Markeer deze met ⚠️ en adviseer de journalist om toestemming te vragen.
   - Onduidelijke verwijzingen: als de spreker zichzelf corrigeert of onzeker is over een feit, markeer dit

Lever:
- Schone transcriptie (sprekersnamen geverifieerd of anders met `[ONGEVERIFIEERD]` markering)
- Lijst van sprekers met identificatie en bronstatus tag per identificatie
- Quotelijst (als interview)
- Verificatielijst

## Bronstatus
- Lokaal: [n] | Web: [n] | Single-source: [n] | Trainingskennis: [n] | Ongeverifieerd: [n]

## Open verificatiepunten
[Lijst, of "Geen open punten"]

Belangrijk: verzin nooit een naam, functie of citaat. Als een naam niet te verifiëren is, hou de oorspronkelijke "Spreker N" label aan en zet het op de verificatielijst.
