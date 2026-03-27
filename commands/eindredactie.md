---
description: Volledige eindredactie-pass op een tekst
allowed-tools: Read, Write, Edit, Bash, Grep, WebSearch, WebFetch
---

Voer een volledige eindredactie uit op de aangeleverde tekst.

Laad eerst de eindredacteur skill uit ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/SKILL.md.

Stel, als niet duidelijk uit context, eerst 2-3 verhelderende vragen:
- Doelgroep en publicatiekanaal
- Gewenst genre (als niet evident)
- Deadline en gewenste lengte

Doorloop vervolgens de volledige 4-fasen workflow uit de skill:
1. LEZEN - genre bepalen, intentie begrijpen, references laden
2. STRUCTUUR - lead, opbouw, alinea's, koppen
3. INHOUD - feiten, bronnen, hoor/wederhoor, ethiek
4. TAAL - spelling, grammatica, stijl, leesbaarheid, AI-patronen

Raadpleeg tijdens fase 3 de fact-check-workflow skill voor verifieerbare claims.
Raadpleeg tijdens fase 3 de source-verification skill voor twijfelachtige bronnen.
Raadpleeg tijdens fase 4 de ai-writing-detox skill voor AI-detectie.

Lever twee producten:
1. Beoordelingsrapport met scores per categorie (1-5) volgens het format uit de skill
2. Gecorrigeerde tekst met inline correcties (~~doorhaling~~ en **toevoeging**)

Sluit af met: publicatieklaar ja/nee/na revisie + genummerde actiepunten.
