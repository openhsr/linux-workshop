---
marp: true
---
## Wilkommen beim Linux Basic-Kurs

![Linux](./images/225px-Tux.svg.png)

---

## Ablauf

* Einführung Linux
* Benutzer Oberfläche
* Hilfe
* Daten Managen
* Software Installieren
* Prozesse
* Benutzerrechte
* Umgebungsvariablen
* Vi

---

## Einführung Linux

*Bitte ergänzen allgemeine Eigenschaften*

---

## Benutzer Oberfläche

![Benutzer Oberfläche](./images/ubuntu_16_LTS.png)

---

## Hilfe

---

### Integrierte Hilfe

Als erste Anlaufstelle bietet sich hier meistens die integrierte Hilfe der einzelnen Befehle an.

```bash
--help / -? / -h
```

---

### Aufgabe 1

Öffnen Sie die Commandline und geben Sie folgendes ein:

```bash
uname --help
```

---

**Erwartete Ausgabe:**

```bash

Usage: uname [OPTION]...
Print certain system information.  With no OPTION, same as -s.

  -a, --all                print all information, in the following order,
                           except omit -p and -i if unknown:
  -s, --kernel-name        print the kernel name
  -n, --nodename           print the network node hostname
  -r, --kernel-release     print the kernel release
  -v, --kernel-version     print the kernel version
  -m, --machine            print the machine hardware name
  -p, --processor          print the processor type or "unknown"
  -i, --hardware-platform  print the hardware platform or "unknown"
  -o, --operating-system   print the operating system
      --help     display this help and exit
      --version  output version information and exit
```

---

### Manpages

Neben der integrierten Hilfe, liefern die meisten Programme sogenannte Manpages mit. Die Manpages bieten meistens eine genaue, ausführliche Hilfe zu einem Befehl.

```bash
Options:    $ man [OPTION] [COMMAND NAME]
No Options: $ man [COMMAND NAME]
```

---

### Aufgabe 2

Öffnen Sie die Commandline und geben Sie folgendes ein:

```bash
man printf
```

---

**Erwartete Ausgabe:**
*ERGÄNZEN*

---

## Daten Managen

Dateinamen in Linux haben einige Eigenheiten:
Case-Sensitive
Maximale Länge 255 Zeichen
Eine Datei welche mit einem "." beginnt, gilt als versteckte Datei.

---

### Dateien suchen und finden

* keine Laufwerksbuchstaben vs Wurzelverzeichnis
* Wurzelverzeichnis hat kinen Namen
* häufig mit / bezeichnet
* Datenträger beim Booten oder zur Laufzeit eingehängt

---

#### cd

Wechseln des Verzeichnisses

```bash
cd Destination
cd ..             Wechselt ins übergeordnete Verzeichnis
cd ~              Wechselt in das Home-Verzeichnis zurück
```

---

#### ls

ls listet den Inhalt eines Verzeichnisses auf

```bash
ls [OPTION] [FILE1, FILE2, ...]
```

---

#### grep

Der Befehl grep durchsucht eine oder mehrere Dateien nach einem Suchbegriff(Text oder Regex) und gibt alle Zeilen oder Dateinamen aus, in denen der Suchbegriff gefunden wurde.

```bash
grep 'xxx' foo | Durchsucht die Datei foo nach dem Text xxx und gibt alle Zeilen auf der Konsole aus, wo xxx gefunden wurde.
grep "*.c" * | Listet alle Dateien mit der Dateiendung .c im aktuellen Verzeichnis auf.
```

---

#### find

Sucht nach Verzeichnis- und/oder Dateinamen aufgrund eines Suchbegriffs. Ohne Pfadangabe wird das aktuelle Verzeichnis und dessen Unterverzeichnisse durchsucht.

```bash
find [OPTION] GESUCHT
find -name h*
```

---

### Aufgabe 3

1. Was ist der unterschied zwischen ls und ls -a? Probieren Sie es in ihrem Verzeichniss aus.
2. Finde alle dateien mit der Endung 'c' or 'asm‘.
3. Suche *.txt Dateien aber ignoriere versteckte Dateien.
4. Finde alle .dot Dateien aber ignoriere .htaccess Dateien.

---

**Antwort**
1. 
ls  listet alle Dateien ohne die Verborgenen auf.
ls -a Alle inklusive den Verborgenen (mit "." beginnend)

```bash
2. $> find . -type f \( -iname "*.c" -or -iname "*.asm" \)
3. $> find . -type f \( -iname "*.txt" ! -iname ".*" \)
4. $> find . -type f \( -iname ".*" ! -iname ".htaccess" \)
```

---

### aktuellen Pfad ausgeben

Der Befehl pwd gibt den Pfad des aktuellen Verzeichnisses aus.

