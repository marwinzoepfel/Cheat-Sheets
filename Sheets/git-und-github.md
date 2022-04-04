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

Eine Software die ich sehr viel benutzte heißt Github, Github ist quasi wie ein Sozialesnetzwerk für Entwickler. Du kannst deine Projekte hochladen und mit anderen Leuten teilen oder einfach öffentlich stellen, so dass jeder den Code anschauen kann. Github hat so viele Funktionen, dass ich diese hier nicht alle aufzählen werde. Geh einfach mal auf die Seite GitHub.com und schau dich um. 

Du kannst jetzt aber Git und Github verknüpfen, wenn du auf Github eine neue Repository erstellst kommt von Github eine Anleitung wie du deine Git Repository auf deinem localem Computer mit Github verknüpfen könnt. 

```bash
echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:username/test.git
git push -u origin main
```

 Wenn hier ein Fehler kommt musst du erst einen SSH Key einrichten und den bei Github hinterlegen.
