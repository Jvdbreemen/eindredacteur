---
name: koppen
description: Genereer 5-7 kopvarianten voor een aangeleverd artikel
allowed-tools: Read WebSearch
---

Genereer kopvarianten voor het aangeleverde artikel of onderwerp.

Laad eerst:
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht, modus B)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/taal-stijl.md (schrijfstijl)
- ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/genre-eisen.md (genre-specifieke kopeisen)

Stappen:
1. Lees het artikel of de samenvatting
2. Bepaal het genre (nieuws, feature, reportage, interview, column)
3. Identificeer de kern: wat is het belangrijkste feit, de sterkste hoek, het meest pakkende beeld?
4. Genereer 5-7 kopvarianten in deze categorieën:

| Type | Omschrijving |
|------|-------------|
| Informatief | Feitelijk, zakelijk, kernboodschap voorop |
| Wervend | Trekt de lezer het stuk in, mag speelser |
| Citaatkop | Sterkste quote uit het stuk als kop |
| Online/SEO | Zoekmachinevriendelijk, trefwoorden vooraan, max 60 tekens |
| Print | Mag korter, grafischer, meer impact |
| Vraagkop | Alleen als het stuk de vraag ook beantwoordt |
| Woordspel | Alleen als het organisch past, niet forceren |

Regels:
- Niet elke categorie is altijd nodig. Lever minimaal 5, maximaal 7 varianten.
- Elke kop moet kloppen met de inhoud van het artikel. Geen koppen die sterker zijn dan het stuk rechtvaardigt.
- Actieve werkwoorden, geen passief
- Geen vraagtekens tenzij het stuk de vraag beantwoordt
- Geen clickbait
- Bij nieuwsberichten: feitelijk en informatief als standaard
- Bij features: meer ruimte voor sfeer en beeld
- Vermeld bij elke variant het type
- **Feitendiscipline:** een kop mag geen feit toevoegen dat niet in het artikel staat. Geen verzonnen cijfers, namen of citaten in koppen. Bij citaatkop: alleen letterlijk uit het artikel.

Output format:

## Kopvarianten: [werktitel]

1. **[type]** — [kop]
2. **[type]** — [kop]
3. ...

**Aanbeveling:** [welke variant past het best bij genre, kanaal en doelgroep, met korte motivatie]

## Bronstatus
- Alle koppen direct gebaseerd op het aangeleverde artikel: [ja/nee]
- Aantal koppen met externe verificatie nodig: [n]

## Open verificatiepunten
[Eventuele claims in koppen die nog gecheckt moeten worden, of "Geen open punten"]
