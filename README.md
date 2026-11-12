# HA Finanztransfer – öffentliche Informationswebsite

Statische Informationswebsite für die **private Home-Assistant-Anwendung HA Finanztransfer**.
Sie ist von der lokalen Banking-App und deren vertraulichen Daten technisch getrennt.

## Inhalte

- `index.html`: öffentlich zugängliche Homepage mit Funktionsbeschreibung
- `datenschutz.html`: Datenschutzhinweise für Website und lokale Anwendung
- `nutzungsbedingungen.html`: Rahmen und Grenzen des privaten Einsatzes
- `assets/site.css`: lokale Darstellung ohne Drittanbieter-Skripte
- `docs/GOOGLE_OAUTH_FREIGABE.md`: geprüfte Schritte zur kostenlosen Domain und Google OAuth
- `domain/ha-finanztransfer.json.template`: **nicht direkt einreichbare** Vorlage für den DNS-Antrag

## Veröffentlichung

GitHub Pages für dieses Repository: **Settings → Pages → Deploy from a branch → main / (root)**.
Die Freigabe kann nicht allein durch einen Git-Commit aktiviert werden.

Nach Aktivierung vorläufige URL:
https://m6w4z8tnz2-sketch.github.io/ha-finanztransfer-info/

Geplante kostenlose Domain (noch nicht registriert):
`ha-finanztransfer.is-a.dev`.

Erst **nach bestätigter is-a.dev-Domainvergabe** diese Domain in den
GitHub-Pages-Einstellungen als Custom domain eintragen und HTTPS aktivieren.

## Datenschutz und Sicherheit

Dieses Repository ist **öffentlich**. Niemals Kontodaten, OAuth-Codes, Client-Secrets,
Refresh-Tokens, API-Keys oder die Google Cloud-Projektkonfiguration mit Geheimnissen
hier einchecken. Die öffentlichen Websites enthalten keine OAuth-Rückgabe und
dürfen nicht ohne gesonderte Prüfung als Redirect-URI verwendet werden.

Alle weiteren Schritte und Abnahmepunkte: [Google OAuth Freigabe](docs/GOOGLE_OAUTH_FREIGABE.md).
