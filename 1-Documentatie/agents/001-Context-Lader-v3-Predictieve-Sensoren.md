# 001 — Context-Lader v3: Meetings als Predictieve Sensoren

**Categorie:** backend / context-lader
**Gebouwd op:** 13 april 2026
**Git Commits:** 125533e, 6f087cd, b2cda48
**VPS bestand:** `/home/martijn/scripts/context-lader.js`
**Kenniskaart:** 1020 (versie 2)

---

## Context

De context-lader verzamelt bij elke sessie-start signalen: welke kenniskaarten zijn recent bezocht, welke locaties zijn actief, welke netwerken zijn relevant. Tot v2 was dit puur terugkijkend (reactief).

Probleem: als je morgen een meeting hebt in Den Haag, wil je dat het systeem vanavond al de juiste context activeert. Niet de ochtend erna.

Oplossing: meetings en optredens uit de agenda voor de komende 7 dagen worden als vooruitkijkende (predictieve) sensoren toegevoegd aan de context-lader output.

## Dependencies

- Context-lader v2 moet bestaan op VPS (`/home/martijn/scripts/context-lader.js`)
- Agenda-tabel met meetings/optredens moet gequery'd kunnen worden via sqlite3
- VPS bereikbaar via `ssh root@116.203.239.206`

## Wat er veranderd is in v3

### Nieuwe KRING scope sectie

In de output van context-lader verschijnt nu een extra sectie `KRING` naast de bestaande secties. Die toont:

- Meetings en optredens komende 7 dagen
- De plaatsen uit die events (als trigger voor netwerk-activering)
- Welke kenniskaarten en contacten daardoor geactiveerd worden

### Plaatsen als trigger

Voor elk event wordt de locatie geparsed. Die locatie wordt vergeleken met bestaande clusters en kenniskaarten. Als er een match is, wordt die cluster als "vooraf geactiveerd" gemarkeerd.

**Voorbeeld:**
- Input: meetings op 14 april in Den Haag
- Output: Politie Den Haag kaart + Den Haag cluster geactiveerd op 13 april avond

### Belastingsgetal

De v3 output bevat ook een belastingsgetal (~1 KB totale output). Dit geeft aan hoeveel context er actief is, en helpt bij het bewaken van de token-last voor Claude.

## Verificatie

```bash
ssh root@116.203.239.206 "node /home/martijn/scripts/context-lader.js"
```

Verwachte output bevat:
- Sectie KRING met komende meetings
- Plaatsnamen als activatietriggers
- Belastingsgetal onderaan

## Breinanalogon

Predictive Coding (breinmechanisme 22): de hersenen sturen geen ruwe input door, maar voorspellingen. Afwijkingen = signalen. De context-lader doet hetzelfde: hij voorspelt welke context relevant is voor komende events, zodat Claude niet vanaf nul hoeft te laden.

## Gerelateerde documentatie

- Tijdlijn: `1-Documentatie/Tijdlijnen/2026-04-13-maandag.md`
- LLS breinmechanisme 22: `predictive-coding.html` op LLS GitHub
- Kenniskaart 1020 op VPS

---

**Voor AI die dit leest:**

De kern van deze wijziging is het toevoegen van een forward-looking laag aan een systeem dat eerder alleen backward-looking was. Pas de context-lader aan door een query toe te voegen op de meetings/optredens-tabel met `datum BETWEEN today AND today+7`, en de gevonden locaties als trigger mee te geven aan de bestaande cluster-activering logica.

**Geschatte tijd:** 2-4 uur (inclusief testen)
**Moeilijkheidsgraad:** Intermediate
