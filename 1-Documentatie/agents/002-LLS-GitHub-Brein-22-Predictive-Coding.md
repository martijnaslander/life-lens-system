# 002 — LLS GitHub: Brein 22/22 — Predictive Coding

**Categorie:** frontend / LLS GitHub
**Gebouwd op:** 13 april 2026
**Git Commits:** 125533e, 6f087cd, b2cda48
**Repo:** life-lens-system (GitHub, origin/main)

---

## Context

Het LLS GitHub-project bevat een reeks pagina's (Engelse + Nederlandse versie) over breinmechanismen die de wetenschappelijke onderbouwing vormen van het Life Lens System. Elk mechanisme heeft een eigen HTML-pagina. Vandaag is nummer 22 — het laatste — toegevoegd: Predictive Coding.

De reeks is nu compleet (22/22).

## Aangemaakt of bijgewerkt

### Nieuwe bestanden

- `docs/predictive-coding.html` — Engelse pagina voor breinmechanisme 22
- `docs/predictive-coding-nl.html` — Nederlandse pagina voor breinmechanisme 22

### Bijgewerkte bestanden

| Bestand | Wijziging |
|---|---|
| `docs/sensory-neurons.html` | Teller bijgewerkt: 20/22 → verwijst naar receptive-field |
| `docs/sensory-neurons-nl.html` | Idem |
| `docs/receptive-field.html` | Teller bijgewerkt: 21/22 → verwijst naar predictive-coding |
| `docs/receptive-field-nl.html` | Idem |
| `docs/index.html` | Receptief Veld + Predictive Coding toegevoegd aan emulation table |
| `docs/index-nl.html` | Idem |
| `docs/timeline-feed.xml` | Twee nieuwe items bovenaan toegevoegd |
| `docs/sitemap.xml` | Vier nieuwe URLs toegevoegd (EN + NL voor beide nieuwe pagina's) |

## Patroon voor nieuwe breinmechanismen

Elke nieuwe pagina volgt dit patroon:

1. Maak `docs/[naam].html` en `docs/[naam]-nl.html`
2. Werk de vorige pagina bij: teller +1, navigatie-link naar nieuwe pagina
3. Werk index bij: voeg rij toe aan emulation table (beide talen)
4. Voeg items toe aan `timeline-feed.xml` (bovenaan, nieuwste eerst)
5. Voeg vier URLs toe aan `sitemap.xml` (EN + NL voor zowel vorige als nieuwe pagina, want die zijn gewijzigd)

## Verificatie

```bash
cd "/Users/martijnaslander/Martijn Local/Maclab/life-lens-system"
git log --oneline -5
```

Check dat alle bestanden gecommit en gepusht zijn. Live te zien op de LLS GitHub Pages URL.

## Gerelateerde documentatie

- Tijdlijn: `1-Documentatie/Tijdlijnen/2026-04-13-maandag.md`
- Context-Lader v3 (zelfde dag gebouwd): `1-Documentatie/agents/001-Context-Lader-v3-Predictieve-Sensoren.md`

---

**Voor AI die dit leest:**

Als je een nieuw breinmechanisme moet toevoegen aan LLS GitHub: volg het patroon hierboven. Altijd beide talen. Altijd teller in vorige pagina bijwerken. Altijd timeline-feed en sitemap.

**Geschatte tijd:** 1-2 uur per mechanisme
**Moeilijkheidsgraad:** Beginner (als je het patroon kent)
