# Abfluss-Service Ebenhöh – Website

Statischer Website-Entwurf für Abfluss-Service Ebenhöh, Kimodenstraße 2, 85413 Hörgertshausen, in drei Design-Varianten.

Live: https://abfluss-service-ebenhoeh.vercel.app
Link zum Verschicken: https://abfluss-service-ebenhoeh.vercel.app/designs

## Status: Entwurf, nicht indexiert

Der Entwurf läuft unter dem echten Namen und den echten Kontaktdaten des Betriebs, ohne bestätigten Auftrag. Er ist über den Link erreichbar, aber für Suchmaschinen gesperrt:

- `robots.txt` mit `Disallow: /`
- Header `X-Robots-Tag: noindex, nofollow` für alle Pfade (`vercel.json`)
- `<meta name="robots">` auf Startseite und Design-Seiten

## Aufbau

| Seite | Design | Dateien |
|---|---|---|
| `/` | 1 Einsatz: Fahrzeugblau, Anthrazit, große Telefonnummer | `index.html`, `styles.css` |
| `/design-2` | 2 Kontur: Anthrazit, Fahrzeugfoto, Hellblau | `design-2.html`, `design-2.css` |
| `/design-3` | 3 Werkstatt: heller Grund, Serife, Logoblau | `design-3.html`, `design-3.css` |
| `/designs` | neutrale Vergleichsseite | `designs.html`, `designs.css` |

- `switcher.css` – Umschalter zwischen den Designs, reine Links
- `impressum.html`, `datenschutz.html`, `agb.html`, `404.html` – nutzen das Design 1
- `images/` – Fahrzeugfotos, Logo und Vorschaubilder für `/designs`
- `archivo-var.woff`, `fraunces-var.woff2`, `plex-sans-*.woff2` – lokale Schriften (SIL Open Font License, siehe `OFL-*.txt`)
- `vercel.json` – saubere URLs, Sicherheits-Header (strikte CSP), noindex

Die Texte stehen in jeder Seite als HTML. Eine Änderung an Fakten oder Telefonnummer muss deshalb in `index.html`, `design-2.html` und `design-3.html` erfolgen. Design 1 und die beiden neuen Designs unterscheiden sich im Inhalt nur in zwei Punkten: Design 2 zeigt statt der Hausskizze ein Heckfoto des Fahrzeugs, und die Quellenangabe bei den Bewertungen verweist auf „den Link bei der Gesamtbewertung“.

## Datenschutz

- keine Cookies, kein localStorage, kein Tracking
- kein JavaScript
- keine externen Ressourcen (Schriften und Bilder lokal, keine eingebettete Karte – nur ein Link zu Google Maps)

## Farben und Logo

| Farbe | Wert | Herkunft |
|---|---|---|
| Anthrazit | `#343636` | Logo |
| Logoblau | `#007096` | Pfeile im Logo |
| Fahrzeugblau | `#86b3f3` | Beschriftung Einsatzfahrzeug |
| Rot | `#c8323a` | Schriftzug EBENHÖH, Visitenkarte |
| Reflexgelb | `#dee410` | Streifen am Fahrzeug, nur Design 1 |

`images/logo.svg` und `favicon.svg` (nur das Zeichen) sind nach dem Logo und dem Heckfoto als Vektor nachgezeichnet, weil vom Betrieb nur eine PNG-Datei mit 99 × 93 px vorliegt. Der Schriftzug ist aus Archivo gesetzt und weicht leicht vom Original ab. Falls der Betrieb eine Vektordatei hat, diese bevorzugen.

## Bilder

| Datei | Motiv | Quelle |
|---|---|---|
| `images/fahrzeug-seite-*.webp`, `images/fahrzeug-breit-*.webp` | Einsatzfahrzeug von der Seite | Abfluss-Service Ebenhöh |
| `images/fahrzeug-heck-*.webp` | Einsatzfahrzeug von hinten | Abfluss-Service Ebenhöh |

Der Betrieb will noch aktuelle Fotos liefern. Für die Vergleichsseite liegen unter `images/vorschau-*.webp` Bildschirmfotos der drei Designs; sie müssen nach sichtbaren Änderungen neu erzeugt werden.

## Bestätigt und offen

| Angabe | Stand |
|---|---|
| Telefon, Mobilnummer, E-Mail-Adresse, Leistungen, 24-Stunden-Dienst | bestätigt durch Fahrzeugbeschriftung und E-Mail des Betriebs (1. 11. 2026) |
| Inhaberin Rosa Ebenhöh, 85413 Hörgertshausen | bestätigt durch E-Mail des Betriebs |
| Straße Kimodenstraße 2, Einsatzgebiet | aus Version 1 übernommen, mit dem Betrieb abstimmen |
| Bewertung (4,6 aus 9) | aus Version 1 übernommen, vor dem Livegang auf Google Maps gegenprüfen |
| Rezensionen | sinngemäß wiedergegeben und auf der Seite so gekennzeichnet |
| USt-IdNr., Handwerkskammer | offen, im Impressum ggf. ergänzen |
| AGB | Wortlaut des Scans, nur Inhaberin und Ort geändert; rechtlich veraltet, siehe unten |
| Neue Fotos | kommen vom Betrieb |

## Deployment

Das Repository ist mit Vercel verbunden; jeder Push auf `main` wird automatisch veröffentlicht.
Kein Build-Schritt nötig (Framework Preset: „Other“, Output-Verzeichnis: Projektwurzel).

## Design festlegen

1. Gewähltes Design zur Startseite machen: dessen HTML nach `index.html` übernehmen und `canonical` sowie die JSON-LD-Daten aus dem bisherigen `index.html` in den `<head>` einsetzen.
2. Die nicht gewählten `design-*`-Dateien sowie `designs.html`, `designs.css`, `switcher.css` und `images/vorschau-*.webp` löschen, nicht mehr benötigte Schriften ebenfalls.
3. In der Startseite `<nav class="switcher">` und den Verweis auf `switcher.css` entfernen. Wortmarken-Link auf `/` setzen.
4. Rechtstexte an das gewählte Design anpassen: Stylesheet und Kopfzeile in `impressum.html`, `datenschutz.html` und `404.html` tauschen sowie Schriften und Bildnachweis im Impressum aktualisieren.
5. `noindex` aufheben: `X-Robots-Tag` aus `vercel.json` und `<meta name="robots" content="noindex, nofollow">` aus der Startseite entfernen, in `robots.txt` wieder `Allow: /` und die Zeile `Sitemap: https://abfluss-service-ebenhoeh.vercel.app/sitemap.xml` eintragen.

## Vor dem Livegang prüfen

- AGB rechtlich prüfen lassen: Der Text stammt aus der Zeit vor 2002 („Vollkaufmann“, „Wandelung“, „zugesicherte Eigenschaft“, „Diskontsatz der Deutschen Bundesbank“), die Haftungsausschlüsse in Ziffer 5 und 6 und der Mindestzins von 11 % sind gegenüber Privatkunden kritisch. In Ziffer 7 steht vermutlich versehentlich „Arbeitnehmer“ statt „Auftragnehmer“.
- Impressum: ggf. USt-IdNr. und Handwerkskammer ergänzen
- Angaben (Inhaberin, Leistungen, Einsatzgebiet) mit dem Betrieb abstimmen
- Zustimmung des Betriebs einholen
