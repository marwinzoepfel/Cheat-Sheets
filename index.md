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

# Git Version Control

Deine Programme werden immer komplexer und die Kommentare in deinem Code werden unverständlich? Da kommt dir Git zur Hilfe.

Aber was ist Git eigentlich? Stark runtergebrochen trackt Git alles was du in deinem Code machst und du kannst dir in Etappen anschauen was du wo geschrieben hast. Mal angenommen ich habe ein einfaches Hello World Programm in Go geschrieben.

Hier eine Beispiel main Function, als Version 1.

```go
func main(){
  fmt.Println("Hello, World")  
}
```

Jetzt gehe ich hin und übersetze es ins Deutsche.

```go
func main(){
  fmt.Println("Hallo, Welt")
}
```

Dann zeigt mir jetzt git ok du hast diese Datei geändert und zwar in der Main Funktion diese Zeile. Jetzt kann ich hin gehen und git sagen, ok habe ich geändert bitte speicher diese Änderung als **Übersetzen von Main Funktion**. Falls ich jetzt ein bisschen weiter an meinem Programm schreibe und einen Fehler mache, ich aber weiß : "Meine letzte Version ging aber noch". Dann kann man hingehen und sich wendern die alte Version anzeigen lassen oder deinen Code zurücksetzen auf die alte Version.

Man kann sich Git also wie eine Art Zeitstrahl vorstellen, auf dem ihr jederzeit hin und her springen könnt.

```
----> Version 1.0 ------> Version1.1 ------> Version2.0
```



## Befehle

Irgendwie muss man jetzt aber git bedienen können, auch wenn es viele IDEs unterstützen bin ich ein großer Fan davon alles weiterhin im Terminal zu machen, oder zumindest die Befehle den Code schaue ich mir meist in meiner IDE an. Jetzt muss git aber erstmal wissen was mein Projekt ist, dafür einfach in meinen Ordner gehen wo alle meine Datein liegen und den Command `git init` eingeben und schon habe ich eine neue Git Repository. Wenn ich jetzt schauen will was ist denn hier alles drin und was habe ich vielleicht schon verändert, benutze den Command `git status`

<img src="../resources/Screenshot 2022-03-15 at 12.30.50 PM.png">

Ich habe in diesem Beispiel schon 2 Datein verändert (Hier in Rot dargestellt), wenn ich jetzt nachschauen will was ich genau verändert habe kann ich `git diff`  eingeben und schon zeigt mit Git genau welche Zeilen ich verändert habe. Diese Funktion nutze ich meist in meiner IDE, wie das funkioniert ist aber jedes mal anders.

Wenn ich jetzt Git sagen will dass ich zufrieden bin mit den Änderungen und diese gerne Speichern möchte, dann muss ich Git erstmal sagen welche Datein in diese Version gehören, dafür benutzt man einfach `git add [Alle Datein die ich hinzufügen möchte]`. Wenn ich jetzt aber einfach alle Datein hinzufügen möchte die ich in diesem Ordner verändert habe benutzte eifnach `git add .` und schon hat Git alle Datein registriert. 

Jetzt muss ich nur noch Git sagen ich bin zufrieden mit diesen Datein und wie ich die neue Version nennen will, hierfür einfach `git commit -m "Der Name der Version oder eine kurze Beschreibung`. Und schon hast du eine neue Version gespeichert, auch wenn sie Version jetzt so groß anhört macht man dieses Verfahren eigentlich super oft, selbst bei kleinen Änderungen.

 <a href="https://github.com/joshnh/Git-Commands">Alle Git Befehle</a>

## Branches

Wenn du dir nochmal den Zeitstrahl von oben vorstellst, dann kannst du jetzt bei jeder Version von dem "Hauptpfeil" abkommen und einen neuen Branch erstellen, hier kannst du jetzt deinen Code ändern so viel du willst. Der Hauptpfeil (Main/Master Branch) bleibt aber unverändert. Wenn du dann zufrieden bist mit deinen Änderungen kannst du die beiden Branches zusammen mergen, also den Code von deinem neuen Branch in den Main übertragen. Wenn du aber nur mit dem Code was ausprobieren wolltest, kannst du neu erstellen Branch einfach löschen und dein Programm bleibt unversehrt.

<img src="../resources/two-branches.png">
> Quelle : https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell

## Opensource

Diese Art von Kontrolle über Code ermöglicht es Entwicklern nicht nur alleine deutlich produktiver zu sein, sondern förder die Produktvität in Teams aber auch in Opensource Projekten. Git ermöglicht es dir nähmlich deinen Code online hochzuladen und den Code von anderen runterzuladen.

### Github

Eine Software die ich sehr viel benutzte heißt Github, Github ist quasi wie ein Sozialesnetzwerk für Entwickler. Ihr könnt eure Projekte hochladen und mit anderen Leuten teilen oder einfach öffentlich stellen, so dass jeder den Code anschauen kann. Github hat so viele Funktionen, dass ich diese hier nicht alle aufzählen werde. Geh einfach mal auf die Seite GitHub.com und schau dich um. 

Ihr könnt jetzt aber Git und Github verknüpfen, wenn ihr auf Github eine neue Repository erstellt kommt von Github eine Anleitung wie ihr eure Git Repository auf eurem localem Computer mit Github verknüpfen könnt. 

```bash
echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:username/test.git
git push -u origin main
```

 Wenn hier ein Fehler kommt müsst ihr erst einen SSH Key einrichten und den bei Github hinterlegen.
