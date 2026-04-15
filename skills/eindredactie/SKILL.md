---
name: eindredactie
description: Volledige eindredactie-pass op een tekst - feedback-first, geen hertekst
allowed-tools: Read Write Edit Bash Grep WebSearch WebFetch
---

Voer een volledige eindredactie uit op de aangeleverde tekst. Lever **feedback**, geen gecorrigeerde hertekst. De auteur verwerkt de correcties zelf.

## Werkvolgorde

### Stap 0: Context bepalen (geen tools nodig)

Stel, als niet evident uit context, 2-3 verhelderende vragen:
- Doelgroep en publicatiekanaal
- Genre (als onduidelijk)
- Deadline en gewenste lengte

Laad alleen wat je daadwerkelijk nodig hebt. Begin minimalistisch.

### Stap 1: Verplichte basis inlezen

Laad nu:
- `${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/SKILL.md` (hoofdrol en workflow)

Niets anders. Overige references laad je pas bij een daadwerkelijke trigger.

### Stap 2: 4-fasen workflow

Doorloop de fases uit de hoofdrolskill: LEZEN, STRUCTUUR, INHOUD, TAAL.

**Conditionele reference-loads** (alleen wanneer van toepassing):

| Reference | Alleen laden wanneer |
|-----------|----------------------|
| `references/genre-eisen.md` | Je twijfelt over genre-specifieke eisen, of het stuk schendt waarschijnlijk genreconventies |
| `references/rode-vlaggen.md` | Je vermoedt rode vlaggen (kop sterker dan stuk, selectieve citaten, one-source, belangenconflict) |
| `references/taal-stijl.md` | Je vindt meer dan 3 taalkundige twijfelgevallen die je zonder reference niet definitief kunt oordelen |
| `references/ethiek.md` | Privacy, stereotypering, proportionaliteit of bronbescherming spelen |
| `references/digitaal.md` | Publicatiekanaal is online of social |
| `references/kwaliteitsschaal.md` | Bij twijfel over scoretoekenning |
| `references/verificatie.md` | Pas laden in Stap 3 als gebruiker fact-check vraagt |
| `references/bronnen/OVERZICHT.md` | Pas laden in Stap 3 als gebruiker fact-check vraagt |
| `references/bronnen/{boek}.md` | Alleen het specifieke boek dat relevant is voor een aangevraagde claim |

Regel: als je twijfelt of een reference nodig is, werk dan eerst zonder. Je kunt hem alsnog opvragen in een vervolgronde.

### Stap 3: Fact-check, claimlijst-first

**Geen automatische WebSearch in de standaardrun.** In plaats daarvan:

1. Extraheer alle verifieerbare feitelijke claims (namen, functies, organisaties, data, cijfers, plaatsnamen, citaten, wetsartikelen, historische beweringen).
2. Rangschik elke claim op risico:
   - **Hoog**: fout zou publicatie blokkeren (namen, functies van betrokkenen, cijfers in kop of lead, juridisch sensitieve uitspraken, directe citaten).
   - **Midden**: fout zou geloofwaardigheid aantasten maar niet blokkeren (historische details, secundaire cijfers, parafrase-bronnen).
   - **Laag**: algemene context, common knowledge, niet-doorslaggevend.
3. Lever de claimlijst aan de gebruiker. Noteer per claim een vermoeden (plausibel, twijfelachtig, verdacht) en een voorgestelde verificatieroute (lokale bron uit `bronnen/OVERZICHT.md`, web, contactpersoon, document).
4. Vraag de gebruiker welke claims je daadwerkelijk moet verifieren. Pas daarna voer je WebSearch of lokale bron-reads uit.
5. Verzin nooit een bron. Claims zonder verificatie houden de status `[TE VERIFIEREN]` of `[ONGEVERIFIEERD]`.

