# Guide: Go High Level + ChatGPT Ads

> Schritt-für-Schritt-Anleitung, um für ein Angebot, das auf Go High Level (GHL) läuft, eine bezahlte Kampagne im ChatGPT Ads Manager (OpenAI) aufzusetzen — von der Produktvorbereitung über Conversion-Tracking und Landingpage bis zur laufenden Anzeige. Extrahiert aus mehreren Go-High-Level-Tutorials von Martin Dellwing.

## Konzept

Der komplette Ablauf in einem Satz: Du vereinfachst zuerst dein Angebot auf EINE klare Sache, richtest danach das Conversion-Tracking ein (bevor überhaupt eine Kampagne existiert), baust dann die Kampagne selbst, führst kalten Traffic über eine eigene Landingpage in GHL (nicht direkt aufs Angebot) und optimierst erst nach dem Launch weiter.

Die Reihenfolge ist bewusst so und sollte nicht vertauscht werden: Ohne funktionierendes Tracking kannst du später nicht auf Conversions optimieren, sondern nur auf Klicks — das ist deutlich ineffizienter und teurer.

## Warum das Ganze

Kalte Werbe-Traffic-Besucher kennen dein Angebot nicht und haben keine Geduld. Wenn dein Angebot zu komplex ist oder deine Landingpage direkt auf eine fremde Checkout-Seite verlinkt, verlierst du die meisten Interessenten sofort. Dieser Guide sorgt dafür, dass du das Angebot, das Tracking und die Landingpage VOR dem ersten Euro Werbebudget sauber aufgesetzt hast.

## Tools, die du brauchst

- **Go High Level (GHL)** — für Landingpage/Funnel, ggf. SaaS Configurator für gestaffelte Preise
- **ChatGPT Ads Manager** (OpenAI) — für die eigentliche Kampagne und das Conversion-Tracking
- **ChatGPT oder Claude** — als Sparringspartner, um deine Preisstruktur/Konfiguration gegenzuchecken
- Zugriff auf den `<head>`-Bereich deiner Website (für das Tracking-Pixel) — in GHL über die Seiteneinstellungen möglich

## Voraussetzungen

- Ein GHL-Account mit mindestens einer Seite/einem Funnel, den du bearbeiten kannst
- Ein klar abgrenzbares Angebot (siehe Schritt 1 — falls noch nicht vorhanden, ist das dein erster Schritt)
- Ein ChatGPT-Ads-Account mit hinterlegter Zahlungsmethode (aktuell nur Kreditkarte)
- Falls du Affiliate bist: Kenntnis darüber, ob du direkt auf die Checkout-Seite verlinken darfst — meistens nicht, siehe Schritt 4

---

## Schritt 1: Angebot vereinfachen, bevor du überhaupt Werbung schaltest

Der mit Abstand größte Fehler in diesem ganzen Workflow: zu viel in das beworbene Produkt zu packen. Kalter Traffic aus einer Anzeige hat null Kontext — ein einziges klares Feature/Ergebnis konvertiert deutlich besser als ein Bündel aus zehn Dingen, die du persönlich cool findest.

1. Wähle EIN Ding, das du bewirbst (z. B. ein Voice-AI-Website-Widget oder eine KI-generierte Website) — nicht mehrere gleichzeitig.
2. Falls du auf GHL ein SaaS-artiges Angebot mit gestaffelten Preisen aufbauen willst, nutze den **SaaS Configurator** (GHL-Pro-Plan, 497 $/Monat, nötig für vollautomatisiertes Reselling) und baue 2–3 Preisstufen in EINER Kategorie. Wichtig: Jede höhere Stufe muss mindestens dieselben Features enthalten wie die darunter — nie weniger.
3. Überlege, ob du eine kostenlose Testphase brauchst. Wenn dein Angebot bereits eine kostenlose interaktive Demo an anderer Stelle hat (z. B. ein Live-Widget, das der Besucher direkt auf der Landingpage testen kann), lass die Trial-Stufe weg — du willst den schnellstmöglichen Weg zur bezahlten Conversion, weil das Werbebudget ja schon läuft.
4. Bei nutzungs-/minutenbasierten Preisstufen (z. B. Voice-/AI-Features): kalkuliere mit gesunder Marge. Kostet dich eine Minute z. B. ~10 Cent, dann preise die Einstiegsstufe so, dass z. B. 100 Minuten eine komfortable Marge lassen. Die "Unlimited"-Stufe ganz oben bewusst hoch ansetzen — sie dient hauptsächlich dazu, Kunden Richtung mittlerer Stufe zu schubsen.
5. Lass deine fertige Preisstruktur von ChatGPT gegenchecken, bevor du sie final einrichtest — es kann über eine ganze Konversation hinweg Kontext zu deinem gesamten GHL-Setup halten und dient so als guter Sanity-Check-Partner.

---

## Schritt 2: Conversion-Tracking einrichten — BEVOR die Kampagne existiert

