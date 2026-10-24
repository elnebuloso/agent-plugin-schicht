---
name: moin
description: >-
  Moin – Wiedereinstieg in laufende Arbeit zu Beginn einer Session: hinterlassene
  Übergabe (Handoff) übernehmen, gegen den echten Stand (git, Commits, erwähnte
  Dateien) abgleichen, Verständnis zeigen und den ersten Schritt vorschlagen.
  Nutze diesen Skill, wenn der Nutzer sich erst orientieren will – wo steht das
  Projekt, was war gestern, wie geht's weiter – bevor er eine konkrete Aufgabe
  gibt; also beim Tages- oder Pausen-Einstieg, der an früher Begonnenes anknüpft.
  Typische Formen: "Moin", "Guten Morgen", "morgen!", "neuer Tag", "nach der
  Mittagspause wieder da", /moin; "wo waren wir / wo stehen wir / wo haben wir
  gestern aufgehört"; "hast du nen Überblick"; "mach mich warm / startklar"; "lass
  uns weitermachen, wo wir aufgehört haben"; "lies dich in den Handoff / die
  Übergabe ein"; "was hat mein Gestern-Ich hinterlassen". Begrüßungswort optional
  – es zählt die Absicht des Wiedereinstiegs. NICHT zum Schreiben der Übergabe am
  Arbeitsende (das ist feierabend), nicht für ein komplett neues Vorhaben und
  nicht für einen bloßen Gruß ohne Wiedereinstieg.
---

# Moin: Session-Start – die Übergabe übernehmen

Moin! Das Gestern-Ich hat (vielleicht) eine Übergabe hinterlassen – Zeit, den
Arbeitsplatz zu übernehmen und ohne Reibung weiterzumachen.

Die Handoff-Datei ist standardmäßig `docs/HANDOFF.md`. Hat der Nutzer beim Aufruf
einen anderen Pfad genannt, nimm den stattdessen.

Der Leitgedanke: Du beginnst einen neuen Arbeitstag und liest, was dein
Gestern-Ich dir hinterlassen hat. Es war gründlich, aber nicht unfehlbar – und
seit dem Schreiben kann sich etwas verändert haben. Deshalb glaubst du der
Übergabe nicht blind, sondern gleichst sie mit der Wirklichkeit ab, bevor ihr
loslegt. Und du stürmst nicht eigenmächtig in die Arbeit: Du zeigst erst, dass
ihr vom Gleichen redet, schlägst den ersten Schritt vor – und wartest auf das Go.

## Ablauf

### 1. Die Übergabe lesen

Lies `docs/HANDOFF.md` (oder den genannten Pfad). Existiert die Datei nicht oder
ist sie leer, gibt es keine Übergabe – sag das kurz und frag, was heute ansteht.
Die restlichen Schritte entfallen dann; erfinde keinen Kontext, der nicht da ist.

Liegt stattdessen eine `HANDOFF.md` außerhalb von `docs/` (z. B. im Projekt-Root
aus einer früheren Session), übernimm sie nicht stillschweigend – das ist eine
neue Stolperfalle (siehe Schritt 2). Leg sie als Abweichung vor und frag, ob
du sie als Quelle nimmst und nach `docs/HANDOFF.md` ziehst.

### 2. Gegen die Realität prüfen

Das Gestern-Ich war gründlich, aber nicht unfehlbar – und vielleicht ist seitdem
etwas passiert. Gleiche die Übergabe mit dem tatsächlichen Stand ab:

- Git-Status und die letzten Commits – was ist seitdem passiert?
- die erwähnten Dateien und Codestellen – existieren sie, sehen sie aus wie
  beschrieben?

Die Übergabe enthält bewusst keinen Git-Stand. Neue Commits, ein Push oder der
Commit der Übergabe selbst sind deshalb keine Abweichung. Steht in einer älteren
Übergabe doch ein Git-Stand (SHA, Commit-Liste, „ahead of origin“), ignorier ihn –
maßgeblich ist, was git jetzt zeigt.

Alles, was nicht zusammenpasst, ist eine **neue Stolperfalle**: Beschriebenes,
das fehlt; Vorhandenes, das nicht erwähnt ist; Zustände, die anders sind als
dokumentiert. Glaub im Zweifel der Wirklichkeit, nicht dem Zettel. Leg jede
Abweichung mit deiner Einschätzung vor, **bevor du irgendetwas daran änderst** –
und warte auf die Entscheidung des Nutzers.

### 3. Verständnis zeigen

Fass in eigenen Worten kurz zusammen, wo ihr steht, was als Nächstes ansteht und
welche Entscheidungen noch offen sind. **Nicht die Übergabe nacherzählen** –
sondern zeigen, dass du sie verstanden hast. So sieht der Nutzer sofort, ob ihr
vom Gleichen redet, bevor es losgeht.

### 4. Den ersten Schritt vorschlagen

Nenn den konkreten ersten Handgriff für heute – klein genug, um direkt
anzufangen, sinnvoll genug, um Schwung zu holen. **Dann warte auf das Go.** Erst
danach wird gearbeitet; preschen ist nicht der Job dieses Schritts.