```bash
pwd [OPTION]
```

---

### Datei erzeugen

Mit dem Befehl touch kann man eine Datei erzeugen.

```bash
cat > Test.txt
This is my txt.
I have fun.

^z
touch Test2.txt
```

---

### Dateien kopieren

Der Befehl cp kopiert eine Datei oder ein Verzeichnis.

```bash
cp [OPTION] Source [SRC2, SRC3, ...] Destination

cp Test.txt TestCopy.txt
```

---

### Dateien verschieben

Der Befehl mv verschiebt eine Datei oder ein Verzeichnis oder benennt sie um.

```bash
mv [OPTION] AlterDateiname   NeuerDateiname   (umbenennen)
mv [OPTION] Quelldateiliste  Zielverzeichnis  (verschieben)

mv TestCopy.txt Copy.txt
```

---

### Dateien löschen

Der Befehl rm löscht eine Datei oder ein Verzeichnis

```bash
rm [OPTION] Destination

rm Test2.txt
```

---

### Verzeichnis erstellen

Der Befehl mkdir (make directory) erstellt ein Verzeichnis.

```bash
mkdir [OPTION] DIRECTORY [DIRECTORY2, DIRECTORY3, ...]

mkdir mydir
```

---

### Verzeichnis löschen

Der Befehl rmdir (remove directory) entfernt ein leeres Verzeichnis.

```bash
rmdir [OPTION] DIRECTORY [DIRECTORY2, DIRECTORY3, ...]

rmdir mydir
```

---

### Aufgabe 4

1. Erstellen Sie ein neues Verzeichnis. (mkdir)
2. Wechseln Sie in dieses Verzeichnis.  (cd)
3. Erstellen Sie darin eine Datei.      (cat)
4. Kopieren Sie diese Datei.            (cp)
5. löschen Sie das Verzeichnis.         (rmdir / rm)

**Frage**: Benötigt man rm oder rmdir um das Verzeichnis zu löschen? (ausprobieren)

---

**Antwort**
rm, der Befehl rm löscht eine Datei oder ein Verzeichnis. Der Befehl rmdir entfernt ein leeres Verzeichnis.

---

### Augabe von Textdateien

Befehl | Beschreibung
------------ | -------------
cat file | Gibt den ganzen Inhalt von file in der Konsole aus
head file | Gibt die ersten zehn Zeilen in der Konsole aus. (-n Anzahl Zeilen)
tail file | Gibt die letzten zehn Zeilen in der Konsole aus. (-n Anzahl Zeilen)
less file | Zeigt den Inhalt von file wie eine Manual Page. Der Text kann gescrollt werden. Mit der Taste q wird der Befehl beendet.

---

### Umleiten der Ein- und Ausgabe

Linux bietet verschiedene Möglichkeiten. Die am häufigsten verwendeten Befehle:

Befehl | Beschreibung
------------ | -------------
befehl > file | Standardausgabe von befehl nach file umleiten
befehl < file | Standardeingabe von befehl nach file umleiten
befehl >> file | Standardausgabe von befehl nach file umleiten. Falls file bereits exisitiert, wird die Ausgabe bei file hinzugefügt.
befehl1 | befehl2 | Pipelining: Leitet die Standardausgabe von befehl1 auf die Standardeingabe von befehl2 um.

---

Diese Anweisung speichert beispielsweise den Inhalt der Datei Test in der Datei Test1.

```bash
cat Test > Test1
```

---

## Software Installieren

---

### Pakete

* Anwendungen für Linux
* ähneln einfachen Archiven
* alle für die Ausführung der Anwendung notwendigen Komponenten

---

## Installation pacman Arch Linux

* Programm pacman (kurz für package manager) verwenden
* root Rechte

Beispiel das Programm sl installieren:

```bash
sudo pacman -S sl
sudo pacman -S links wget lsof
```

---

### Paketsuche

