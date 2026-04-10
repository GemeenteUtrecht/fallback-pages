# Quick Reference - Versie Controleren

## 🚀 Snelle Gids voor Leveranciers

### Hoe controleer ik welke versie er draait?

#### Methode 1: Pagina Bron Inspecteren (Snelste)
1. Open de pagina in uw browser
2. Klik **rechts** → **"Paginabron weergeven"** (of `Ctrl+U` / `Cmd+U`)
3. Zoek naar: `<meta name="version"`
4. U ziet: `<meta name="version" content="1.0.0" />`
5. Datum staat in: `<meta name="version-date" content="2026-04-10" />`

**Voorbeeld output:**
```
<!-- Version Information -->
<meta name="version" content="1.0.0" />
<meta name="version-date" content="2026-04-10" />
<meta name="application-name" content="Fallback Page - Website" />
<!-- Fallback page: website | Version 1.0.0 | 2026-04-10 -->
```

#### Methode 2: Zoeken naar Comment (Alternative)
1. Open pagina bron (`Ctrl+U`)
2. Zoek naar: `"Fallback page:`
3. U ziet: `<!-- Fallback page: website | Version 1.0.0 | 2026-04-10 -->`

---

### Waar vind ik Release Informatie?

**Op GitHub:**
1. Ga naar: https://github.com/gemeenteUtrecht/fallback-pages
2. Klik **Releases** (rechtscenter)
3. U ziet alle versies met:
   - Versienummer
   - Release datum
   - Gedetailleerde changelog

---

### Versie Nummers Begrijpen

```
Versie Format: MAJOR.MINOR.PATCH
Voorbeeld:     1.0.0

1   = MAJOR   (grote wijzigingen)
0   = MINOR   (inhoudelijke wijzigingen)  
0   = PATCH   (kleine fixes)
```

---

### Nieuwe Versie Downloaden

```bash
# Optie 1: Klonen hele repository
git clone https://github.com/gemeenteUtrecht/fallback-pages.git

# Optie 2: Specifieke versie
git clone https://github.com/gemeenteUtrecht/fallback-pages.git
cd fallback-pages
git checkout v1.0.0

# Optie 3: ZIP Download
# Visit: https://github.com/gemeenteUtrecht/fallback-pages/releases
# Klik "Source code (zip)" op gewenste versie
```

---

### Changelog Controleren

Open `CHANGELOG.md` in repository om alle wijzigingen per versie te zien:

```
## [1.0.0] - 2026-04-10
### Added
- Initial release
- Version tracking

## [1.1.0] - 2026-04-15  
### Changed
- Updated opening hours
- Fixed contact form
```

---

## 📞 Bestanden Overzicht

| Bestand | Doel |
|---------|------|
| `website/index.html` | Fallback voor website |
| `loket/index.html` | Fallback voor online loket |
| `signalen/index.html` | Fallback voor Signalen app |
| `index.html` | Root redirect pagina |
| `CHANGELOG.md` | Volledige wijzigingenshistorie |
| `VERSIONING.md` | Gedetailleerde versioning documentatie |

---

## ⚡ Snelle Checklist

- [ ] Pagina bron geopend (`Ctrl+U` / `Cmd+U`)
- [ ] Meta tags gevonden met versienummer
- [ ] Datum genoteerd van `version-date`
- [ ] GitHub Releases gecheckt voor changelog
- [ ] Nieuwe versie gedownload indien nodig

---

**Vragen?** Raadpleeg `VERSIONING.md` voor volledige documentatie.