**Uitzondering**: als een claim zo verdacht is dat publicatie zonder check onverantwoord is (bijvoorbeeld een citaat dat feitelijk onjuist klinkt, een datum die niet kan kloppen), markeer dit expliciet als `[PUBLICATIEBLOKKEREND]` in het rapport en geef er een korte motivatie bij. Ook dan check je niet automatisch, maar dwing je een beslissing af.

### Stap 4: Sub-skills alleen op trigger

Roep sub-skills niet standaard aan. Alleen wanneer:

| Skill | Trigger |
|-------|---------|
| `ai-writing-detox` | Je detecteert 3 of meer AI-patronen (lege transities, opsommingsziekte, cliche-cluster, overmatig "belangrijk/cruciaal/essentieel") |
| `fact-check-workflow` | De gebruiker akkoord geeft om specifieke claims te verifieren en de claim niet triviaal is |
| `source-verification` | Een gebruikte bron in het stuk onbekend is, een single-source setup, of verdacht oogt |

## Output: feedback-only

Lever **een** document: het beoordelingsrapport. Geen gecorrigeerde tekst, geen inline strikes, geen hertekst. Verwijs naar specifieke locaties in het origineel (alinea-nummer, eerste woorden van de zin, of citaat tussen aanhalingstekens) zodat de auteur zelf kan navigeren.

### Rapportstructuur

```
## Eindredactie-rapport: [titel]

**Genre:** [gedetecteerd]
**Doelgroep / kanaal:** [afgeleid of aangegeven]
**Publicatieklaar:** Ja / Na revisie / Nee
**Totaalscore:** [1-5]

### Scores per categorie
| Categorie | Score | Toelichting |
|-----------|-------|-------------|
| Feitelijke correctheid | [1-5] | [1 zin] |
| Structuur en opbouw | [1-5] | [1 zin] |
| Taal en stijl | [1-5] | [1 zin] |
| Brongebruik en attributie | [1-5] | [1 zin] |
| Ethiek | [1-5] | [1 zin] |
| Genre-eisen | [1-5] | [1 zin] |
| Koppen | [1-5] | [1 zin] |

### Sterke punten
- [max 3 bullets, concreet]

### Rode vlaggen
- [leeg laten als er geen zijn; anders: korte omschrijving + locatie]

### Actiepunten op prioriteit
**Must-fix (publicatieblokkerend):**
1. [Locatie] - [probleem] - [voorgestelde oplossing in 1 zin]

**Should-fix (kwaliteit):**
1. [Locatie] - [probleem] - [voorgestelde oplossing in 1 zin]

**Could-fix (cosmetisch):**
1. [Locatie] - [probleem] - [suggestie]

### Taal en stijl, compact
Lijst de concrete taalfouten als: "alinea X, 'fragment...': fout -> voorstel". Geen volledige zinsherstel, alleen het stukje dat wijzigt. Alleen fouten, geen voorkeurs-stijlkwesties.

### Claimlijst voor fact-check
| # | Claim | Risico | Vermoeden | Voorgestelde verificatieroute |
|---|-------|--------|-----------|-------------------------------|
| 1 | [claim verbatim of parafrase] | Hoog/Midden/Laag | Plausibel/Twijfelachtig/Verdacht | [lokale bron, web, contactpersoon] |

Sluit af met: "Welke claims wil je dat ik verifieer?"

### Geraadpleegde references
- [alleen bestanden die je daadwerkelijk hebt geladen]

### Geraadpleegde sub-skills
- [alleen als getriggerd]
```

## Efficientie-principes

- **Feedback, geen hertekst**: de auteur corrigeert zelf.
- **Lazy loading**: references alleen op trigger.
- **Claimlijst-first**: WebSearch pas na akkoord gebruiker.
- **Sub-skills op trigger**: geen standaard-chain.
- **Verwijzen per locatie**: alinea-nummer + fragment, niet hele zinnen.
- **Kwaliteitsbehoud**: alle categorieen worden beoordeeld, alleen de uitvoering is compacter.

Als de gebruiker expliciet om een volledige gecorrigeerde hertekst vraagt, lever die dan apart aan na het rapport. Standaard niet.
