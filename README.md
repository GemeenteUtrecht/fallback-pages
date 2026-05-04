# Fallback Pages

Deze repository bevat statische fallbackpagina’s voor de website en het digitaal loket van Gemeente Utrecht.

De pagina’s worden gebruikt wanneer de reguliere dienstverlening tijdelijk niet beschikbaar is, bijvoorbeeld door een storing, onderhoud of uitval van onderliggende systemen. In zo’n situatie kan via een router, hub of andere fallback-locatie een eenvoudige statische HTML-pagina worden getoond aan bezoekers.

Wil je weten hoe dit er uit ziet? Kijk dan naar de [front-end weergave](https://gemeenteutrecht.github.io/fallback-pages/).

## Doel

Het doel van deze repository is om een centrale plek te bieden voor fallbackpagina’s die:

- snel inzetbaar zijn bij verstoringen
- eenvoudig te hosten zijn als statische pagina
- duidelijke informatie geven aan bezoekers
- gebruikt kunnen worden voor zowel de website als het digitaal loket
- los inzetbaar zijn van backend-systemen

## Inhoud

De repository bevat momenteel:

- `index.html` – overzichtspagina / root landing page
- `website/index.html` – fallbackpagina voor de website (storing)
- `website/onderhoud/index.html` – fallbackpagina voor de website (gepland onderhoud)
- `loket/index.html` – fallbackpagina voor het digitaal loket (storing)
- `loket/onderhoud/index.html` – fallbackpagina voor het digitaal loket (gepland onderhoud)
- `signalen/index.html` – fallbackpagina voor Signalen (storing)
- `signalen/onderhoud/index.html` – fallbackpagina voor Signalen (gepland onderhoud)
- `README.md` – toelichting op doel, inhoud en gebruik

Per fallback-doel zijn er dus twee varianten: een **storing**-variant (onverwachte uitval) en een **onderhoud**-variant (gepland onderhoud, met een verwachte hersteltijd).

## Gebruik

Wanneer de website of het digitaal loket niet beschikbaar is, kan tijdelijk een statische pagina uit deze repository worden geserveerd vanuit een fallback-locatie.

De pagina kan bezoekers onder andere informeren over:

- de aard van de storing of onderbreking
- wat er tijdelijk niet beschikbaar is
- wat eventueel nog wel werkt
- alternatieve contactmogelijkheden
- het advies om het later opnieuw te proberen

## Gepland onderhoud

Naast de standaard storingspagina's bevat elke fallback-map een `onderhoud/index.html`. Deze variant wordt ingezet bij **gepland onderhoud**, wanneer vooraf bekend is wanneer de dienst weer beschikbaar is.

### Wanneer welke variant inzetten?

| Situatie | Pad |
|---|---|
| Onverwachte storing, hersteltijd onbekend | `website/index.html`, `loket/index.html`, `signalen/index.html` |
| Gepland onderhoud, hersteltijd bekend | `website/onderhoud/index.html`, `loket/onderhoud/index.html`, `signalen/onderhoud/index.html` |

De fallback-router/hub schakelt om door eenvoudig naar het andere pad te wijzen.

### Hersteltijd invullen vóór deploy

Elke onderhoudspagina bevat een `<time>`-element met een placeholder. Vul deze altijd in vóór deploy — anders ziet de bezoeker letterlijk `[VUL TIJD IN]` op de pagina staan (bewust zichtbaar zodat de stap niet vergeten wordt).

Zoek in de HTML naar de markering `BEHEERDER:` en pas twee dingen aan:

```html
<!-- BEHEERDER: pas datetime en de zichtbare tijd aan vóór deploy. Zie README.md → "Gepland onderhoud". -->
Wij verwachten dat de website het <time datetime="2026-05-04T18:00">[VUL TIJD IN]</time> weer doet.
```

1. **`datetime`-attribuut** – ISO 8601 formaat (`YYYY-MM-DDTHH:MM`), voor screenreaders en machines.
2. **Zichtbare tekst tussen `<time>...</time>`** – natuurlijke Nederlandse tekst voor de bezoeker, bijvoorbeeld `vandaag om 18:00` of `morgenochtend om 09:00`.

## GitHub Pages / preview

De root `index.html` kan worden gebruikt als overzichtspagina voor een GitHub Pages-preview van deze repository.

Daarmee ontstaat één centrale startpagina van waaruit de afzonderlijke fallbackpagina’s direct te openen zijn.

## Uitgangspunten

De fallbackpagina’s in deze repository zijn:

- statisch en lichtgewicht
- snel te deployen
- eenvoudig te beheren
- toegankelijk en duidelijk geschreven
- onafhankelijk van backend-systemen

## Versiebeheering

Dit project implementeert een volledig versiebeheersysteem via:

- **Meta Tags in HTML** – Elke pagina bevat versie- en datuminformatie in `<meta>`-tags
- **Semantic Versioning** – MAJOR.MINOR.PATCH format (bijv. 1.0.0)
- **CHANGELOG.md** – Centraal register van alle wijzigingen
- **GitHub Releases** – Opensbare release-geschiedenis met download links
- **GitHub Actions** – Automatische versie-update bij het maken van tags

### Huidige versie controleren

Open pagina bron en zoek naar:
```html
<meta name="version" content="1.0.0" />
<meta name="version-date" content="2026-04-10" />
```

Zie [VERSION-QUICK-REFERENCE.nl.md](./VERSION-QUICK-REFERENCE.nl.md) voor snelle instructies.

### Versie Releases

- Alle beschikbare versies op: [GitHub Releases](../../releases)
- Gedetailleerde changelog: [CHANGELOG.md](./CHANGELOG.md)
- Volledige versioning gids: [VERSIONING.md](./VERSIONING.md)

## Beheer

Aanpassingen aan teksten, contactgegevens of styling kunnen in deze repository worden bijgehouden, zodat altijd een actuele versie beschikbaar is voor inzet bij incidenten of onderhoud.

Nieuwe versies worden gemaakt via Git tags en GitHub Releases, waarbij alle pagina's automatisch worden voorzien van actuele versiegegevens.

## Opmerking

Deze repository is bedoeld als noodvoorziening en niet als vervanging van de reguliere website of het digitale loket.
