# Google-OAuth-Freigabe: Status und kostenlose Domain

Stand: 12.11.2026

## Bestätigter Stand

- GitHub-Pages-Website: https://m6w4z8tnz2-sketch.github.io/ha-finanztransfer-info/
- Der [Pages-Build vom 12.11.2026](https://github.com/m6w4z8tnz2-sketch/ha-finanztransfer-info/actions/runs/43240077156) ist erfolgreich; ein unabhängiger HTTP-Abruf durch die Assistenz war technisch nicht möglich.
- `ha-finanztransfer.is-a.dev` ist **noch nicht beantragt oder zugeteilt**. Im öffentlichen is-a.dev-Registrierungsrepository wurde am 12.11.2026 keine gleichnamige Domain-Datei gefunden.
- Home Assistant, Banking-App, Google Cloud und Tailscale-Callback blieben unverändert.

## 1. is-a.dev – manuelle Domainregistrierung

**Verbindliche Anbieterregeln:** Die [Nutzungsbedingungen, Abschnitt 6](https://github.com/is-a-dev/register/blob/main/TERMS_OF_SERVICE.md) und [AGENTS.md](https://github.com/is-a-dev/register/blob/main/AGENTS.md) lehnen **KI-generierte Registrierungs-Pull-Requests** ausdrücklich ab. Deshalb darf die Assistenz weder die antragsbezogene Datei/Branch im Fork als fertigen Antrag erzeugen noch den PR für den Benutzer eröffnen. Der Kontoinhaber muss die Datei und den Antrag nach den [offiziellen Anleitungen](https://docs.is-a.dev/quickstart/) selbst erstellen und verstehen. Die nachfolgenden Werte sind **technische Fakten**, kein fertiger Einreichungstext.

### Vorgehen im iPhone-Browser

1. https://github.com/m6w4z8tnz2-sketch/register/tree/main/domains öffnen.
2. **Add file → Create new file** wählen (bei mobiler Ansicht ggf. Safari → Desktop-Website anfordern).
3. Dateinamen **`ha-finanztransfer.json`** festlegen. Direkt im Ordner `domains` anlegen.
4. Das [offizielle Domain-JSON-Beispiel](https://docs.is-a.dev/quickstart/) persönlich übertragen und dabei eintragen:
   - `owner.username`: `m6w4z8tnz2-sketch`
   - `records.CNAME`: `m6w4z8tnz2-sketch.github.io`
   - gemäß [PR-Template](https://github.com/is-a-dev/register/blob/main/.github/PULL_REQUEST_TEMPLATE.md) **ausreichende Kontaktdaten** im `owner`-Bereich ergänzen (z. B. eine bewusst öffentlich gemachte E-Mail-Adresse oder zulässige Plattformadresse). Ein GitHub-Benutzername allein wird möglicherweise nicht akzeptiert.
5. Datei in **eigenem Fork** committen; dafür muss noch kein PR erstellt werden.
6. Bei `is-a-dev/register` selbst einen PR eröffnen. Das **offizielle PR-Template vollständig** ausfüllen, die Vorschau-URL `https://m6w4z8tnz2-sketch.github.io/ha-finanztransfer-info/` sowie einen **selbst erstellten Screenshot** angeben. Keine Zugangsdaten einfügen.
7. Auf die Entscheidung der ehrenamtlichen Maintainer warten; eventuelle Rückfragen persönlich beantworten.

**Hinweis:** is-a.dev akzeptiert nur Websites, die hauptsächlich ein persönliches oder nichtkommerzielles Softwareprojekt darstellen. Der Betreiber entscheidet, ob diese Informationswebsite den Vorgaben genügt. Eine Zustimmung ist nicht garantiert.

Nach Annahme und DNS-Verfügbarkeit in [GitHub-Pages-Einstellungen](https://github.com/m6w4z8tnz2-sketch/ha-finanztransfer-info/settings/pages) als Custom Domain `ha-finanztransfer.is-a.dev` eintragen und **Enforce HTTPS** aktivieren. Erst dann ist der Abruf der drei Seiten über die eigene Domain sinnvoll zu testen.

Offizielle Nachweise:
- https://docs.is-a.dev/quickstart/
- https://docs.is-a.dev/domain-structure/
- https://docs.is-a.dev/guides/github-pages/
- https://github.com/is-a-dev/register/blob/main/.github/PULL_REQUEST_TEMPLATE.md

## 2. Google Search Console

Erst nach aktiver Domain im Google-Konto des bestehenden Cloud-Projekts https://search.google.com/search-console öffnen:

1. **URL-Präfix** wählen und `https://ha-finanztransfer.is-a.dev/` eintragen.
2. Verifizierung durch **HTML-Meta-Tag** auswählen. Das `google-site-verification`-Tag ist ein öffentlicher Eigentumsnachweis, kein OAuth-Secret.
3. Meta-Tag nach Prüfung über einen eigenen GitHub-PR im `<head>` von `index.html` eintragen und ausrollen.
4. Erst danach in Search Console die Bestätigung auslösen. Das Meta-Tag dauerhaft belassen.

Falls Google ausdrücklich eine Domain-Property verlangt, kann ein zusätzlicher DNS-TXT-Nachweis erforderlich werden.

Quelle: https://support.google.com/webmasters/answer/9008080

## 3. Google Auth Platform – Branding

Nach funktionierender und bestätigter Domain:

- Autorisierte Domain: `ha-finanztransfer.is-a.dev`
- Homepage: `https://ha-finanztransfer.is-a.dev/`
- Datenschutz: `https://ha-finanztransfer.is-a.dev/datenschutz.html`
- Nutzungsbedingungen: `https://ha-finanztransfer.is-a.dev/nutzungsbedingungen.html`

Den bestehenden Google-OAuth-Redirect
`https://homeassistant.taild5d315.ts.net/local/ing_google_callback.html`
separat überprüfen. Die Domain `ts.net` gehört nicht zum Projekt und kann wegen fehlender Domainbestätigung zum Hindernis werden. **Keine ungeprüfte Umstellung auf eine öffentliche Callback-Seite**, die vertrauliche OAuth-Codes in Logs offenlegen könnte.

Google: https://developers.google.com/identity/verification/authentication-verification

## Abnahmegrenzen

Domainvergabe, Search-Console-Nachweis, Google-OAuth-Veröffentlichung und sichere Callback-Architektur sind noch nicht abgenommen. Produktive ING-Abrufe und Google-Drive-Uploads werden damit **nicht** freigeschaltet.

**Für die reine Informationswebsite ist kein Git Pull, kein HA-Reload und kein Neustart nötig.**
