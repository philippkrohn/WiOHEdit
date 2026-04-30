# Wir in Ostholstein – Web-Auftritt

AZAV-konformer Web-Auftritt der **Wir in Ostholstein gGmbH** für Vermittlungs­fachkräfte der Arbeitsagenturen und Jobcenter.

## Inhalt

- **Startseite** mit Hero, Maßnahmen-Übersicht, Trust-Bar, Team-Teaser und AZAV-Block
- **3 Maßnahmen** nach § 45 SGB III mit allen AZAV-Pflichtangaben
- **Team-Seite** mit pseudonymisierter Darstellung gemäß DSGVO Art. 4 Nr. 5
- **AZAV/Qualität** mit Trägerzertifikat, PDCA-Kreislauf, Beschwerde­management nach DIN ISO 10002
- **Kontakt** mit Anfrageformular für Vermittlungs­fachkräfte (Initialen statt Klarnamen)
- **FAQ** für AA/JC-Mitarbeitende
- **Impressum** und **Datenschutzerklärung**

## Technik

- Standalone-HTML (`index.html`) – nichts zu kompilieren, kein Build-Schritt
- React 18 + Tailwind CSS v4 via CDN
- Eigene SVG-Icon-Komponente (50 inline definierte Icons)
- Keine Cookies, kein Tracking, keine externen Karten- oder Analyse-Dienste

## Bilder

Im Ordner `images/` liegen alle Symbolbilder (KI-generiert) jeweils in:

- **WebP** in zwei Auflösungen pro Motiv (klein/groß) – moderne Browser laden automatisch die passende Größe
- **JPG** als Fallback für ältere Browser

Insgesamt 13 Motive (1 Hero, 1 Team-Gruppe, 6 Coach-Porträts, 3 Maßnahmen, 1 Standort, 1 QM/AZAV). Gesamtgröße aller Bildvarianten zusammen: ca. 4,5 MB.

## Lokal anschauen

Einfach `index.html` doppelklicken – die Datei lädt Bilder relativ aus `./images/`. Bei einigen Browsern (z. B. Safari mit strenger CORS-Policy) klappt das per Doppelklick nicht; dann lieber:

```
python3 -m http.server 8000
# dann http://localhost:8000 öffnen
```

## Deployment

Reine Static-HTML-Site, läuft auf jeder statischen Hosting-Plattform: GitHub Pages, Netlify, Cloudflare Pages, Vercel, Hetzner Webspace, all-inkl, Strato …

Die leere Datei `.nojekyll` sorgt dafür, dass GitHub Pages die Dateien unverändert ausliefert.

## Update-Workflow für GitHub Pages

Wenn du eine neue Version dieses ZIPs erhältst, einfach im GitHub-Repo:

1. **Add file → Upload files**
2. Alle Dateien plus den `images`-Ordner aus dem ZIP per Drag-and-Drop hineinziehen
3. „Commit changes" mit einer kurzen Notiz wie „Update Bilder + Texte"
4. Nach 30–90 Sekunden ist die Live-Seite aktualisiert

GitHub fragt nach, ob bestehende Dateien überschrieben werden sollen – ja.

## Inhaltliche Hinweise

Die aktuelle Version enthält **Platzhalter-Daten** für: Anschriften, Telefon, Trägerzertifikat-Nummer, Maßnahmen-Nummern, Eingliederungsquoten, Mitarbeiter-Initialen und -Funktionen.

Diese müssen vor Live-Schaltung durch echte Daten ersetzt werden. Alle Daten sind im `<script type="text/babel">`-Block der `index.html` zentral hinterlegt:

- `ANBIETER` – Trägerangaben
- `MASSNAHMEN` – die drei Maßnahmen mit allen AZAV-Pflichtangaben
- `TEAM` – die sechs Coaches (Initialen + Rolle + Qualifikation)
- `FAQ_AA_JC` – Fragen und Antworten

## Bilder sind KI-generiert

Alle Personenfotos sowie das Standort-Außenbild und das QM/AZAV-Bild sind KI-generierte Symbolbilder. Sie zeigen keine echten Mitarbeitenden und keine echten Räume – das passt zur Pseudonymisierungs-Strategie der Webseite und vermeidet Persönlichkeitsrechts-Konflikte. Auf der Team-Seite und in den Alt-Texten ist dies dezent kenntlich gemacht.

## Edit-Modus für Änderungswünsche

Auf jeder Seite findet sich unten rechts ein dezenter Schalter „Edit". Beim Anklicken werden alle änderbaren Elemente mit gelben/blauen Plaketten markiert, die ihre eindeutige **Adresse** zeigen (z. B. `home.hero.headline` oder `team.member.mk.rolle`).

**Workflow:**
1. Edit-Modus einschalten
2. Auf eine Plakette klicken — die Adresse wird in die Zwischenablage kopiert
3. Adresse plus ALT/NEU-Werte in `WUNSCHLISTE-VORLAGE.md` eintragen
4. Liste an Claude schicken — alle Änderungen werden in einem Rutsch eingearbeitet

Die Datei `REFERENZKARTE.md` enthält eine vollständige Liste aller Adressen, gegliedert nach Seiten — als Nachschlagewerk, falls ihr die Wünsche ohne aktivierten Edit-Modus sammeln wollt.

Der Edit-Modus bleibt nach dem Schließen des Browser-Tabs aktiv (gespeichert im Browser). Zum Ausschalten einfach erneut auf den Schalter klicken.

## Lizenz

© Wir in Ostholstein gGmbH. Alle Rechte vorbehalten.
