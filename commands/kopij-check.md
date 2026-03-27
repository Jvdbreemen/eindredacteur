---
description: Snelle pre-publish check met compact rapport
allowed-tools: Read, WebSearch, WebFetch
---

Voer een snelle pre-publish check uit op de aangeleverde tekst.

Laad de eindredacteur skill uit ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/SKILL.md.
Laad ${CLAUDE_PLUGIN_ROOT}/skills/eindredacteur/references/rode-vlaggen.md.

Dit is GEEN volledige eindredactie maar een snelle scan. Focus op de grootste risico's.

Pipeline:

1. RED FLAG SCAN
   - Scan op rode vlaggen uit references/rode-vlaggen.md
   - Categoriseer als: 🔴 KRITIEK / 🟡 SERIEUS / 🟠 AANDACHT
   - Bij 🔴 vlaggen: direct melden, publicatie afraden

2. LEAD & KOP CHECK
   - Kop: accuraat? actief? niet misleidend? niet sterker dan artikel?
   - Lead: bevat de kern? compact genoeg? (nieuws: max 30 woorden)
   - Suggereer alternatieven als kop of lead zwak is

3. VERIFICATIE-SCAN
   - Lichtgewicht: alleen direct verifieerbare claims (namen, functies, data, cijfers)
   - Gebruik WebSearch bij twijfel over specifieke feiten
   - Geen volledige fact-check, wel een vangnet

4. COMPACT RAPPORT
   Lever in dit exacte format:

   ```
   KOPIJ-CHECK: [titel]
   Genre: [genre]
   Datum: [datum]

   ✅/⚠️/❌ Lead          - [korte toelichting]
   ✅/⚠️/❌ Kop           - [korte toelichting]
   ✅/⚠️/❌ Feiten        - [korte toelichting]
   ✅/⚠️/❌ Bronnen       - [korte toelichting]
   ✅/⚠️/❌ Hoor/wederhoor - [korte toelichting]
   ✅/⚠️/❌ Taal          - [korte toelichting]
   ✅/⚠️/❌ Ethiek        - [korte toelichting]

   RODE VLAGGEN:
   [lijst, of "Geen gevonden"]

   ACTIEPUNTEN:
   1. [hoogste prioriteit eerst]
   2. ...

   OORDEEL: [Publiceerbaar / Na revisie publiceerbaar / Niet publiceerbaar]
   ```
