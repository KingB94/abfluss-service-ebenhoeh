# Abfluss-Service Ebenhöh – Website

Statische Website für Abfluss-Service Ebenhöh, Kimodenstraße 2, 85413 Hörgertshausen.

Live: https://abfluss-service-ebenhoeh.vercel.app

## Aufbau

- `index.html` – Startseite (Leistungen, Ablauf, Erste Hilfe, Bewertungen, FAQ, Kontakt)
- `impressum.html`, `datenschutz.html`, `404.html`
- `styles.css` – gesamtes Styling
- `archivo-var.woff` – Schrift Archivo (SIL Open Font License, siehe `OFL-Archivo.txt`), lokal gehostet
- `vercel.json` – saubere URLs und Sicherheits-Header (strikte CSP)

## Datenschutz

- keine Cookies, kein localStorage, kein Tracking
- kein JavaScript
- keine externen Ressourcen (Schrift lokal, keine eingebettete Karte – nur ein Link zu Google Maps)

## Deployment

Das Repository ist mit Vercel verbunden; jeder Push auf `main` wird automatisch veröffentlicht.
Kein Build-Schritt nötig (Framework Preset: „Other“, Output-Verzeichnis: Projektwurzel).

## Vor dem Livegang prüfen

- Impressum: ggf. USt-IdNr. und Handwerkskammer ergänzen
- Angaben (Inhaberin, Leistungen, Einsatzgebiet) mit dem Betrieb abstimmen