* [https://www.archlinux.org/packages/](https://www.archlinux.org/packages/)
* oder pacman verwenden

Alle verfügbaren Pakete anzeigen

```bash
pacman -Ss
filtern: pacman -Ss youtube
```

---

### Andere Möglichkeiten

---

#### dpkg

* arbeitet direkt auf DPKG-Dateien
* Nachteile: nur einzelne Pakete werden installiert, Paketabhängigkeiten werden nicht aufgelöst
* Pakete müssen lokal auf dem Rechner vorliegen

#### apt-get

* kann Pakete, abhängige Pakete und Bibliotheken automatisch installieren
* Pakete werden aus verschiedenen Quellen im Internet heruntergeladen

#### aptitude

* nicht mehr benötigte, also verwaiste Pakete automatisch deinstallieren
* abhängige Pakete automatisch nachinstallieren

---

### Aufgabe 5

*noch ergänzen etwas Sinnvolles Instalieren?*

---

## Prozesse

* mehrere Programme «gleichzeitig» auszuführen
* Prozesse sind isoliert.

---

### ps

listet aktuell aktive Prozesse auf

### kill

Mit dem Befehl kill können verschiedene Signale an einen Prozess geschickt werden. Wenn kein Signal
angegeben wird, wird das Signal TERM verschickt und der Prozess i.d.R. normal beendet.

---

## Benutzerrechte

Unix wurde für den Einsatz auf Grossrechnern entwickelt und war deshalb bereits zu Beginn als Multi-User-Betriebssystem konzipiert.

---

### Root-Rechte

* Superuser (root) und «normale» Benutzerrechte
* Systemadministration nur mit root-Rechten ausgeführt, resp.
* Befehl sudo

Beispiele:

```bash
sudo pacman -S foo
sudo nano /etc/foo
```

Shell mit root-Rechten öffnen:

```bash
sudo -s
```

---

### Dateirechte

drei Rechte: Lesen (read, r), Schreiben (write, w) und Ausführen (execute, x).
zuweisen an: Besitzer der Datei (u), der Gruppe der Datei (g) sowie für andere Benutzer (o)

---

**chmod**
Der Befehl chmod setzt die Dateirechte, wobei es zwei Notationen (Symbolisch oder Oktal-Modus) gibt.
Beide Beispiele weisen dem Besitzer einer Datei namens foo das Executable-Recht zu:

```bash
chmod u+x foo
chmod 764 foo
```

---

Dateien mit Recht informationen
**ls -al**

---

## Umgebungsvariabeln

*Ergänzen oder Entfernen*

---

## Vi

Vi war der erste „full-screen“ Texteditor für UNIX. Er ist klein und „einfach“, aber hat eine gewöhnungsbedürftige Bedienung.

---

### Warum Vi lernen

* auf jedem – noch so minimalistischen – Unix-System ist ein vi installiert 
* läuft im Terminal und ist hilfreich bei Remote-Zugriff

---

### Starten

```bash
vi file
vi +N filename 		Go to the Nth line of the file after opening it.
```

---

### Verlassen

* **:w** Änderungen speichern
* **:w fname** Änderungen speichern in File fname
* **:w!**	Speichern erzwingen
* **:q** Beenden (klappt nur, wenn Text seit letztem Speichern nicht 	verändert wurde)
* **:q!** Verlassen ohne zu speichern auch bei modifiziertem Dokument
* **:wq** Speichern und beenden (oder: ZZ ohne „:“) (:x)
* **:sav fname** Aktuelle Datei unter einem neuen Namen speichern (neue Datei wird 	bearbeitet, alte Datei wir geschlossen, aber nicht gespeichert)
* **:e fname** aktuelle Datei wird geschlossen (muss gespeichert sein) und neue 	Datei geöffnet
* **...!** Force der Aktion (:w! oder q!)

---

### im File Navigieren

* **hjkl** Bewegung des Cursors nach links, unten, oben, rechts
* **w** Move to the beginning of the next word on the current line 
* **b** Move to the beginning of the previous word on the current line 
* **e** Move to the end of next word on the current line 
* **ge** Move to the end of previous word on the current line 
* **$** Mit dem Cursor zum Zeilenende springen 
* **0** Mit dem Cursor zum Zeilenanfang springen (Null) (oder ^)
* **Ctrl-f** Scroll forward one page 
* **Ctrl-b** Scroll backward one page 
* **xG** Springen zu Zeilennummer (3G moves to line 3) (auch :3 oder 3gg )
* **G** Ans Ende der Datei springen
* **gg** An Start der Datei springen

---

### Text bearbeiten

* **i** Wechsel in den Insert-Mode an der aktuellen Cursorposition 	(Einfügen links vom Cursor)
* **I** Einfügen am Zeilenanfang
* **a** Wechsel in den Insert-Mode, einfügen rechts vom Cursor (append)
* **A** Einfügen am Zeilenende

---

* **s** Wechsel in den Insert-Mode, aktuelles Zeichen wird überschrieben
* **SText** Ersetze ganze Zeile durch "Text" der eingegeben wird

---

* **rc** Ersetzen des aktuellen Zeichen unter Cursor durch das Zeichen "c" 
* **R** Überschreiben ab Cursorposition (REPLACE Mode)

---

* **x** löscht Zeichen unter Cursor  nach rechts (auch xx, z.B. 5x)
* **X** löscht Zeichen links von Cursor (auch xX, z.B. 5X)
* **dw** löscht ab Cursor-Position bis Anfang des nächstens Wortes (ohne Insert Mode)
* **D** löscht Text hinter Cursor bis Zeilenende

---

### Aufgabe 6

*Vim Aufgabe?*
