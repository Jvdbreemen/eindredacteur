# Eindredacteur

Cowork-plugin voor Nederlandstalige journalistieke eindredactie. Beoordeelt, corrigeert en verbetert artikelen, transcripties en andere journalistieke producties.

## Installatie

Kopieer de `eindredacteur/` map naar je Cowork plugins directory, of installeer het `.plugin` bestand via Cowork.

## Skill

### eindredacteur

Triggert automatisch wanneer een Nederlandstalige tekst ter beoordeling wordt aangeboden. Werkt ook bij expliciete opdrachten als "beoordeel dit artikel", "redigeer", "check mijn tekst" of "copy edit".

**Workflow in 4 fases:**
1. **Lezen** - genre bepalen, intentie begrijpen, doelgroep identificeren
2. **Structuur** - lead, opbouw, alinea's, koppen beoordelen
3. **Inhoud** - feiten verifiëren, bronnen checken, hoor/wederhoor, ethiek
4. **Taal** - spelling, grammatica, stijl, leesbaarheid, AI-patronen detecteren

**Output:**
- Beoordelingsrapport met scores per categorie (1-5)
- Gecorrigeerde tekst met inline correcties

## Commands

### /eindredactie
Volledige eindredactie-pass. Doorloopt alle 4 fases, integreert met fact-check en source-verification skills, levert rapport + gecorrigeerde tekst.

### /transcriptie
Schoont een transcriptie op naar leesbaar Nederlands. Identificeert sprekers, corrigeert taal, structureert de tekst en extraheert bruikbare citaten.

### /kopij-check
Snelle pre-publish check. Scant op rode vlaggen, checkt lead en kop, doet lichte feitenverificatie. Levert een compact rapport met go/no-go oordeel.

## Integratie met andere skills

De eindredacteur werkt samen met:
- **ai-writing-detox** - detecteert AI-schrijfpatronen
- **fact-check-workflow** - verifieert feitelijke claims
- **source-verification** - beoordeelt bronbetrouwbaarheid
- **editorial-workflow** - pre-publish checklist
- **newsroom-style** - Engelse stijlregels bij (deels) Engelse tekst

## References

De skill bevat 6 reference-bestanden die on-demand geladen worden:

| Bestand | Inhoud |
|---------|--------|
| `taal-stijl.md` | Nederlandse taalregels, spelling, zinsbouw, citeerwijze |
| `genre-eisen.md` | Checklists per genre (nieuws, feature, reportage, interview, column, verslag, recensie) |
| `rode-vlaggen.md` | Detectie van kritieke, serieuze en aandachtspunten |
| `kwaliteitsschaal.md` | Scoredefinities (1-5) en evaluatieprotocol |
| `ethiek.md` | Privacy, hoor/wederhoor, bronbescherming, rectificatie |
| `digitaal.md` | SEO, social media, toegankelijkheid, mobile-first |

## Bronnen

Gebaseerd op:
- Kussendrager, N., Van der Lugft, D. & Verschoor, B. (2014). *Basisboek journalistiek*. Noordhoff Uitgevers.
- Goris, R. & Delforge, G. (2012). *Journalistiek: inleiding tot het vak*. Lannoo Campus.
- Riblet, C. (1974). *The solid gold copy editor*. Walter de Gruyter.
- Briggs, M. (z.d.). *Journalism 2.0: How to survive and thrive*. Knight Foundation.
- Drok, N. (2007). *De toekomst van de journalistiek*. Boom Lemma.
- Bardoel, J. & Wijfjes, H. (2015). *Journalistieke cultuur in Nederland*. Amsterdam University Press.
- Wilson, J. (z.d.). *Freelance Writer's Handbook*. Loompanics Unlimited.

## Auteur

Jim van den Breemen
