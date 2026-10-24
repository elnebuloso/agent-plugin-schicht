---
name: besenrein
description: >-
  Besenrein – eine Session-Übergabe (Handoff) gemeinsam mit dem Nutzer auflösen:
  Eintrag für Eintrag gegen den echten Stand prüfen und erledigen, als Aufgabe
  festhalten, dokumentieren oder verwerfen, bis die Datei gelöscht werden kann.
  Nur auf ausdrücklichen Aufruf (/besenrein). NICHT für den Tagesstart aus einer
  Übergabe (das ist moin) und nicht für das Schreiben einer Übergabe (das ist
  feierabend).
disable-model-invocation: true
---

# Besenrein: die Übergabe auflösen

Die Übergabe hat ihren Zweck erfüllt; was darin steht, soll an seinen dauerhaften Ort, damit
die Datei weg kann. Am Ende ist jeder Eintrag erledigt, als Aufgabe festgehalten, dokumentiert
oder bewusst verworfen – und die Übergabe wird gelöscht.

Die Handoff-Datei ist standardmäßig `docs/HANDOFF.md`. Hat der Nutzer beim Aufruf einen anderen
Pfad genannt, nimm den stattdessen.

Du änderst nichts ohne Freigabe des Nutzers – mit einer Ausnahme: VERWERFEN mit Beleg (Schritt
2b). Das bricht nicht die Regel, nichts eigenmächtig zu entsorgen: Gelöscht wird dabei nichts,
jede Verwerfung steht mit Beleg im Abschlussbericht, und die Datei löscht erst das Ja des
Nutzers.

## Kategorien

- **ERLEDIGEN:** noch relevant, klar umrissen, jetzt mit überschaubarem Aufwand machbar. →
  Umsetzen und verifizieren (Tests, Checks des Projekts).
- **AUFGABE:** noch relevant, aber zu groß, unklar oder außerhalb des Scopes. → Im
  Aufgabensystem des Projekts festhalten (Backlog, Issues, TODO-Datei – was das Projekt nutzt).
  Gibt es schon eine passende Aufgabe, dort ergänzen; sonst eine neue anlegen, verständlich ohne
  die Übergabe (Was, Warum, betroffene Dateien, Akzeptanzkriterien). Hat das Projekt kein
  Aufgabensystem, frag, wohin.
- **DOKUMENTIEREN:** dauerhaft gültiges Wissen. → An den Zielort aus der Karte (Schritt 1).
- **VERWERFEN:** erledigt, veraltet, überholt – oder steht schon dort, wo der Leser es braucht.

## Ablauf

1. **Übersicht und Zielorte.** Lies die Übergabe komplett. Zeige:
   - eine nummerierte Liste aller Einträge, je eine Zeile, ohne Bewertung;
   - eine Karte der Zielorte, abgeleitet aus dem Projekt: wohin Architektur, Testwissen,
     Betriebswissen, Entscheidungen, Arbeitsweise und offene Arbeit gehören. Fehlt ein Ort,
     schlag ihn vor.

   Warte auf das OK zu beidem.

2. **Je Eintrag** (oder je Block, siehe unten):
   a) Prüfe ihn gegen den echten Stand: Code, Tests, Git-Historie, Aufgaben, Doku. Glaub nicht
      der Formulierung in der Übergabe.
   b) Ist das Ergebnis VERWERFEN mit konkretem Beleg (Datei:Zeile, Commit, Aufgabe) und ohne
      sinnvolle Alternative: nicht fragen. Melde es in einer Zeile („Eintrag N verworfen: …“)
      und mach mit dem nächsten weiter.
   c) Sonst leg vor: Eintrag (kurz), Befund mit Fundstellen, Empfehlung mit Begründung, den
      konkreten Text oder die Änderung samt Zielort, und falls sinnvoll eine Alternative mit Vor-
      und Nachteil. Warte auf die Entscheidung.
   d) Setz sie um, committe (siehe Regeln), bestätige in einer Zeile und leg direkt den nächsten
      Eintrag vor.

   **Blöcke:** Einträge mit gleicher Kategorie und gleichem Zielort darfst du zusammen vorlegen,
   jeder mit Nummer, damit der Nutzer einzeln abweichen kann.

   **Nebenbefunde:** Stößt du beim Prüfen auf etwas, das nicht in der Übergabe steht, melde es
   gesondert und fass es erst nach Freigabe an.

3. **Abschlussbericht.** Eine Tabelle `| # | Eintrag | Kategorie | Ergebnis / Aufgabe / Doku-Ort |`
   für alles außer VERWERFEN; die verworfenen Einträge gebündelt nach Grund („Kommentar im Code:
   22, 26, 31“). Bestätige, dass kein Eintrag offen ist, und nenne ausdrücklich alles, was danach
   nur noch im Gespräch steht.

4. **Löschen.** Frag, ob die Übergabe gelöscht werden soll. Erst nach dem Ja.

## Regeln

- **So nah am Leser wie möglich:** Kommentar an der Codestelle vor Test vor Modul-Doku vor
  Entscheidungsdokument oder Regeldatei. Steht es dort schon, ist es VERWERFEN.
- **Kein Beleg, kein Direkt-Verwerfen.** Konntest du etwas nicht eindeutig prüfen, sag es und
  empfiehl lieber AUFGABE als VERWERFEN.
- **Commits:** einer je umgesetztem Eintrag oder Block, nach den Commit-Regeln des Projekts. Nie
  pushen, außer der Nutzer sagt es.
