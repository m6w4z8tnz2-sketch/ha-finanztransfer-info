# Google-OAuth-Freigabe: Status und kostenlose Domain

Stand: 12.11.2026

## Bestätigter Stand

- [Öffentliche Homepage](https://m6w4z8tnz2-sketch.github.io/ha-finanztransfer-info/) auf GitHub Pages; Branch `main`, Verzeichnis `/(root)`.
- [Pages-Build vom 12.11.2026](https://github.com/m6w4z8tnz2-sketch/ha-finanztransfer-info/actions/runs/43240077156): **success**. Ein unabhängiger HTTP-Abruf der Live-Seite steht noch aus.
- `ha-finanztransfer.is-a.dev` ist **noch nicht registriert**; die Datei `is-a-dev/register/domains/ha-finanztransfer.json` war beim öffentlichen Lookup nicht vorhanden.
- Home Assistant, Banking-App, Google-OAuth-Client, Google Cloud und Tailscale-Callback bleiben unverändert.

## 1. is-a.dev-Domain registrieren

Die einfachste Registrierung benötigt **zunächst nur einen CNAME** auf GitHub Pages; die Google-Verifizierung erfolgt später. Die vollständige, auf unseren GitHub-Namen abgestimmte Vorlage liegt in `domain/ha-finanztransfer.json.template`.

1. Die drei bestehenden Seiten im privaten Browser prüfen.
2. https://github.com/is-a-dev/register öffnen und im eigenen GitHub-Konto auf **Fork** klicken.
3. Im Fork `domains/ha-finanztransfer.json` erstellen und die Vorlage **persönlich prüfen und übernehmen**.
4. Pull Request auf `is-a-dev/register` im Browser selbst erstellen, das dortige PR-Template ausfüllen, den öffentlichen Vorschaulink und einen selbst angefertigten Screenshot beifügen.
5. Die Domain gilt erst nach Annahme des Antrags und Veröffentlichung der DNS-Daten als verfügbar.
6. Danach unter [GitHub Pages](https://github.com/m6w4z8tnz2-sketch/ha-finanztransfer-info/settings/pages) als **Custom domain** `ha-finanztransfer.is-a.dev` eintragen und **Enforce HTTPS** aktivieren.

**Achtung:** Die [is-a.dev-Nutzungsbedingungen](https://github.com/is-a-dev/register/blob/main/TERMS_OF_SERVICE.md) stehen KI-erstellten PRs ausdrücklich ablehnend gegenüber. Der Antrag muss deshalb vom Kontoinhaber selbst nach eigener Prüfung übermittelt werden; die technische Website darf dagegen mit KI erstellt worden sein.

Quellen: https://docs.is-a.dev/quickstart/ und https://docs.is-a.dev/guides/github-pages/

## 2. Google Search Console

Nach aktiver Domain im Google-Konto des vorhandenen Cloud-Projekts https://search.google.com/search-console öffnen.

1. **URL-Präfix** auswählen, `https://ha-finanztransfer.is-a.dev/` eingeben.
2. Bestätigungsmethode **HTML-Tag** wählen und das `google-site-verification`-Meta-Tag bereitstellen. Das Tag ist ein öffentlicher Eigentumsnachweis, **kein Client-Secret**.
3. Dieses Tag in den `<head>` von `index.html` übernehmen und nach GitHub-PR/Merge veröffentlichen. Danach in Search Console bestätigen.
4. Das Tag dauerhaft erhalten. Falls Google ausdrücklich eine Domain-Property statt einer URL-Präfix-Property fordert, ist dafür eine zusätzliche **DNS-TXT-Bestätigung** mit Änderung beim Anbieter nötig.

Google: https://support.google.com/webmasters/answer/9008080

## 3. Google Auth Platform / Branding

Erst wenn die Domain funktioniert und verifiziert ist:

- Autorisierte Domain: `ha-finanztransfer.is-a.dev`
- Homepage: `https://ha-finanztransfer.is-a.dev/`
- Datenschutz: `https://ha-finanztransfer.is-a.dev/datenschutz.html`
- Nutzungsbedingungen: `https://ha-finanztransfer.is-a.dev/nutzungsbedingungen.html`

Zusätzlich sind alle registrierten OAuth-Redirect-Domains zu prüfen. Der bisherige lokale Callback `https://homeassistant.taild5d315.ts.net/local/ing_google_callback.html` kann von Google als **nicht selbst verifizierte** Domain beanstandet werden. Eine öffentliche Domain für die Homepage löst dieses Problem nicht automatisch.

**Keine ungeprüfte OAuth-Redirect-Änderung auf statische GitHub Pages:** Übertragene `code`-Parameter könnten in den Hosting-Logs erscheinen. Eine sichere Weiterleitungsarchitektur ist ein separater, sicherheitskritischer Arbeitsschritt.

Google: https://developers.google.com/identity/verification/authentication-verification

## Abnahmegrenzen

Vor dem produktiven, unbeaufsichtigten Betrieb müssen die Domainbestätigung, Google-Veröffentlichung, sichere Callback-Architektur, Banking-Lesetest und Drive-Upload separat bestätigt werden. Niemals Bankdaten, Tokens, OAuth Client-Secrets oder private Schlüssel ins öffentliche Repository eintragen.

**Keine Änderung an Home Assistant, kein Git Pull, Reload oder Neustart nötig.**
