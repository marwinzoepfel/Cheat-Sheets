# Die Go Infrastruktur

Go ist bekannt für eine sehr geniale Infrastruktur, dass ist auch der Grund warum ich dir alles mit Go beibringe. Go ist nicht super einfach aber du lernt sehr viel und sehr gelenkt mit Go. Viele schlechte Gewohnheiten unterstützt Go nicht und so fängt man vorallem als neuer Entwickler garnicht an sich diese anzugewöhnen.

## Die alte Go Struktur

Bis zur 12. Go Version gab es einen GOPATH, den gibt es zwar immer noch aber er wird anders benutzt. Der GOPATH lag meistens direct auf dem Nutzer und hieß einfach `/go`

> Benutzername/go

Wenn ich als Entwickler also ein neues Projekt starten wollte musste ich hierfür erstmal einen neuen Ordner anlegen und hier drin meinen Code schreiben. Go Programme liefen also nur in diesem Order sonst nirgends, außer man baut sich eine Binary die läuft immer egal ob mit oder ohne Go.

<img src="../resources/Screenshot 2022-03-15 at 9.16.52 AM.png">

So  würde dann in dem GOPATH die Struktur aussehen, dass ist nicht zwingend, da hat jeder Entwickler seine eigenen Vorzüge. Ich habe mich für den oben gezeigten Aufbau entschieden, hier gibt es 3 Order : bin / pkg / src. Bin und pkg schauen wir uns später an, du kannst dir jetzt erstmal merken hier kommt der Code von anderen Entwicklern rein auf den wir dann zugreifen können. bin = binary, pkg = package

In den src Ordner kurz für Sourcecode kommt dein eigener Code rein, alle Go Programme die du schreibst sind hier auf einem Haufen zusammen.

## Die neue Go Struktur

Da ich mit dem GOPATH aufgewachsen bin halte ich mich mehr oder weniger strickt dran, ich empfehle es dir trotzdem erstelle einen GO Ordner, oder wahrscheinlich hat Go beim installieren diesen schon erstellt dann suche den einfach mal. Go unterstützt jetzt aber eine deutlich angenehmere Lösung die troztdem noch sehr gut organisiert ist, diese heißt Go Mod.

### Go Mod

Mit Go Mod zeigst du jetzt Go in welchen Ordnern dein Projekt ist, einfach einen neuen Ordner erstellen und in das Terminal `go mod init`  eingeben und schon hast du dein eigenes Projekt. Mit dem Command erstellst du jetzt 2 neue Datein

- go.mod
- go.sum

Die go.mod Datei ermöglicht es anderen Entwicklern automatische alles auf ihren Computer zu laden, was dein Programm braucht. Zudem stehen hier Informationen drin, wie welche Verison du von Go benutzt. Die go.sum ist für dich nicht weiter wichtig, hier stehen einfach Informationen für Go drin was es runterladen muss und so weiter.

### Go Get

Wie schon öfter angesprochen wirst du viel mit dem Code von anderen Entwicklern arbeiten, als Beispiel wenn du eine Webseite schreiben willst und nicht wirklich alles selber schreiben willst kannst du dir Erweiterungen von anderen Entwicklern runter laden. Dass ist nicht nur ok sondern auch gut so, es gibt Entwickler die sich in manchen Dingen deutlich besser auskennen als du und vorallem wenn es um Daten von Nutzern geht sind ihre Lösungen meist sicherer, als bei ganz frischen Entwicklern wie bei dir.

Hierfür benutzten viele Entwickler tools wie git, GitHub, GitLab usw.  Go Get ist aber quasi eine eingebaute Version von diesen Tools, einfach den command `go get [projekt von anderen Entwicklern]` eingeben, alles was hier eingeklammert ist steht meist auf den Webseiten von den Entwicklern der jeweiligen Bibliothek.

