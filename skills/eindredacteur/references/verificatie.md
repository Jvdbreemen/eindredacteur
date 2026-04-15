# Verificatie en bronnendiscipline

Centrale verificatielaag voor alle skills in de Eindredacteur plugin. Doel: voorkomen dat de tool feiten, bronnen of citaten verzint. Een journalist moet kunnen leunen op de output. Bronstatus moet altijd zichtbaar zijn.

Laad dit bestand in elke skill die feitelijke claims doet, bronnen citeert of begrippen uitlegt.

---

## 1. Bronvolgorde (verplicht)

Volg deze volgorde elke keer dat je een feit, bron, citaat of definitie nodig hebt. Sla geen stap over.

**Stap 1 - Lokale bronnen eerst.**
Raadpleeg `${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/bronnen/OVERZICHT.md` om te bepalen welk(e) boek(en) het domein dekken. Lees daarna het of de relevante samenvatting(en) volledig in. Citeer letterlijk en in APA7.

**Stap 2 - WebSearch alleen als lokaal niets dekt.**
Pas WebSearch of WebFetch toe wanneer geen enkele lokale bron het onderwerp dekt, of wanneer actuele context vereist is (nieuws, recente cijfers, beleidsupdates, prijzen, schema's, sterfgevallen, verkiezingen). Verifieer minimaal twee onafhankelijke, geloofwaardige bronnen. Noteer URL en raadpleegdatum.

**Stap 3 - Vraag de gebruiker bij geen treffer.**
Als noch lokale bronnen noch WebSearch een betrouwbare bron opleveren, vraag de gebruiker om bronmateriaal of expliciete toestemming voor een ongeverifieerde uitspraak. Doe geen aannames. Vul nooit een referentie in op basis van waarschijnlijkheid.

**Stap 4 - Nooit verzinnen.**
Genereer nooit een APA7 referentie, auteur, titel, jaar, paginanummer, citaat of cijfer dat je niet uit een lokale of webbron hebt gehaald. Liever leeg of `[ONGEVERIFIEERD]` dan plausibel ogend.

---

## 2. Wanneer WebSearch overslaan

Sommige skills doen geen feitelijke claims en hoeven WebSearch niet te raadplegen. Sla over bij:

- pure tekstredactie zonder feitelijke uitspraken (taal, stijl, ritme)
- structurele herschikkingen waarbij de feitelijke inhoud onveranderd blijft
- formattering of opmaak
- procesvragen (wat is een goed itemsheet, hoe schrijf ik een lead)

Doe WebSearch altijd wel bij:
- begripsuitleg met externe definities
- naamcontroles, functietitels, organisaties
- cijfers, statistieken, jaartallen
- citaten waarvan de bron onbekend is
- recente gebeurtenissen of beleid

---

## 3. Fallback bij leeg resultaat

Als WebSearch geen bruikbaar resultaat teruggeeft, hanteer per skill een van twee modi.

**Modus A - Strikt: stop en vraag.**
Voor `leguit` en `interviewprep`. Stop het proces. Vraag de gebruiker om bronmateriaal of bevestiging. Lever geen output zonder bron.

**Modus B - Markeer en lever af.**
Voor alle andere skills. Lever de output wel, maar markeer elke onverifieerbare claim expliciet met `[ONGEVERIFIEERD]` of `[TE VERIFIËREN]`. Voeg aan het einde een sectie `Open verificatiepunten` toe met de specifieke vragen die de gebruiker zelf moet checken.

---

## 4. APA7 discipline

Gebruik APA7 in alle bronvermeldingen. Verzin nooit een referentie.

**Volledige bron in lijst onderaan:**
```
Auteur, A. A. (Jaar). Titel van het werk. Uitgever.
```

Voorbeelden uit de gebundelde bronnen (volledig en correct, mag je letterlijk overnemen):
```
Bardoel, J., & Wijfjes, H. (2015). Journalistieke cultuur in Nederland. Amsterdam University Press.
Briggs, M. (z.d.). Journalism 2.0: How to survive and thrive. J-Lab and the Knight Citizen News Network.
Drok, N. (2007). De toekomst van de journalistiek. Boom.
Goris, G., & Delforge, S. (2012). Journalistiek: Inleiding tot het vak. Acco.
Kussendrager, N., Van der Lugft, D., & Verschoor, C. (2014). Basisboek journalistiek. Noordhoff.
Riblet, C. B. (1974). The solid gold copy editor. Iowa State University Press.
Wilson, R. (z.d.). Freelance writer's handbook (2nd ed.).
```

**In tekst:**
```
(Kussendrager et al., 2014)
(Bardoel & Wijfjes, 2015)
```

Als je twijfelt over een veld (jaar, uitgever, paginanummer): laat het veld leeg en markeer met `[TE VERIFIËREN]`. Niet invullen op gevoel.

---

## 5. Bronstatus tags (verplicht in output)

Markeer elke feitelijke uitspraak met een van de volgende tags. Zonder tag is een feitelijke uitspraak ongeldig.

| Tag | Betekenis |
|-----|-----------|
| `[BRON-LOKAAL: bestand.md]` | Onderbouwd via een lokaal bronbestand uit `references/bronnen/`. |
| `[BRON-WEB: URL, dd-mm-jjjj]` | Onderbouwd via WebSearch of WebFetch, met URL en raadpleegdatum. |
| `[SINGLE-SOURCE]` | Slechts één onafhankelijke bron beschikbaar. Tweede verificatie aanbevolen. |
| `[TRAININGSKENNIS]` | Op basis van algemene kennis, niet getoetst tegen externe bron. Mag alleen voor onomstreden achtergrond. |
| `[ONGEVERIFIEERD]` | Niet te verifiëren binnen deze sessie. Gebruiker moet zelf checken. |
| `[TE VERIFIËREN]` | Onderdeel van een referentie of cijfer dat nog ontbreekt of niet zeker is. |

Plaats de tag direct achter de claim, bijvoorbeeld: "Het Openbaar Ministerie startte het onderzoek in maart 2026 [BRON-WEB: nos.nl/artikel-12345, 08-04-2026]."

---

## 6. Verplichte output-elementen

Elke skill die deze verificatielaag gebruikt, sluit de output af met een sectie:

```
## Bronnen
- [APA7 entries van alle gebruikte bronnen]

## Bronstatus
- Lokaal: [aantal claims met BRON-LOKAAL]
- Web: [aantal claims met BRON-WEB]
- Single-source: [aantal]
- Trainingskennis: [aantal]
- Ongeverifieerd: [aantal]

## Open verificatiepunten
- [Lijst van claims die de gebruiker zelf moet checken, met concreet vraagstuk]
```

Als alle claims zijn afgedekt: laat de sectie 'Open verificatiepunten' leeg met de tekst "Geen open punten."

---

## 7. Wat NOOIT mag

- APA7 referenties verzinnen of plausibel maken zonder daadwerkelijke bron.
- Auteursnamen, jaartallen of titels gokken.
- Citaten genereren die niet letterlijk uit een bron komen.
- Cijfers afronden of "ongeveer" maken zonder bronvermelding.
- Een lokale bron citeren die je niet daadwerkelijk hebt ingelezen.
- Web bronnen verzinnen of plausibele URLs construeren.
- Een bronstatus tag weglaten bij een feitelijke claim.

Bij twijfel: lever minder, markeer eerlijk, of stop en vraag.

---

*Deze verificatielaag is verplicht voor: leguit, invalshoek, interviewprep, script, eindredactie, kopij-check, transcriptie, koppen, itemsheet, herschrijf, montage, sumai, sum-aiauth.*
