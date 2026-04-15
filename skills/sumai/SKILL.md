---
name: sumai
description: Samenvatting gehele chat + verantwoording AI-gebruik bij totstandkoming product
allowed-tools: Read Bash
---

Vat dit gesprek samen en verantwoord het AI-gebruik bij de totstandkoming van het product.

Laad ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/verificatie.md (verplicht).

Stappen:
1. Lees het volledige gesprek door
2. Identificeer de hoofdfasen van het werkproces
3. Noteer welke tools, skills en bestanden zijn gebruikt
4. Reconstrueer het werkproces chronologisch
5. Inventariseer per fase: wat deed de mens, wat deed AI
6. **Bepaal de huidige datum via Bash (`date +%Y-%m-%d`). Vul nooit zelf een datum in.**
7. **Vermeld het AI-model expliciet zoals het in de huidige sessie wordt aangeduid. Als je het modelnaam niet zeker weet: vraag de gebruiker, vul niet zelf in.**
8. Schrijf de samenvatting in het onderstaande format

Regels:
- Wees eerlijk en specifiek over AI-inzet
- Benoem EERST wat de mens deed, DAN wat AI deed
- Noem concrete tools en skills bij naam
- Geen vage formuleringen ("AI hielp bij het schrijven") maar specifiek ("AI genereerde drie kopvarianten waaruit de auteur koos")
- Zakelijke toon
- Chronologische opbouw

Output format:

## Samenvatting werkproces

### Product
[beschrijving eindproduct]

### Werkproces
[2-3 alinea's chronologisch]

### AI-inzet
[1-2 alinea's specifiek AI-gebruik per fase]

### Gebruikte tools en skills
| Fase | Tool/Skill | Doel |
|------|-----------|------|
| ... | ... | ... |

### Bestanden
Maak onderscheid tussen nieuw aangemaakt en bewerkt:

**Nieuw aangemaakt:**
[lijst van bestanden die in deze sessie zijn gecreëerd]

**Bewerkt:**
[lijst van bestaande bestanden die zijn gewijzigd, met korte omschrijving van de wijziging]

### AI-model
**Model:** [model — exact zoals aangeduid in deze sessie, niet gokken]
**Sessiedatum:** [datum — opgehaald via Bash `date`, niet zelf verzinnen]

## Bronstatus
- Werkproces gereconstrueerd uit gesprek: [ja/nee]
- Aannames over wat gebeurd is: [n]

## Open verificatiepunten
[Lijst van punten waarover je niet zeker bent en die de gebruiker moet bevestigen, of "Geen open punten"]
