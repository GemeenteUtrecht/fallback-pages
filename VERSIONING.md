# Versioning Strategy - Fallback Pages

Dit document beschrijft de versiebeheerstrategie voor de statische fallback-pagina's van Gemeente Utrecht.

## Overzicht

De versiebeheerstrategie bestaat uit vier componenten:

1. **Meta Tags in HTML** - Versie-informatie in de pagina's zelf
2. **GitHub Releases** - Publieke release-geschiedenis
3. **CHANGELOG.md** - Gedetailleerde wijzigingslog
4. **GitHub Actions** - Automatische versie-injectie

---

## 1. Meta Tags in HTML

Elke HTML-pagina bevat versie-informatie in de `<head>` sectie:

```html
<meta name="version" content="1.0.0" />
<meta name="version-date" content="2026-04-10" />
<meta name="application-name" content="Fallback Page - Website" />
<!-- Fallback page: website | Version 1.0.0 | 2026-04-10 -->
```

### Voordelen
- **Leveranciers kunnen direct zien welke versie er draait** door de bron te inspecteren (`Ctrl+U` / `Cmd+U`)
- Volledig onafhankelijk van servers of databases
- Werkt offline
- Eenvoudig uit te lezen voor monitors/dashboards

### Locaties
- `website/index.html` - Fallback voor website (storing)
- `website/onderhoud/index.html` - Fallback voor website (gepland onderhoud)
- `loket/index.html` - Fallback voor online loket (storing)
- `loket/onderhoud/index.html` - Fallback voor online loket (gepland onderhoud)
- `signalen/index.html` - Fallback voor Signalen (storing)
- `signalen/onderhoud/index.html` - Fallback voor Signalen (gepland onderhoud)
- `index.html` (root) - Root redirect pagina

> Per fallback-doel delen de storing- en onderhoudsvariant dezelfde versie. Eén release dekt beide varianten.

---

## 2. GitHub Releases & Tags

### Hoe een nieuwe versie uit te geven

#### Stap 1: Update CHANGELOG.md
Voeg een nieuw gedeelte toe aan het begin van `CHANGELOG.md`:

```markdown
## [1.1.0] - 2026-04-15
### Gewijzigd
- website/index.html: openingstijden aangepast
- loket/index.html: contactinformatie bijgewerkt

### Gecorrigeerd
- signalen/index.html: typo in URL gefixed
```

#### Stap 2: Maak een Git Tag
```bash
git tag -a v1.1.0 -m "Version 1.1.0 - April 2026"
git push origin v1.1.0
```

#### Stap 3: GitHub Release
GitHub automatisch detecteert de tag en stelt je in staat een release aan te maken:

1. Ga naar **GitHub** → **Releases**
2. Klik **"Draft a new release"**
3. Selecteer tag `v1.1.0`
4. Titel: `Version 1.1.0 - April 2026`
5. Beschrijving: Kopieer inhoud uit `CHANGELOG.md`
6. Klik **"Publish release"**

**De GitHub Actions workflow zal automatisch:**
- De versienummers in alle HTML-bestanden bijwerken
- De wijzigingen committen
- De commit pushen naar main

---

## 3. Semantic Versioning (SemVer)

We volgen **Semantic Versioning** voor versienummering: `MAJOR.MINOR.PATCH`

### Versionering in je context

```
MAJOR  (eerste getal)
├─ Groot ontwerp/herstructurering
├─ Voorbeeld: Volledige herindeling pagina
└─ → 2.0.0

MINOR  (tweede getal)
├─ Inhoudelijke wijzigingen
├─ Voorbeelden:
│  ├─ Nieuwe contactgegevens
│  ├─ Gewijzigde openingstijden
│  ├─ Bijgewerkte links
│  └─ Nieuwe secties
└─ → 1.1.0

PATCH  (derde getal)
├─ Kleine correcties / bugfixes
├─ Voorbeelden:
│  ├─ Typo's
│  ├─ CSS-aanpassingen
│  ├─ Breuken in links
│  └─ Spellingsfouten
└─ → 1.0.1
```

---

## 4. CHANGELOG.md

De `CHANGELOG.md` is het centrale register van alle wijzigingen. Dit bestand:

- **Ondersteunt leveranciers** om te zien wat er is veranderd
- **Helpt traceren** welke wijzigingen in welke versie zitten
- **Faciliteert communicatie** met stakeholders

### Format

Zie `CHANGELOG.md` in deze repository voor het volledige format.

---

## Workflow voor Leveranciers

### Huidige versie controleren

**Optie 1: Via browser bron**
1. Open de fallback pagina in browser
2. Druk `Ctrl+U` (Windows) of `Cmd+U` (macOS)
3. Zoek naar `meta name="version"`
4. Lees versienummer en datum af

**Optie 2: Via Releases pagina**
1. Ga naar GitHub → Releases
2. Zie alle releases met gedetailleerde changelogs

### Nieuwe versie ophalen

```bash
# Clone/pull repository
git clone https://github.com/gemeenteUtrecht/fallback-pages.git
cd fallback-pages

# Check beschikbare versies
git tag -l

# Switch naar specifieke versie
git checkout v1.0.0

# Of: download ZIP van release pagina op GitHub
```

---

## Automated Version Injection (GitHub Actions)

De `.github/workflows/update-version.yml` workflow voert automatisch de volgende acties uit:

1. **Detecteert gemaakte tag** (bijv. `v1.1.0`)
2. **Extraheert versienummer en huidige datum**
3. **Werkt alle HTML-bestanden bij** met:
   - Nieuw versienummer in meta tags
   - Nieuwe datum
   - Geupdateerde HTML-commentaar
4. **Commit en push** wijzigingen

**Voordeel:** Je hoeft versienummers niet handmatig in HTML aan te passen - dit gebeurt automatisch!

---

## Best Practices

### ✅ Do's
- ✅ Update `CHANGELOG.md` VOOR je een tag aanmaakt
- ✅ Gebruik semantic versioning consistent
- ✅ Schrijf duidelijke changelog-entries
- ✅ Maak releases in GitHub voor volledige tracering
- ✅ Laat leveranciers weten wanneer nieuwe versies beschikbaar zijn

### ❌ Don'ts
- ❌ Werk versienummers handmatig in HTML aan
- ❌ Skip changelog updates
- ❌ Maak tags zonder releases aan te maken
- ❌ Wijzig oude releases/tags

---

## Voorbeeld Workflow

### Scenario: Je wilt openingstijden updaten

```
1. Edit website/index.html met nieuwe openingstijden
   
2. Update CHANGELOG.md:
   ## [1.1.0] - 2026-04-15
   ### Gewijzigd
   - website/index.html: openingstijden aangepast (woensdag tot 15:00)

3. Commit wijzigingen:
   git add .
   git commit -m "Update opening hours"
   git push

4. Maak tag:
   git tag -a v1.1.0 -m "Version 1.1.0"
   git push origin v1.1.0

5. GitHub → Releases → "Publish release"
   (workflow voert nu automatisch versie-updates uit)

6. Leveranciers zien direct v1.1.0 in hun pagina's
```

---

## Ondersteuning

Voor vragen over versiebeheering, zie:
- `CHANGELOG.md` - Volledige historie
- GitHub Releases - Alle uitgegeven versies
- `.github/workflows/update-version.yml` - Automation details