Das brauchst du zwingend, wenn du später auf Conversions statt nur auf Klicks optimieren willst. Ohne diesen Schritt siehst du zwar Klicks, aber nicht, ob daraus tatsächlich Kunden werden.

1. Gehe im ChatGPT Ads Manager auf **Conversions einrichten**, lege eine Datenquelle an und hole dir die Pixel-ID sowie das seitenweite Installations-Snippet.
2. Installiere dieses Snippet **seitenweit** (im `<head>`-Bereich, auf jeder Seite deiner Website). Das kannst du wörtlich einem KI-Page-Builder als Prompt geben: _"Füge folgenden OpenAI Ads Pixel seitenweit auf [Seite] in den Headbereich ein, sodass er auf jeder Seite gelesen wird. Direkt umsetzen und bestätigen."_ Danach veröffentlichen nicht vergessen.
3. **Datenschutz-Pflicht**: Sobald dieses Tracking-Pixel läuft, muss es in deinem Cookie-Banner offengelegt werden.
4. Lege zusätzlich ein **zweites, separates Conversion Event** speziell für den Kauf-/Abschluss-Moment an (z. B. "Abonnement erstellt" für ein Abo-Produkt). Dieses Event bekommt ein eigenes Pixel-Snippet, das NUR auf der Bestätigungs-/Danke-Seite (z. B. `/danke`) eingebaut wird — nicht seitenweit.
5. Teste die Einrichtung: Öffne im Ads Manager den Ereignisstream ("Ereignisstream anzeigen"), klicke "Abfrage starten", besuche in einem neuen Tab deine eigene Danke-Seite und prüfe danach den Stream — dort sollte ein erfolgreiches Event mit JSON-Payload auftauchen. Danach die Abfrage wieder pausieren.

---

## Schritt 3: Die Kampagne aufsetzen

Hier geht es um die konkreten Einstellungen beim Anlegen der Kampagne. Gehe sie in dieser Reihenfolge durch:

1. **Kampagnenziel wählen**: "Reichweite" streut zu breit für ein Vertriebsziel. "Klicks" ist die sichere Standardwahl, vor allem wenn du Affiliate bist und rechtlich nicht direkt auf eine Checkout-Seite verlinken darfst. "Conversions" setzt das Pixel-Setup aus Schritt 2 voraus und braucht eine Zielseite, die vollständig unter deiner Kontrolle steht.
2. **Targeting festlegen**: ChatGPT Ads erlaubt sehr granulares Targeting — bis auf einzelne Städte/Postleitzahlen (anders als Meta, das auch bei kleinen Gebieten noch breiter ausspielt). Prüfe vorher realistisch, ob dein Angebot bei so einem eng eingegrenzten kleinen Gebiet überhaupt ausgespielt würde.
3. **Custom Audiences beachten**: Für EWR/Schweiz-Kampagnen werden aktuell noch keine personalisierten Anzeigen unterstützt — Daten werden zwar schon gesammelt, sind aber noch nicht nutzbar.
4. **Plattform wählen**: iOS-App / Android-App / Web — orientiere dich daran, wo deine Zielgruppe tatsächlich ist, statt reflexhaft alle drei zu aktivieren.
5. **A/B-Test über Plattformen**: Wenn du vergleichen willst, welche Plattform bei dir wirklich performt, lege separate Kampagnen an, die jeweils NUR auf eine Plattform beschränkt sind — nicht mehrere Plattformen in einer Kampagne mischen.
6. **Budget festlegen**: Kein Enddatum setzen, solange die Kampagne läuft — laufen lassen und bei Erfolg skalieren, bei Mittelmaß unverändert lassen. Die Plattform kann an einem starken Tag bis zu das Doppelte deines Tagesbudgets ausgeben, aber die Gesamtausgabe über 7 Tage ist auf das 7-fache des Tagesbudgets gedeckelt (sie gleicht sich über die Woche selbst aus).
7. **Auto-Übersetzung ("Textanpassung") deaktivieren**, außer du willst deine Anzeige bewusst auch automatisch übersetzt Leuten zeigen, die die Sprache deiner Anzeige nicht sprechen.
8. **Gebotsstrategie wählen**: Für eine neue, ungetestete Kampagne "Ergebnisse maximieren" (automatisches Bieten) wählen, oder einen manuellen Max-CPC setzen. Falls manuell: Setze den Wert eher HÖHER als von der Plattform vorgeschlagen (z. B. vorgeschlagen 2–3 € → du setzt 4 €). Ein höheres Gebotsdach kauft dir früh bessere Sichtbarkeit, und die Plattform gibt sowieso selten das volle Maximum aus — sie optimiert nach unten, wenn möglich, und die Konkurrenz ist früh in der Regel niedriger als später.
9. **Kontexthinweise ausfüllen** (optionales Feld): Fülle es trotzdem explizit aus, besonders wenn deine Landingpage textarm ist — beschreibe deine tatsächliche Zielgruppe konkret (z. B. "Entscheider/Geschäftsführer", nicht "Mitarbeiter ohne Entscheidungsbefugnis"), damit die Plattform nicht rein aus dem Seiteninhalt raten muss.
10. **Tracking-URL-Parameter generieren lassen**: Lass ChatGPT oder Claude die Query-Parameter-Vorlage mit den dynamischen Platzhaltern der Plattform erstellen (z. B. `{ad_id}`, `{campaign_id}`) — wird nativ unterstützt, und eine KI macht das zuverlässiger als von Hand.

