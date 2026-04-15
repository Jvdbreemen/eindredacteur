# Eindredacteur

**Versie 0.4.1**

Cowork-plugin voor Nederlandstalige journalistieke eindredactie. Beoordeelt, corrigeert en verbetert artikelen, transcripties en andere journalistieke producties.

Vanaf v0.4.0 met verplichte verificatielaag, gebundelde lokale bronnen (7 vakboeken) en bronstatus tagging in elke output. Doel: een tool waarop een journalist kan leunen, zonder verzonnen feiten of bronnen.

## Installatie

De plugin werkt zowel in **Claude Code** als in **Cowork**.

### Claude Code

Clone de repo in je plugins directory:

```bash
git clone https://github.com/Jvdbreemen/eindredacteur.git ~/.claude/plugins/eindredacteur
```

Of voeg de repo toe via een plugin marketplace die naar deze GitHub URL verwijst. Claude Code leest `.claude-plugin/plugin.json` automatisch uit.

### Cowork

Kopieer de map naar je Cowork plugins directory, of installeer een `.plugin` bundel via Cowork.

### Verificatie

Na installatie zou de skill `eindredacteur` en de commands (`/eindredactie`, `/transcriptie`, etc.) beschikbaar moeten zijn. Test met een korte Nederlandstalige tekst en de opdracht "beoordeel dit artikel".

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

## Commands (v0.3.0)

### Redactie
- `/eindredactie` - Volledige eindredactie-pass op een tekst
- `/transcriptie` - Transcriptie opschonen en corrigeren naar leesbaar Nederlands
- `/kopij-check` - Snelle pre-publish check met compact rapport
- `/koppen` - 5-7 kopvarianten genereren (informatief, wervend, SEO, print)
- `/herschrijf` - Tekst herschrijven voor ander kanaal, format of doelgroep

### Voorbereiding
- `/interviewprep` - Interview voorbereiding met vragenlijst en research-briefing
- `/invalshoek` - 3-5 invalshoeken met pitch-varianten voor een onderwerp

### Audio & video
- `/itemsheet` - Ingevuld itemsheet voor audio/video-productie
- `/script` - Voicetrack of scriptvoorstel voor audio/video
- `/montage` - Montage-opbouw en shotlist

### Verantwoording
- `/sum-aiauth` - AI-verantwoording voor portfolio's (1-1,5 alinea)
- `/sumai` - Samenvatting gehele gesprek + AI-verantwoording

### Kennistools
- `/leguit` - Begripsuitleg in standaardformat (korte uitleg, voorbeeld, bron, verdieping)

## Integratie met andere skills

De eindredacteur werkt samen met:
- **ai-writing-detox** - detecteert AI-schrijfpatronen
- **fact-check-workflow** - verifieert feitelijke claims
- **source-verification** - beoordeelt bronbetrouwbaarheid
- **editorial-workflow** - pre-publish checklist
- **newsroom-style** - Engelse stijlregels bij (deels) Engelse tekst

## Verificatielaag (nieuw in v0.4.0)

Elke skill die feiten of bronnen aanraakt, gebruikt een verplichte verificatielaag (`references/verificatie.md`). Deze legt vast:

1. **Bronvolgorde**: lokale bronnen eerst (gebundeld in `references/bronnen/`), WebSearch tweede, gebruiker derde. Nooit verzinnen.
2. **Twee modi**: strikt (`leguit`, `interviewprep` stoppen bij geen bron) of markeer-en-lever (overige skills leveren met expliciete `[ONGEVERIFIEERD]` markering).
3. **Bronstatus tags**: elke feitelijke claim krijgt een tag (`[BRON-LOKAAL]`, `[BRON-WEB]`, `[SINGLE-SOURCE]`, `[TRAININGSKENNIS]`, `[ONGEVERIFIEERD]`, `[TE VERIFIËREN]`).
4. **Open verificatiepunten**: elke output sluit af met een lijst die de gebruiker zelf moet checken.

De gebundelde bronnen bevatten samenvattingen van zeven journalistieke vakboeken (Kussendrager, Bardoel & Wijfjes, Briggs, Drok, Goris & Delforge, Riblet, Wilson). Een lichtgewicht index in `references/bronnen/OVERZICHT.md` helpt bepalen welke samenvatting bij welk domein hoort.

## References

De skill bevat reference-bestanden die on-demand geladen worden:

| Bestand | Inhoud |
|---------|--------|
| `verificatie.md` | **Verplicht**. Bronvolgorde, fallback, APA7-discipline, bronstatus tags |
| `bronnen/OVERZICHT.md` | Index van de 7 gebundelde boeksamenvattingen, met domeinen |
| `bronnen/*.md` | Samenvattingen per boek (kussendrager, bardoel-wijfjes, briggs, drok, goris, riblet, wilson) |
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

## Licentie

MIT. Zie `LICENSE`.

## Bijdragen

Issues en pull requests zijn welkom via GitHub. Voor grote wijzigingen: open eerst een issue om de aanpak te bespreken.
