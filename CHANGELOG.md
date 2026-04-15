# Changelog

## v0.4.1 - Publicatie-klaar, commands + skills parallel

### Nieuw
- `LICENSE` (MIT) toegevoegd.
- `commands/` map hersteld met thin wrappers voor alle 13 skills, zodat ze zowel via slash command (`/eindredactie`, `/transcriptie`, ...) als via skill-trigger beschikbaar zijn in Claude Code en Cowork.
- README installatie-sectie uitgebreid met Claude Code en Cowork instructies.

### Gewijzigd
- Persoonlijke auteurreferenties verwijderd uit `plugin.json` en README.
- `plugin.json` krijgt `"license": "MIT"` veld.
- `/sum-AIauth` en `/sumAI` hernoemd naar `/sum-aiauth` en `/sumai` (match met bestandsnamen).

## v0.4.0 - Verificatielaag en lokale bronnen

**Aanleiding:** in v0.3.3 gebruikten 10 skills WebSearch zonder gedefinieerde fallback bij leeg resultaat. De `leguit` skill bevatte een instructie die hallucinatie van APA7 referenties uitlokte. De gebundelde boeksamenvattingen werden door geen enkele skill gebruikt.

### Nieuw

- **Verificatielaag** (`references/verificatie.md`) met verplichte bronvolgorde (lokaal eerst, web tweede, gebruiker derde), twee fallbackmodi (strikt en markeer-en-lever), APA7-discipline en bronstatus tags.
- **Gebundelde lokale bronnen** in `references/bronnen/` met samenvattingen van zeven journalistieke vakboeken: Kussendrager et al. (2014), Bardoel & Wijfjes (2015), Briggs, Drok (2007), Goris & Delforge (2012), Riblet (1974), Wilson. Plugin werkt nu standalone, ook voor externe gebruikers.
- **Bronnenindex** (`references/bronnen/OVERZICHT.md`) als lichtgewicht routing-laag die domeinen koppelt aan de juiste samenvatting.
- **Bronstatus tags** verplicht in elke output: `[BRON-LOKAAL]`, `[BRON-WEB]`, `[SINGLE-SOURCE]`, `[TRAININGSKENNIS]`, `[ONGEVERIFIEERD]`, `[TE VERIFIËREN]`.
- **Open verificatiepunten** sectie verplicht in elke skill output.

### Gewijzigd

- `leguit/SKILL.md` (P1): twee-traps procedure (begripscontext + bronstrategie). Strikte modus: stopt en vraagt om bronmateriaal als geen bron te vinden is. Verzint geen referenties meer.
- `invalshoek/SKILL.md` (P2): bronvolgorde verplicht in onderwerp-analyse, bronstatus tag per claim.
- `interviewprep/SKILL.md` (P3): strikte modus voor research-briefing. Geen gegokte biografische feiten over echte personen.
- `script/SKILL.md` (P4): WebSearch toegevoegd aan allowed-tools, feitendiscipline regel toegevoegd. Geen verzonnen citaten of cijfers in voice-over.
- `eindredacteur/SKILL.md` (P6+P9): description versmald, verificatielaag in fase 3 verplicht gesteld, references-tabel uitgebreid.
- `eindredactie/SKILL.md` (P8+P7): verplichte fact-check tijdens fase 3, bronstatus rapport toegevoegd aan output.
- `kopij-check/SKILL.md` (P10): verificatielaag include, bronstatus en open verificatiepunten in compact rapport.
- `transcriptie/SKILL.md` (P10): geen verzonnen sprekersnamen, verificatielaag include, bronstatus rapport.
- `koppen/SKILL.md` (P10): feitendiscipline regel, geen verzonnen feiten in koppen.
- `itemsheet/SKILL.md` (P10): verificatielaag include, voorgestelde gesprekspartners als voorstellen gemarkeerd.
- `herschrijf/SKILL.md` (P10): geen feiten toevoegen die niet in het origineel staan.
- `montage/SKILL.md` (P10): verificatielaag include, geen verzonnen shots.
- `sumai/SKILL.md` + `sum-aiauth/SKILL.md` (P10+B10): Bash toegevoegd, datum via `date` command, AI-model exact zoals aangeduid in sessie. Niet meer zelf gokken.

### Fixes

- B9: `genre-eisen.md` voorbeeld over Zwolle nu gemarkeerd als `[fictief]`.
- B10: sumai en sum-aiauth instrueren expliciet om datum en model niet zelf in te vullen.

### Plugin metadata

- Versie: 0.3.3 → 0.4.0
- Description uitgebreid met verificatielaag.
- Keywords uitgebreid met "bronverificatie", "fact-check", "hallucinatie-preventie".

---

## v0.3.3 - Eerdere release

Plugin met 1 skill, 6 commands en 6 referentiebestanden, gebouwd op kennis uit 7 journalistieke vakboeken. Geen verificatielaag, WebSearch zonder gedefinieerde fallback.