---

## Schritt 4: Landingpage bauen — nicht direkt aufs Angebot verlinken

Wenn du Affiliate bist (oder aus anderen Gründen kalten Traffic nicht direkt auf eine Checkout-Seite schicken darfst), baue eine EIGENE Zwischen-Landingpage in GHL, statt nach außen zu verlinken.

1. Nutze GHLs **AI Studio / Funnel AI**, um schnell einen ersten Entwurf zu generieren: Seiten → Funnels → Neuer Funnel → Funnel AI → Unternehmen/Nische, Ziel (Leads generieren / Termine bekommen / Arbeit präsentieren / Produkte verkaufen) und Tonalität auswählen. Damit entsteht innerhalb einer Minute eine komplette Seite mit Scroll-Animationen und stimmigem Farbschema.
2. Formuliere den Prompt für Funnel AI möglichst detailliert (Seitenziel, Affiliate-Hinweis in der Nähe der CTA-Buttons, eine Vertrauens-/Social-Proof-Leiste) — das liefert ein spürbar besseres Ergebnis als ein generischer Prompt.
3. Kosten einplanen: Eine vollständige KI-Generierung kostet ungefähr 0,70 € in Tokens; oft gibt es zusätzlich ein kostenloses Erst-Kontingent. Danach kosten die ersten 5 Generierungen pro Subaccount nichts, weitere ca. 99 Cent — günstig im Vergleich zur Zeit, die eine manuell gebaute Seite kosten würde.
4. Nutze anschließend den visuellen Editor, um Bilder/Texte anzupassen, sobald der KI-Entwurf nah dran ist — **visuelle Änderungen kosten keine Tokens**, nur eine vollständige (Neu-)Generierung durch die KI kostet.
5. Klicke immer auf **veröffentlichen/aktualisieren** und prüfe die Live-Vorschau, bevor du die Seite als Ziel-URL deiner Anzeige einträgst — eine Seite ist erst live, wenn sie veröffentlicht wurde.

---

## Schritt 5: Die Anzeige selbst erstellen

1. Beachte das harte Zeichenlimit im Titel (~50 Zeichen) — auf manchen Placements wird darüber hinaus abgeschnitten. Packe den wichtigsten Nutzen an den Anfang.
2. Formuliere die Headline konsequent um den tatsächlichen Nutzen für den Besucher (z. B. "Deine Website beantwortet Fragen selbst — rund um die Uhr", nicht einfach ein Feature-Name).
3. Erstelle mindestens 2 Anzeigenvarianten, um verschiedene Framings zu testen, statt nur den automatisch vorgeschlagenen Anzeigentext der Plattform zu übernehmen.
4. Lade auf Account-Ebene ein Firmenlogo hoch — fehlt es, wird das als Fehler/fehlendes Feld angezeigt.
5. Beachte: Aktuell wird ausschließlich per Kreditkarte abgerechnet.

---

## Schritt 6: Nach dem Launch

1. Rechne mit einer Prüf-/Freigabe-Verzögerung, bevor Anzeigen tatsächlich ausgespielt werden.
2. Rechne mit einer weiteren Verzögerung, bis überhaupt Impressionen erscheinen — das kann ~2 Stunden dauern, danach springt die Zahl oft von 0 auf mehrere Tausend Impressionen.
3. Erstelle relativ bald nach dem Launch mehrere Anzeigenvarianten (nicht nur 1–2), damit das System unterschiedliche konversationelle Kontexte zum Abgleich hat — das empfiehlt die Plattform selbst so.
4. **Skalieren, sobald profitabel**: Entweder dieselbe Nische auf andere Werbeplattformen ausweiten (Meta/Facebook/Instagram), oder dasselbe Nischen-Playbook für ANDERE Nischen wiederholen (gleiches Produkt, andere vertikale Landingpages, z. B. `/dachdecker`, `/immobilienmakler`) — enge Nischen haben meist weniger Werbe-Konkurrenz als der breite Markt.
5. Erwäge das Einrichten eines "Managed Agent" (ein KI-Agent mit API-Zugriff auf deinen Ads-Account), der die Performance nachts auswertet und dir morgens einen Report mit Änderungsvorschlägen liefert — Einrichtung über eine API-Verbindung in GHL, keine Programmierung nötig.
