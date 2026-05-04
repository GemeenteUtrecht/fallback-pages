# Wijzigingenslog

Alle opmerkelijke wijzigingen aan de Fallback Pages worden in dit bestand bijgehouden.

Dit bestand volgt het format van [Keep a Changelog](https://keepachangelog.com/nl-NL/1.0.0/)
en dit project volgt [Semantic Versioning](https://semver.org/lang/nl/).

## [1.2.0] - 2026-05-04

### Toegevoegd
- `website/onderhoud/index.html`: onderhoudsvariant voor de website-fallback
- `loket/onderhoud/index.html`: onderhoudsvariant voor de loket-fallback
- `signalen/onderhoud/index.html`: onderhoudsvariant voor de Signalen-fallback
- `<time>`-element met `datetime`-attribuut voor de verwachte hersteltijd op elke onderhoudspagina (toegankelijk en machine-leesbaar)
- README-sectie "Gepland onderhoud" met instructies voor beheerders

### Gewijzigd
- `index.html` (root): overzichtspagina toont nu zowel de storing- als de onderhoudsvariant per fallback-doel
- `VERSIONING.md`: locatie-overzicht uitgebreid met onderhoudspagina's
- `VERSION-QUICK-REFERENCE.nl.md`: bestanden-overzicht uitgebreid met onderhoudspagina's

## [1.0.0] - 2026-04-10

### Toegevoegd
- Eerste release van fallback pages voor Gemeente Utrecht
- website/index.html: Fallback pagina voor website
- loket/index.html: Fallback pagina voor online loket
- signalen/index.html: Fallback pagina voor Signalen applicatie
- Versie meta tags en tracking voor alle pagina's
- Semantic versioning strategie

### Opmerking
- Dit zijn statische HTML pagina's die op elke webserver kunnen worden gedeployed
- Elke pagina bevat versie-informatie in meta tags voor eenvoudige identificatie
- CSS is inline ingebed voor portabiliteit en offline functionaliteit
- Alle pagina's voldoen aan toegankelijkheidsstandaarden (WCAG conform)
