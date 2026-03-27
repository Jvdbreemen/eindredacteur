---
description: Transcriptie opschonen en corrigeren naar leesbaar Nederlands
allowed-tools: Read, Write, Edit
---

Schoon de aangeleverde transcriptie op naar leesbaar, correct Nederlands.

Laad de eindredacteur skill uit ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/SKILL.md en
raadpleeg ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/taal-stijl.md.

Pipeline:

1. FORMATDETECTIE
   - Herken of het een AI-transcriptie is (Whisper, Otter, Descript), handmatige transcriptie, of platte tekst
   - Herken tijdcodes en sprekerslabels
   - Gebruik structuur uit de interview-transcription skill (jamditis) als referentie

2. SPREKERSIDENTIFICATIE
   - Als er "Spreker 1, Spreker 2" labels zijn: zoek in de tekst naar namen, introducties, rolverwijzingen
   - Koppel labels aan namen waar mogelijk
   - Vraag bevestiging als onzeker

3. TAALCORRECTIE
   - Corrigeer spelling, grammatica, interpunctie
   - Bij DIRECTE CITATEN: behoud de spreekstijl van de spreker (woordkeuze, toon), verwijder eh's en herhalingen
   - Bij INDIRECTE PASSAGES: herschrijf journalistiek naar correct Nederlands
   - Verwijder false starts en overbodige herhalingen
   - Maak zinnen af die halverwege stoppen (markeer met [aangevuld])

4. STRUCTURERING
   - Verdeel in logische alinea's op basis van onderwerp/thema
   - Behoud tijdcodes als referentie
   - Markeer onverstaanbare passages als [onverstaanbaar, HH:MM:SS]
   - Voeg tussenkopjes toe bij langere transcripties (>1000 woorden)

5. QUOTELIJST (optioneel, lever als de transcriptie interviewmateriaal bevat)
   - Extraheer bruikbare citaten
   - Per citaat: tijdcode, spreker, de quote, en een korte context-notitie
   - Sorteer op nieuwswaarde/bruikbaarheid

Lever:
- Schone transcriptie
- Lijst van sprekers met identificatie
- Quotelijst (als interview)
- Eventuele onduidelijkheden die de auteur moet verificeren
