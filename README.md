# No-Touch-Register · OT-Containment-Governance

Ein leichtgewichtiges, browserbasiertes Werkzeug zur Steuerung von Containment-Entscheidungen in industriellen OT-Umgebungen — als Begleitmaterial zum Fachbuch **„ISMS für die Industrie. Von ISO 27001 über NIS2 bis OT-Security“**.

Es ist die operative Schwester der [Crown-Jewels-Identifikation](https://sabinefroemling-tech.github.io/crown-jewels-companion/). Während das erste Werkzeug die kritischsten Assets identifiziert, beantwortet dieses die Frage, die in fast jedem IR-Playbook offenbleibt: **Wer darf im akuten OT-Vorfall was abschalten?**

## Was es macht

In der IT begrenzt der Reflex „im Zweifel isolieren“ den Schaden. In der OT kann genau dieser Reflex den Schaden erst auslösen — eine isolierte SPS in einem kontinuierlichen Prozess kann eine Charge zerstören oder einen Reaktor in einen unsicheren Zustand bringen. Dieses Muster ist das *Containment-Paradox* (Kap. 9.1).

Das No-Touch-Register ist keine separate Datenbasis. Es ist dieselbe Crown-Jewels-Liste, ergänzt um die Veto-Steuerung. Für jedes Crown Jewel wird festgelegt:

- **Veto-pflichtige Maßnahme** — die Aktion am Asset, die der SOC nicht eigenständig ausführen darf (Netzwerk-Isolation, Service-Restart, Account-Lockout von Service-Konten, Konfigurations- oder Firmware-Aktion).
- **Warum kein unilateraler SOC-Zugriff** — die Begründung (Operator verliert Sichtbarkeit, Gefahr für Safety, kontinuierlicher Prozess nicht einfach stoppbar, Kaskadierung im Verbund, Verlust des regulatorischen Datenstroms).
- **Sicherer Rückfall** — die vorab abgestimmte Sicherer-Zustand-Aktion, die bei Fristablauf greift (Umschalten auf redundanten Master, letzten gültigen Zustand halten, Wechsel auf Reserve-Schutzschema, lokale Pufferung).
- **Eskalationskette & Zeitfenster** — namentlich benannte Rollen mit harten Fristen (Vorlage: Schichtleiter 5 Min → Leittechniker 10 Min → Werksleiter 15 Min → Rückfall). Die Fristen werden auf numerische, monoton steigende Werte geprüft.
- **RACI je Maßnahme** — Accountable (Asset Owner / Werksleiter), Responsible (SOC), Consulted (CISO / ISB), Informed (Geschäftsleitung).

Davon abgegrenzt sind die **vorab freigegebenen Maßnahmen** (Monitoring vertiefen, Logs sichern, forensische Images, Sperrung kompromittierter Benutzerkonten, Isolation benachbarter IT-Systeme außerhalb des OT-Datenpfads). Diese führt der SOC eigenständig aus — die schnelle Klasse bleibt schnell. Damit entkräftet das Register den häufigsten Einwand, das Veto-Recht sei eine Geschwindigkeitsbremse (Kap. 9.5).

Ausgabe ist ein einseitiger, druckbarer **operativer Aushang** für SOC, Leitwarte und den Arbeitsplatz des OT Security Lead.

Die Methodik bildet das Verfahren aus dem Buch ab: Kap. 9.3 (No-Touch-Register, Tab. 9.1), Kap. 9.4 (RACI für Containment), Kap. 9.5 (Eskalationskette mit Zeitfenstern).

## Nutzung

Es ist keine Installation nötig. Die Datei `index.html` im Browser öffnen — oder die gehostete Version aufrufen. Alle Daten bleiben ausschließlich im Browser; es findet keine Datenübertragung statt (DSGVO-freundlich), und es wird nichts still gespeichert.

- **Crown-Jewels-JSON importieren** — übernimmt direkt die Assets aus dem Crown-Jewels-Tool; es werden nur jene mit der Klassifikation „Crown Jewel“ übernommen, RTO, Typ und Asset Owner vorbefüllt.
- **Speichern / Laden (JSON)** — der Arbeitsstand wird als Datei abgelegt und wieder eingelesen.
- **Export CSV** — vollständiger Audit-Export inklusive der vorab freigegebenen Maßnahmen.
- **Drucken / PDF** — der operative Aushang; für den Wand-Aushang ist die Druckansicht **A3 quer** empfohlen.

## Grenzen

Der Wert liegt nicht in der Grafik, sondern in der Disziplin davor (Kap. 9.3 / 9.4). Dieses Werkzeug ist das sichtbare Endprodukt eines methodisch sauberen Prozesses — nicht der Prozess selbst. Wer welches Asset mit welcher Frist und welchem benannten Eskalations-Empfänger auf die Liste setzt, ist Ergebnis der Crown-Jewels-Analyse (Kap. 3.5), eines Workshops mit der Anlagenleitung (Kap. 9.6) und der RACI-Entscheidungen (Kap. 9.4). Ein ausgefüllter Aushang ohne diesen vorausgehenden Abgleich erzeugt Scheinsicherheit.

Zwei Schritte bleiben außerhalb des Werkzeugs: den Sicherheits-Stopp im real ausgeführten IR-Playbook verankern und die OT-Spalte der RACI-Matrix korrigieren.

Außerdem setzt der sichere Rückfall einen autarken Inselbetrieb voraus: Wer keinen Island-Mode hat (Kap. 24.3), kann auch keinen geordneten sicheren Zustand definieren. Das Werkzeug ist eine Hilfe zur Workshop-Strukturierung und ersetzt weder den Workshop noch eine vollständige Risiko- oder Business-Impact-Analyse.

## Lizenz

© Sabine Frömling. Veröffentlicht unter [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/deed.de) — Namensnennung, nicht-kommerziell, keine Bearbeitungen. Details in [`LICENSE`](LICENSE).

## Autorin

**Sabine Frömling** — Unabhängige IT-Security- und Compliance-Beraterin (OT-Security, NIS2, ISO 27001, KRITIS).
[LinkedIn](https://www.linkedin.com/in/sabine-froemiing/)
