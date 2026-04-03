# Fallback Pages

Deze repository bevat statische fallbackpagina’s voor de website en het digitaal loket van Gemeente Utrecht.

De pagina’s worden gebruikt wanneer de reguliere dienstverlening tijdelijk niet beschikbaar is, bijvoorbeeld door een storing, onderhoud of uitval van onderliggende systemen. In zo’n situatie kan via een router, hub of andere fallback-locatie een eenvoudige statische HTML-pagina worden getoond aan bezoekers.

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
- `webiste/index.html` – fallbackpagina voor de website
- `loket/index.html` – fallbackpagina voor het digitaal loket
- `README.md` – toelichting op doel, inhoud en gebruik
-  [WIP] `signalen/index.html` – fallbackpagina voor het digitaal loket

## Gebruik

Wanneer de website of het digitaal loket niet beschikbaar is, kan tijdelijk een statische pagina uit deze repository worden geserveerd vanuit een fallback-locatie.

De pagina kan bezoekers onder andere informeren over:

- de aard van de storing of onderbreking
- wat er tijdelijk niet beschikbaar is
- wat eventueel nog wel werkt
- alternatieve contactmogelijkheden
- het advies om het later opnieuw te proberen

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

## Beheer

Aanpassingen aan teksten, contactgegevens of styling kunnen in deze repository worden bijgehouden, zodat altijd een actuele versie beschikbaar is voor inzet bij incidenten of onderhoud.

## Opmerking

Deze repository is bedoeld als noodvoorziening en niet als vervanging van de reguliere website of het digitale loket.