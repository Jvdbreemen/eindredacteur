---
name: sum-aiauth
description: AI-verantwoording voor portfolio's en authenticiteitsverklaringen (1-1,5 alinea)
allowed-tools: Read Bash
---

Genereer een AI-verantwoordingstekst voor het huidige product/gesprek.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/ethiek.md (ethische context)

**Bepaal de huidige datum via Bash (`date +%Y-%m-%d`). Vul nooit zelf een datum in.**
**Vermeld het AI-model exact zoals het in de huidige sessie wordt aangeduid. Als je het niet zeker weet: vraag de gebruiker.**

Stappen:
1. Scan dit gesprek op alle momenten waar AI is ingezet
2. Categoriseer het AI-gebruik (research, tekstgeneratie, redactie, fact-check, structuur, vertaling, data-analyse)
3. Bepaal de verhouding menselijke inbreng vs. AI-inbreng
4. Schrijf een verantwoording van 1-1,5 alinea (4-7 zinnen)

Regels:
- Derde persoon ("de journalist", "de auteur")
- Benoem EERST wat de mens deed, DAN wat AI deed
- Wees specifiek over het type AI-inzet, niet vaag
- Geen bagatellisering, geen overdrijving
- Vermeld altijd: AI-model, datum, type inzet
- Zakelijke, transparante toon

Output format:
## AI-verantwoording

[1-1,5 alinea]

**AI-model:** [model — exact zoals aangeduid in deze sessie, niet gokken]
**Datum:** [datum — opgehaald via Bash `date`]
**Type inzet:** [categorieën]
