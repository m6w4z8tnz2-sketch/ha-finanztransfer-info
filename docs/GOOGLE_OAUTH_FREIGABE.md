# Google OAuth – Freigabe und Domain (Stand: 12.11.2026)

## Ziel und Grenzen

Kostenfreie, öffentlich zugängliche Informationswebsite für die private HA-Anwendung.
Die vorhandene Banking-/Google-OAuth-Konfiguration bleibt unverändert, bis die neue
Domain und alle Redirect-Domains tatsächlich geprüft sind.

**Noch nicht erledigt durch GitHub-Commits:** GitHub Pages aktivieren; is-a.dev-Domain
beantragen und genehmigen lassen; Google Search Console bestätigen; Google Auth
Platform ändern; OAuth-Markenprüfung/Produktivfreigabe erreichen.

## 1. GitHub Pages aktivieren

1. https://github.com/m6w4z8tnz2-sketch/ha-finanztransfer-info/settings/pages
2. Unter **Build and deployment** Quelle **Deploy from a branch** wählen.
3. **main**, **/(root)** auswählen und **Save**.
4. Unter https://m6w4z8tnz2-sketch.github.io/ha-finanztransfer-info/ die
   Startseite und beide Unterseiten vollständig im privaten Browser testen.

## 2. Domain bei is-a.dev beantragen

1. Nach aktivierter Website eine Domainverifizierung in der Google Search Console
   vorbereiten: https://search.google.com/search-console
2. Als Domain-Property `ha-finanztransfer.is-a.dev` wählen und den von Google
   angezeigten TXT-Wert kopieren. Dies ist ein öffentlicher DNS-Nachweis,
   **kein OAuth Client-Secret**.
3. `domain/ha-finanztransfer.json.template` kopieren, TXT-Platzhalter durch
   den vollständigen `google-site-verification=...`-Wert ersetzen und als
   `domains/ha-finanztransfer.json` in den eigenen Fork von
   https://github.com/is-a-dev/register übertragen.
4. GitHub Pull Request an `is-a-dev/register` erstellen, Website-Vorschau
   und öffentlich erreichbare URL hinzufügen. is-a.dev prüft selbst und
   entscheidet über die Registrierung. Die URL steht vorher nicht zur Verfügung.
5. is-a.dev erlaubt die Kombination von CNAME und TXT **nur bei aktivem Proxy**;
   deshalb steht `proxied: true` in der Vorlage.
6. Nach Merge/Propagation unter Repository → Settings → Pages → Custom domain
   `ha-finanztransfer.is-a.dev` eintragen, **Enforce HTTPS** aktivieren.
7. Website, alle Unterseiten und Google Search Console Domain-Bestätigung prüfen.

Quelle: https://docs.is-a.dev/quickstart/
https://docs.is-a.dev/guides/github-pages/
https://docs.is-a.dev/faq/

## 3. Google Auth Platform (nicht vor bestätigter Domain)

Im bestehenden Google Cloud-Projekt unter Google Auth Platform → Branding:

- Homepage: `https://ha-finanztransfer.is-a.dev/`
- Privacy Policy: `https://ha-finanztransfer.is-a.dev/datenschutz.html`
- Terms: `https://ha-finanztransfer.is-a.dev/nutzungsbedingungen.html`
- Autorisierte Domain für diese URLs: `ha-finanztransfer.is-a.dev`

Bei Verifizierung alle weiteren autorisierten Domains/Redirects kontrollieren.
Insbesondere ist der bisherige **private Tailscale-Callback**
`https://homeassistant.taild5d315.ts.net/local/ing_google_callback.html`
gesondert zu bewerten: `ts.net` steht nicht unter eigener Domainhoheit.
Google kann dessen Domainverifizierung verlangen. **Die neue Homepage allein
behebt diesen möglichen Blocker nicht.**

Weder den vorhandenen Callback noch den aktiven OAuth-Client vorschnell
auf eine öffentliche Seite umstellen: Ein Redirect, der OAuth-Codes oder
Tokens öffentlich sichtbar macht, wäre ein Sicherheitsproblem.
Bei einer anderen Redirect-Architektur zuerst einen eigenen Review
der HA-App und des sicheren Codes-austausch-Prozesses durchführen.

Der vorgesehene `drive.file`-Scope ist laut Google-Drive-API-Dokumentation
nicht sensitiv, trotzdem kann eine Branding-Prüfung nötig sein.
Eine Freigabe kann nicht durch die bloße Bereitstellung einer Privacy-Seite
garantiert werden.

Quellen:
- https://developers.google.com/identity/verification/authentication-verification
- https://developers.google.com/workspace/drive/api/guides/api-specific-auth
- https://developers.google.com/identity/protocols/oauth2/policies

## 4. Nachweise vor produktivem Dauerbetrieb

- Website/Datenschutzhinweise unter endgültiger Domain abrufbar
- Domain von is-a.dev und Google Search Console bestätigt
- OAuth-Status **In Produktion** und notwendige Markenprüfung abgeschlossen
- Google-OAuth-Callback und alle registrierten Domains zulässig und sicher
- CSV-Export/Google Picker/Upload der HA-App separat getestet
- Bank- und Google-Autorisierung nur nach ausdrücklicher Betreiberfreigabe
- Kein Geheimnis in GitHub, Website oder Logs; keine unbeabsichtigte Löschung

**Kein Git Pull, Home-Assistant-Reload oder HA-Neustart für diese Website nötig.**
