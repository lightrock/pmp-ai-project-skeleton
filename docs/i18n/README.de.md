# Doctor Bones

Doctor Bones ist eine anbieterunabhängige Repository-Vorlage für KI-unterstützte Entwicklung.

Sie hilft dabei, Projekterinnerung im Repository zu halten, statt sie im Chat einzuschließen. Sie gibt dem Mensch/KI-Team eine gemeinsame Arbeitsdisziplin: Workorders, Playbooks, Beispiele, Checks, Übergaberegeln und Release-Readiness-Gewohnheiten.

## Sprachen

- [English](../../README.md)
- [Español](README.es.md)
- [Français](README.fr.md)
- Deutsch: diese Datei
- [Português do Brasil](README.pt-BR.md)

## Was das ist

Doctor Bones ist kein weiterer Coding-Agent.

Es ist eine repo-native Disziplinschicht, damit man KI-Assistenten und Coding-Agenten nutzen kann, ohne Absicht, Einschränkungen, Checks oder Projekthistorie zu verlieren.

Das Grundmodell ist:

```text
menschliche Absicht
→ die Foreground-KI klärt die Aufgabe
→ das Repository speichert dauerhafte Leitlinien
→ die Executor-KI erledigt begrenzte Arbeit
→ Checks prüfen, was prüfbar ist
→ der Abschluss verweist zurück auf die ursprüngliche Absicht
```

Betrachte die Foreground-KI als Planungs- und Architekturassistenten. Betrachte die Executor-KI als den Arbeiter mit Dateizugriff, Laufzeitumgebung, Tests und Commit/PR-Werkzeugen.

Das Repository ist die Gedächtnis- und Disziplinschicht zwischen beiden.

## Erste Schritte

1. Wenn du diese Vorlage kopiert hast, schreibe dieses README bald für dein echtes Projekt um.
2. Lies [`examples/README.md`](../../examples/README.md), um die Day-in-the-Life-Workflow-Beispiele zu sehen.
3. Lies [`readme_pmp.md`](../../readme_pmp.md) mindestens einmal und halte es griffbereit.
4. Lies [`AGENTS.md`](../../AGENTS.md), bevor du einen KI-Assistenten bittest, das Repository zu ändern.
5. Nutze eine Workorder für umfangreiche, mehrdateiige, architektursensible oder prozesssensible Arbeit.
6. Führe die verfügbaren Checks aus, bevor du Arbeit als abgeschlossen behandelst.

## Start-Prompt für die Foreground-KI

Ersetze `<Pfad zu deinem Repo>` durch den echten Pfad deines Repositories. Du kannst deine Foreground-KI auch bitten, dieses README für dein neues Projekt zu aktualisieren.

Wenn du einen neuen Chat oder Tab für dieses Repository startest, füge dies in die Foreground-KI ein:

```text
Du bist die Foreground-KI für <Pfad zu deinem Repo>

Der aktuelle Repository-Zustand ist wichtiger als Chat-Erinnerung. Prüfe den aktuellen Repository-Zustand, bevor du Architektur-Ratschläge gibst, Workorders schreibst oder Repo-Änderungen vorschlägst.

Lies zuerst README.md, examples/README.md, readme_pmp.md, AGENTS.md und die relevante Ordner-Anleitung. Identifiziere dann aktuellen Zustand, Ziel, Einschränkungen, Foreground/Executor-Entscheidung und den kleinsten nützlichen nächsten Schritt.
```

## Workorder-Abkürzung

Für umfangreiche Arbeit sprich mit der Foreground-KI, bis die Aufgabe klar ist, und sage dann:

```text
Create a workorder and also show it to me here.
```

Du kannst einen Link zur Workorder-Datei kopieren und deiner Executor-KI, die in einer Umgebung für dieses Repository arbeitet, sagen, dass sie diese ausführen soll.

Du kannst auch den Workorder-Text kopieren/einfügen, wenn du die Foreground-KI gebeten hast, ihn zuerst anzuzeigen. Halte diesen Block sauber: keine Zitate, Assistentennotizen, Erklärungen, zusätzlichen Links oder Kommentare innerhalb des Workorder-Texts.

## Checks

Führe dies vom Repository-Root aus, wenn verfügbar:

```text
python tools/pmp_check.py --area all
python -m pytest
```

Wenn ein Check fehlschlägt, füge die exakte Befehlsausgabe in die Foreground-KI ein und bitte um die kleinste sichere Korrektur.

## Über Doctor Bones

Doctor Bones ist eine KI-anbieterunabhängige Arbeitsdisziplin für KI-unterstützte Projekte.

Die Kurzfassung:

```text
Absicht erfasst
Umfang begrenzt
Einschränkungen bewahrt
Executor instruiert
Checks erforderlich
Abschluss an ursprüngliche Absicht zurückgebunden
```

Die vollständige Erklärung steht in [`readme_pmp.md`](../../readme_pmp.md).
