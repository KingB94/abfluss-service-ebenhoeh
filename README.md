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
| `/` | 1 Einsatz: Signalgelb, Anthrazit, große Telefonnummer | `index.html`, `styles.css` |
| `/design-2` | 2 Kontur: dunkel, Foto, Kupfer | `design-2.html`, `design-2.css` |
| `/design-3` | 3 Werkstatt: Papier, Serife, Tannengrün | `design-3.html`, `design-3.css` |
| `/designs` | neutrale Vergleichsseite | `designs.html`, `designs.css` |

- `switcher.css` – Umschalter zwischen den Designs, reine Links
- `impressum.html`, `datenschutz.html`, `404.html` – nutzen das Design 1
- `images/` – Fotos für Design 2 und Vorschaubilder für `/designs`
- `archivo-var.woff`, `fraunces-var.woff2`, `plex-sans-*.woff2` – lokale Schriften (SIL Open Font License, siehe `OFL-*.txt`)
- `vercel.json` – saubere URLs, Sicherheits-Header (strikte CSP), noindex

Die Texte stehen in jeder Seite als HTML. Eine Änderung an Fakten oder Telefonnummer muss deshalb in `index.html`, `design-2.html` und `design-3.html` erfolgen. Design 1 und die beiden neuen Designs unterscheiden sich im Inhalt nur in zwei Punkten: Design 2 zeigt statt der Hausskizze ein Foto, und die Quellenangabe bei den Bewertungen verweist auf „den Link bei der Gesamtbewertung“.

## Datenschutz

- keine Cookies, kein localStorage, kein Tracking
- kein JavaScript
- keine externen Ressourcen (Schriften und Bilder lokal, keine eingebettete Karte – nur ein Link zu Google Maps)

## Bilder

| Datei | Motiv | Quelle | Lizenz |
|---|---|---|---|
| `images/deckel-*.webp` | Schachtdeckel, Viborg (Dänemark) | [W.carter, Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Manhole_cover_at_Viborg_Katedralskole.jpg) | gemeinfrei (PD-self) |
| `images/strahl-band-*.webp` | Reinigung eines Abflussschachts, Greenville (USA) | [City of Greenville, Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Storm_Drain_Cleaning_(53904492315).jpg) | Public Domain Mark |

Beide Fotos sind **Platzhalter** und zeigen nicht den Betrieb. Der Maps-Eintrag enthielt beim Abruf nur ein einziges Foto (abgesackter Schachtdeckel in einer Einfahrt), das nicht verwendbar ist. Für die Vergleichsseite liegen unter `images/vorschau-*.webp` Bildschirmfotos der drei Designs; sie müssen nach sichtbaren Änderungen neu erzeugt werden.

Der Betrieb hat nach bisherigem Stand kein öffentliches Logo. Design 2 und 3 nutzen deshalb nur den Namen als Wortmarke. Das runde Zeichen in Design 1 und `favicon.svg` wurde für die Website gezeichnet und stammt nicht vom Betrieb.

## Bestätigt und offen

| Angabe | Stand |
|---|---|
| Name, Adresse, Telefon, E-Mail-Adresse, Inhaberin | aus Version 1 übernommen, mit dem Betrieb abstimmen |
| Bewertung (4,6 aus 9) | aus Version 1 übernommen, vor dem Livegang auf Google Maps gegenprüfen |
| Erreichbarkeit rund um die Uhr, Einsatzgebiet, Leistungen | aus Version 1 übernommen, mit dem Betrieb abstimmen |
| Rezensionen | sinngemäß wiedergegeben und auf der Seite so gekennzeichnet |
| USt-IdNr., Handwerkskammer | offen, im Impressum ggf. ergänzen |
| Eigene Fotos, Logo | offen, beim Betrieb anfragen |

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

- Impressum: ggf. USt-IdNr. und Handwerkskammer ergänzen
- Angaben (Inhaberin, Leistungen, Einsatzgebiet) mit dem Betrieb abstimmen
- Zustimmung des Betriebs einholen
