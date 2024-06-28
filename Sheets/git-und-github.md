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

Irgendwie muss man jetzt aber Git bedienen können. Auch wenn es viele IDEs unterstützen, bin ich ein großer Fan davon, alles weiterhin im Terminal zu machen, oder zumindest die Befehle. Den Code schaue ich mir meist in meiner IDE an. Jetzt muss Git aber erstmal wissen, was mein Projekt ist. Dafür einfach in den Ordner gehen, wo alle meine Dateien liegen, und den Befehl `git init` eingeben, und schon habe ich ein neues Git-Repository. Wenn ich jetzt schauen will, was denn hier alles drin ist und was ich vielleicht schon verändert habe, benutze ich den Befehl `git status`.

<img src="../resources/Screenshot 2022-03-15 at 12.30.50 PM.png">

Ich habe in diesem Beispiel schon 2 Dateien verändert (hier in Rot dargestellt). Wenn ich jetzt nachschauen will, was ich genau verändert habe, kann ich `git diff` eingeben, und schon zeigt mir Git genau, welche Zeilen ich verändert habe. Diese Funktion nutze ich meist in meiner IDE, wie das funktioniert, ist aber jedes Mal anders.

Wenn ich jetzt Git sagen will, dass ich zufrieden bin mit den Änderungen und diese gerne speichern möchte, dann muss ich Git erstmal sagen, welche Dateien in diese Version gehören. Dafür benutzt man einfach  `git add [Alle Datein die ich hinzufügen möchte]`. Wenn ich jetzt aber einfach alle Dateien hinzufügen möchte, die ich in diesem Ordner verändert habe, benutze ich einfach `git add .`, und schon hat Git alle Dateien registriert.

Jetzt muss ich nur noch Git sagen, ich bin zufrieden mit diesen Dateien und wie ich die neue Version nennen will. Hierfür einfach `git commit -m "Der Name der Version oder eine kurze Beschreibung`. Und schon habe ich eine neue Version gespeichert, auch wenn es "Version" jetzt so groß anhört, macht man dieses Verfahren eigentlich super oft, selbst bei kleinen Änderungen.



 <a href="https://github.com/joshnh/Git-Commands">Alle Git Befehle</a>

## Branches

Wenn du dir nochmal den Zeitstrahl von oben vorstellst, dann kannst du jetzt bei jeder Version vom "Hauptpfeil" abkommen und einen neuen Branch erstellen. Hier kannst du jetzt deinen Code ändern, so viel du willst. Der Hauptpfeil (Main/Master-Branch) bleibt aber unverändert. Wenn du dann zufrieden bist mit deinen Änderungen, kannst du die beiden Branches zusammenführen (mergen), also den Code von deinem neuen Branch in den Main übertragen. Wenn du aber nur mit dem Code etwas ausprobieren wolltest, kannst du den neu erstellten Branch einfach löschen, und dein Programm bleibt unversehrt.

<img src="../resources/two-branches.png">
> Quelle : https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell

## Opensource

Diese Art von Kontrolle über Code ermöglicht es Entwicklern nicht nur alleine deutlich produktiver zu sein, sondern fördert die Produktivität in Teams, aber auch in Open-Source-Projekten. Git ermöglicht es dir nämlich, deinen Code online hochzuladen und den Code von anderen runterzuladen.

### Github

Eine Software, die ich sehr viel benutze, heißt GitHub. GitHub ist quasi wie ein soziales Netzwerk für Entwickler. Du kannst deine Projekte hochladen und mit anderen Leuten teilen oder einfach öffentlich stellen, sodass jeder den Code anschauen kann. GitHub hat so viele Funktionen, dass ich diese hier nicht alle aufzählen werde. Geh einfach mal auf die Seite GitHub.com und schau dich um.

Du kannst jetzt aber Git und GitHub verknüpfen. Wenn du auf GitHub ein neues Repository erstellst, kommt von GitHub eine Anleitung, wie du dein Git-Repository auf deinem lokalen Computer mit GitHub verknüpfen kannst.

```bash
echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:username/test.git
git push -u origin main
```

Wenn hier ein Fehler kommt, musst du erst einen SSH-Key einrichten und diesen bei GitHub hinterlegen.
