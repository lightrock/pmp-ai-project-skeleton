Die öffentliche Einführung findest du auf der [Doctor Bones GitHub Pages Site](https://lightrock.github.io/drbones/).

# Doctor Bones

Doctor Bones ist eine anbieterunabhängige Repository-Vorlage für KI-unterstützte Entwicklung.

Sie hilft dir, Projekterinnerung im Repository zu halten, statt sie im Chat einzuschließen. Sie gibt deinem Mensch/KI-Team eine gemeinsame Arbeitsdisziplin: Workorders, Playbooks, Beispiele, Checks, Übergaberegeln und Gewohnheiten für Release-Bereitschaft.

Die Idee ist: Wann immer du ein neues Projekt startest, starte mit einem Doctor Bones.

Du musst deine Kopie dieser Vorlage nicht unbedingt auf deinen lokalen PC oder in deine Agentenumgebung holen, um sie zu nutzen. Doctor Bones trägt seine kognitive Architektur im Repository selbst. Wenn du die Startanweisungen unten befolgst, sollte deine Foreground-KI genug Projektverständnis haben, um aus Repository-Leitlinien, Beispielen, Playbooks, Checks und Übergaberegeln heraus zu denken.

Standardmäßig muss nichts im traditionellen Sinn irgendwo "laufen", und du musst nicht unbedingt einen Executor wie Codex aufrufen. Richte deine Foreground-KI zuerst auf die passende Doctor-Bones-basierte Repository-Instanz aus. Nutze einen Executor nur dann, wenn die Aufgabe Dateiänderungen, eine Laufzeitumgebung, Checks, Commits oder Pull Requests braucht.

## Mehr zur Idee

Bevor die KI programmiert, bring dem Repository bei zu sprechen. Bevor die KI behauptet, fertig zu sein, definiere, was fertig bedeutet. Bevor die KI empfiehlt, trenne Beleg von Schlussfolgerung. Bevor die KI patcht, definiere Autorität, Verifikation und Grenzregeln.

Können wir repository-native Standards definieren, denen Cursor, Codex, Claude Code, Copilot... und GitHub-Bots folgen sollten?

Können wir es leicht machen, das Ganze an deine konkreten Bedürfnisse anzupassen?

## In Arbeit / TODO / ZU ERLEDIGEN

Siehe [TODO.md](../../TODO.md) für die grobe Arbeitsliste dessen, was noch zu Repository-Dateien, Schemas, Rubriken, Beispielen, Checks und Integrationszielen werden muss.

## Sprachen

- [English](../../README.md)
- [Español](README.es.md)
- [Français](README.fr.md)
- Deutsch: diese Datei
- [Português do Brasil](README.pt-BR.md)
- [हिन्दी](README.hi.md)

## Was das ist

Es ist eine repository-native Disziplinschicht, um KI-Assistenten und Coding-Agenten zu nutzen, ohne Absicht, Einschränkungen, Checks oder Projekthistorie zu verlieren.

Das Grundmodell ist:

```text
menschliche Absicht
→ die Foreground-KI klärt die Aufgabe
→ das Repository erfasst dauerhafte Leitlinien
→ die Executor-KI führt begrenzte Arbeit aus
→ Checks prüfen, was geprüft werden kann
→ der Abschluss verweist zurück auf die ursprüngliche Absicht
```

Betrachte die Foreground-KI als Planungs- und Architekturassistenten. Betrachte die Executor-KI als den Arbeiter mit Dateizugriff, Laufzeitumgebung, Tests und Commit/PR-Werkzeugen.

Das Repository ist die Gedächtnis- und Disziplinschicht zwischen beiden.

## Erste Schritte

1. Wenn du diese Vorlage kopiert hast, schreibe dieses README bald für dein echtes Projekt um.
2. Lies [`examples/README.md`](../../examples/README.md), um die Day-in-the-Life-Workflow-Beispiele zu sehen.
3. Lies [`readme_pmp.md`](../../readme_pmp.md) mindestens einmal und halte es griffbereit.
4. Lies [`AGENTS.md`](../../AGENTS.md), bevor du einen KI-Assistenten bittest, das Repository zu ändern.
5. Nutze eine Workorder für substanzielle, mehrere Dateien betreffende, architektursensible oder prozesssensible Arbeit.
6. Führe die verfügbaren Checks aus, bevor du Arbeit als abgeschlossen behandelst.

## Prozessgrenze

Erstelle deine Projekt-Workorders nicht im öffentlichen Doctor-Bones-Quellrepository, außer du trägst absichtlich zu Doctor Bones selbst bei.

Für dein eigenes Projekt erstelle oder nutze zuerst dein eigenes Repository aus dieser Vorlage. Richte dann deine Foreground-KI auf die URL dieses Projekt-Repositorys aus und erstelle dort die Workorders.

Nutze `lightrock/drbones` als Quellvorlage, Referenzimplementierung und Upstream-Projekt. Nutze dein kopiertes Doctor-Bones-basiertes Repository als den Ort, an dem Projekterinnerung, Workorders, Lessons Learned und projektspezifische Änderungen leben.

## Start-Prompt für die Foreground-KI

Dieser Prompt ist für ein Repository gedacht, das aus der Doctor-Bones-Vorlage erstellt wurde. Ersetze nach dem Kopieren dieser Vorlage `<your project repository URL>` durch die URL deines eigenen Projekt-Repositorys.

Wenn du einen neuen Chat oder Tab für dein Projekt-Repository startest, füge dies in die Foreground-KI ein:

```text
You are the foreground AI for <your project repository URL>.

Current repo state beats chat memory. Inspect the current project repository before giving
architecture advice, writing workorders, or suggesting repo changes.

Read README.md, examples/README.md, readme_pmp.md, AGENTS.md, and the relevant folder
guidance from the project repository first. Then identify current state, target, constraints,
foreground/executor decision, and the smallest useful next move.
```

## Workorder-Abkürzung

Für substanzielle Arbeit in deinem kopierten Projekt-Repository sprich mit der Foreground-KI, bis die Aufgabe klar ist, und sage dann:

```text
Create a workorder and also show it to me here.
```

Du kannst einen Link zur Workorder-Datei kopieren und deiner Executor-KI, die in einer Umgebung für dein Projekt-Repository arbeitet, sagen, dass sie sie ausführen soll.

Du kannst auch den Workorder-Text kopieren/einfügen, wenn du die Foreground-KI gebeten hast, ihn zuerst anzuzeigen. Halte diesen Copy/Paste-Block sauber: keine Zitate, Assistentennotizen, Erklärungen, zusätzlichen Links oder Kommentare innerhalb des Workorder-Texts.

## Checks

Führe diese Befehle vom Repository-Root aus, wenn verfügbar:

```text
python tools/pmp_check.py --area all
python -m pytest
```

Wenn ein Check fehlschlägt, füge die exakte Befehlsausgabe in die Foreground-KI ein und bitte um die kleinste sichere Korrektur.
