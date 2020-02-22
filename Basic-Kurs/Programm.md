# Programm

Der Linux Basic Kurs bietet einen einfachen Einstieg in den Umgang mit Linux. Willkommen sind
alle mit installiertem Linux oder mit einer vorbereiteten Linux VM. Zu beginn werden die tollen
Eigenschaften von Linux präsentiert und anschliessend interaktiv die wichtigsten Commandline-Befehle
erlernt. Anschliessend sollte der Umgang mit Linux kein Problem mehr sein.

## Ablauf
* Deep-Dive Linux Universe
* Gnome Desktop Environment
* Wichtige unterschiede zu Windows
* Hilfe holen
* Daten Managen
* Software Installiere
* Prozesse
* Benutzerrechte
* Einrichten Software für HSR

## Einführung Linux

*Bitte ergänzen allgemeine Eigenschaften*

## Benutzer Oberfläche
*Input von anderen (kenne mich zuwenig aus wie unterschiedlich oder nicht die Verschiedenen Varrianten
sind!)
Bsp: Die Toolbars am oberen und unteren Bildschirmrand heissen Panels und entsprechen der
Taskleiste unter Windows. Das Menü am linken Rand des oberen Panels ist das Applications-Menu (vergleichbar
mit dem Windows Startmenü). Über das Places-Menu (rechts daneben) können Sie direkt auf verschiedene
Ordner zugreifen. Über das System-Menu, neben dem Places-Menu, können Sie sich abmelden und das System 
herunterfahren. Das untere Panel bietet Ihnen die Möglichkeit, zwischen verschiedenen Desktops zu 
wechseln, ähnlich wie auf Windows 10. Über den Knopf am linken Ende des unteren Panels können Sie alle 
offenen Fenster verbergen und wieder anzeigen.     BILD EINFÜGEN*

## Hilfe

### Integrierte Hilfe
Ein umfangreiches System wie Linux braucht eine ausgereifte  Hilfe, wo die Funktionsweise von Kommandos
nachgeschlagen werden kann.

Als erste Anlaufstelle bietet sich hier meistens die integrierte Hilfe der einzelnen Befehle an. Die
integrierte Hilfe ist bei den meisten Programmen mit diesen Parameter-aufrufbar:
```
--help / -? / -h
```

### Aufgabe 1
Öffnen Sie die Commandline und geben Sie folgendes ein: 
```
uname --help
```
** Erwartete Ausgabe:**
```
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
### Manpages
Neben der integrierten Hilfe, liefern die meisten Programme sogenannte Manpages mit. Die Manpages bieten
meistens eine genaue, ausführliche Hilfe zu einem Befehl.
Zugriff auf die Manpages erhält man mit dem Kommando man:
```
Options:    $ man [OPTION] [COMMAND NAME]
No Options: $ man [COMMAND NAME]
```
### Aufgabe 2
Öffnen Sie die Commandline und geben Sie folgendes ein: 
```
man printf
```
** Erwartete Ausgabe:**
*BILD ERGÄNZEN*

## Daten Managen
Dateinamen in Linux haben einige Eigenheiten:
Case-Sensitive
Maximale Länge 255 Zeichen
Eine Datei welche mit einem "." beginnt, gilt als versteckte Datei.

### Dateien suchen und finden
Im Unterschied zu Windows kennt Linux keine Laufwerksbuchstaben. Alle Verzeichnisse sind dem
Wurzelverzeichnis untergeordnet. Genau genommen hat das Wurzelverzeichnis keinen Namen, wird
aber häufig mit / bezeichnet. Datenträger werden beim Booten oder zur Laufzeit an bestimmten
Punkten in der Verzeichnishierarchie eingehängt.

**cd**

Wechseln des Verzeichnisses
```
cd Destination
cd ..             Wechselt ins übergeordnete Verzeichnis
cd ~              Wechselt in das Home-Verzeichnis zurück
```

**ls**

ls listet den Inhalt eines Verzeichnisses auf
```
ls [OPTION] [FILE1, FILE2, ...]
```

**grep**

Der Befehl grep durchsucht eine oder mehrere Dateien nach einem Suchbegriff und gibt alle Zeilen oder
Dateinamen aus, in denen der Suchbegriff gefunden wurde. Als Suchbegriff kann ein Text oder ein
regulärer Ausdruck verwendet werden.
``` 
grep 'xxx' foo | Durchsucht die Datei foo nach dem Text xxx und gibt alle Zeilen auf der Konsole aus, wo xxx gefunden wurde.
grep "*.c" * | Listet alle Dateien mit der Dateiendung .c im aktuellen Verzeichnis auf.
```

**find**
Der Befehl find durchsucht das Dateisystem nach Verzeichnis- und/oder Dateinamen aufgrund eines
Suchbegriffs. Ohne Pfadangabe(n) wird das aktuelle Verzeichnis und dessen Unterverzeichnisse
durchsucht.

``` 
find [OPTION] GESUCHT
find -name h*
```

### Aufgabe 3
1. Was ist der unterschied zwischen ls und ls -a? Probieren Sie es in ihrem Verzeichniss aus.
2. Find any file whose name ends with either 'c' or 'asm‘.
3. Find *.txt file but ignore hidden .txt file such as .vimrc or .data.txt file.
4. Find all .dot files but ignore .htaccess file.
5. List all setuid enabled files.
6. Alle Bilder, die auf .jpg enden mit tar archivieren.

** Antwort**
1. 
ls    listet alle Dateien ohne die Verborgenen auf.
ls -a Alle inklusive den Verborgenen (mit "." beginnend)
```
2. $> find . -type f \( -iname "*.c" -or -iname "*.asm" \)
3. $> find . -type f \( -iname "*.txt" ! -iname ".*" \)
4. $> find . -type f \( -iname ".*" ! -iname ".htaccess" \)
5. $> find / -xdev \( -perm -4000 \) -type f -print0 | xargs -0 ls -l
6. $> find -iname '*.jpg' -exec tar -rf bilder.tar {} \;
```

### aktuellen Pfad ausgeben
Der Befehl pwd gibt den Pfad des aktuellen Verzeichnisses aus.
```
pwd [OPTION]
```

### Datei erzeugen
Mit dem Befehl touch kann man eine Datei erzeugen.
```
cat > Test.txt
This is my txt.
I have fun.

^z
touch Test2.txt
```

### Dateien kopieren
Der Befehl cp kopiert eine Datei oder ein Verzeichnis.
```
cp [OPTION] Source [SRC2, SRC3, ...] Destination

cp Test.txt TestCopy.txt
```

### Dateien verschieben
Der Befehl mv verschiebt eine Datei oder ein Verzeichnis oder benennt sie um.
```
mv [OPTION] AlterDateiname   NeuerDateiname         (umbenennen)
mv [OPTION] Quelldateiliste  Zielverzeichnis		(verschieben)

mv TestCopy.txt Copy.txt
```

### Dateien löschen
Der Befehl rm löscht eine Datei oder ein Verzeichnis
```
rm [OPTION] Destination

rm Test2.txt
```

### Verzeichnis erstellen
Der Befehl mkdir (make directory) erstellt ein Verzeichnis.
```
mkdir [OPTION] DIRECTORY [DIRECTORY2, DIRECTORY3, ...]

mkdir mydir
```

### Verzeichnis löschen
Der Befehl rmdir (remove directory) entfernt ein leeres Verzeichnis.
```
rmdir [OPTION] DIRECTORY [DIRECTORY2, DIRECTORY3, ...]

rmdir mydir
```

### Aufgabe 4
1. Erstellen Sie ein neues Verzeichnis. mkdir
2. Wechseln Sie in dieses Verzeichnis.  cd
3. Erstellen Sie darin eine Datei.      cat
4. Kopieren Sie diese Datei.            cp
5. löschen Sie das Verzeichnis.         rmdir / rm

**Frage**: Benötigt man rm oder rmdir um das Verzeichnis zu löschen? (Wenn niht klar ausprobieren)

**Antwort**
rm, der Befehl rm löscht eine Datei oder ein Verzeichnis. Der Befehl rmdir (remove directory) entfernt ein leeres Verzeichnis.

### Augabe von Textdateien
Befehl | Beschreibung
------------ | -------------
cat file | Gibt den ganzen Inhalt von file in der Konsole aus
head file | Gibt die ersten zehn Zeilen von file in der Konsole aus. Mit der Option -n kann die Anzahl Zeilen festgelegt werden
tail file | Gibt die letzten zehn Zeilen von file in der Konsole aus. Mit der Option -n kann die Anzahl Zeilen festgelegt werden
more file | Dieser Befehl ist obsolet. Verwenden Sie less file
less file | Zeigt den Inhalt von file wie eine Manual Page, d.h. der Text kann gescrollt werden. Mit der Taste q wird der Befehl beendet.

### Umleiten der Ein- und Ausgabe
Linux bietet verschiedene Möglichkeiten, die Ein- und/oder die Ausgabe von Befehlen umzuleiten. Die
am häufigsten verwendeten Befehle sind wie folgt
Befehl | Beschreibung
------------ | -------------
befehl > file | Standardausgabe von befehl nach file umleiten
befehl < file | Standardeingabe von befehl nach file umleiten
befehl >> file | Standardausgabe von befehl nach file umleiten. Falls file bereits exisitiert, wird die Ausgabe bei file hinzugefügt.
befehl1 | befehl2 | Pipelining: Leitet die Standardausgabe von befehl1 auf die Standardeingabe von befehl2 um.

```
cat Test > Test1
```
Die Anweisung speichert beispielsweise den Inhalt der Datei Test in der Datei Test1. Mit
dem Zeichen > wird die Standardausgabe des Befehls foo auf die Datei Test1 umgeleitet. (Ansehen)

## Software Installieren 

### Pakete
Anwendungen für Linux werden in Form sogenannter Pakete angeboten. Sie ähneln einfachen Archiven, in denen alle für die Ausführung der Anwendung not-wendigen Komponenten enthalten sind. Zusätzlich

## Installation pacman Arch Linux
Um auf Arch Linux zusätzliche Pakete zu installieren, können sie das Programm pacman (kurz für package manager) verwenden. Beachten Sie, dass Sie root Rechte benötigen um mittels pacman Pakete zu installieren. Um zum Beispiel das Programm sl zu installieren, verwenden Sie das folgende Kommando: 
```
sudo pacman -S sl 
sudo pacman -S links wget lsof
```
### Paketsuche
Um nach Paketen zu suchen, können Sie entweder die Arch Linux Package Search Seite (https://www.archlinux.org/packages/), oder pacman verwenden. Um alle verfügbaren Pakete anzuzeigen, verwenden Sie folgendes Kommando:
```
pacman -Ss
filtern: pacman -Ss youtube
```
### Systemaktualisierungen
Arch Linux ist eine sogenannte Rolling Release Distribution. Das bedeutet, dass es im Gegensatz zu anderen Linux Distributionen, wie zum Beispiel Debian oder Ubuntu, keine festen Release Versionen gibt. Es empfiehlt sich daher regelmässig update durchzuführen. Sie können dies mit dem folgenden Kommando tun:
```
pacman -Syu
```
Wir empfehlen Ihnen, jeweils zuerst eine Systemaktualisierung durchzuführen bevor Sie ein neues Paket installieren

### Andere Möglichkeiten

#### dpkg
- arbeitet direkt auf DPKG-Dateien (.deb)
- Nachteile: nur einzelne Pakete werden installiert, Paketabhängigkeiten werden nicht aufgelöst (müssen manuell installiert werden)
- Pakete müssen lokal auf dem Rechner vorliegen

#### apt-get
- kann Pakete, abhängige Pakete und Bibliotheken automatisch installieren (kann keine Pakete herunterladen)
- Pakete werden aus verschiedenen Quellen im Internet heruntergeladen

#### aptitude
- nicht mehr benötigte, also verwaiste Pakete automatisch deinstallieren
- abhängige Pakete automatisch nachinstallieren

### Aufgabe 5
*noch ergänzen*

## Prozesse
Prozesse sind ein zentrales Konzept bei allen Betriebssystemen, die Multitasking unterstützen, d.h. in der
Lage sind, mehrere Programme «gleichzeitig» auszuführen. Prozesse sind aus Gründen der Sicherheit und der Robustheit
voneinander isoliert. Das Betriebssystem stellt sicher, dass Prozess A nicht auf Speicher von Prozess B zugreifen
oder Programmcode von Prozess B ausführen kann.

**ps**
listet aktuell aktive Prozesse auf

**kill**
Mit dem Befehl kill können verschiedene Signale an einen Prozess geschickt werden. Wenn kein Signal
angegeben wird, wird das Signal TERM verschickt und der Prozess i.d.R. normal beendet.

## Benutzerrechte
Unix wurde für den Einsatz auf Grossrechnern entwickelt und war deshalb bereits zu Beginn als Multi-User-Betriebssystem konzipiert.

### Root-Rechte
Aus Gründen der Sicherheit und der Robustheit wird generell zwischen Superuser (root) und «normalen» Benutzerrechten unterschieden.
Beispielsweise dürfen Programme und Konfigurationsdateien zur Systemadministration nur mit root-Rechten ausgeführt, resp. 
geändert werden. Um ein Programm mit root-Rechten auszuführen, stellt man den Befehl sudo vor das auszuführende Programm. 
Linux prüft, ob der Benutzer in der sudoer-Liste eingetragen ist, erfragt das Passwort des Benutzers und führt
anschliessend das Programm mit root-Rechten aus.

Beispiele:
```
sudo pacman -S foo
sudo nano /etc/foo
```

Shell mit root-Rechten öffnen:
```
sudo -s
```
### Dateirechte
Auf Dateiebene unterscheidet Linux drei Rechte: Lesen (read, r), Schreiben (write, w) und Ausführen
(execute, x). Diese drei Rechte können dem Besitzer der Datei (u), der Gruppe der Datei (g) sowie für
andere Benutzer (o) gesetzt werden.

**chmod**
Der Befehl chmod setzt die Dateirechte, wobei es zwei Notationen (Symbolisch oder Oktal-Modus) gibt.
Beide Beispiele weisen dem Besitzer einer Datei namens foo das Executable-Recht zu:
```
chmod u+x foo
chmod 764 foo
```

**ls -al**
mit Recht informationen

## Umgebungsvariabeln
 *Ergänzen oder Entferne*

## Vi
Vi war der erste „full-screen“ Texteditor für UNIX. Er ist klein und „einfach“, aber hat eine gewöhnungsbedürftige Bedienung.
Er ist immer noch sehr beliebt und auf praktisch jedem System verfügbar.

**Warum Vi lernen**
*auf jedem – noch so minimalistischen – Unix-System ist ein vi installiert 
*läuft im Terminal  hilfreich bei Remote-Zugriff

### Starten
```
vi file
vi +N filename 		Go to the Nth line of the file after opening it.

```
### Verlassen
* :w		Änderungen speichern
* :w fname 	Änderungen speichern in File fname
* :w!		Speichern erzwingen
* :q		Beenden (klappt nur, wenn Text seit letztem Speichern nicht 	verändert wurde)
* :q! 		Verlassen ohne zu speichern auch bei modifiziertem Dokument
* :wq		Speichern und beenden (oder: ZZ ohne „:“) (:x)
* :sav fname Aktuelle Datei unter einem neuen Namen speichern (neue Datei wird 	bearbeitet, alte Datei wir geschlossen, aber nicht gespeichert)
* :e fname	aktuelle Datei wird geschlossen (muss gespeichert sein) und neue 	Datei geöffnet
* ...!	    Force der Aktion (:w! oder q!)

### im File Navigieren
* hjkl  	Bewegung des Cursors nach links, unten, oben, rechts
* w 		Move to the beginning of the next word on the current line 
* b 		Move to the beginning of the previous word on the current line 
* e 		Move to the end of next word on the current line 
* ge		Move to the end of previous word on the current line 
* $ 		Mit dem Cursor zum Zeilenende springen 
* 0 		Mit dem Cursor zum Zeilenanfang springen (Null) (oder ^)
* Ctrl-f 	Scroll forward one page 
* Ctrl-b 	Scroll backward one page 
* xG 		Springen zu Zeilennummer (3G moves to line 3) (auch :3 oder 3gg )
* G 		Ans Ende der Datei springen
* gg		An Start der Datei springen

### Text bearbeiten
* i 	Wechsel in den Insert-Mode an der aktuellen Cursorposition 	(Einfügen links vom Cursor)
* I 	Einfügen am Zeilenanfang 
* a 	Wechsel in den Insert-Mode, einfügen rechts vom Cursor (append)
* A		Einfügen am Zeilenende 

* s		Wechsel in den Insert-Mode, aktuelles Zeichen wird überschrieben
* SText Ersetze ganze Zeile durch "Text" der eingegeben wird

* rc	Ersetzen des aktuellen Zeichen unter Cursor durch das Zeichen "c" 
* R 	Überschreiben ab Cursorposition (REPLACE Mode)

* x 	löscht Zeichen unter Cursor  nach rechts (auch xx, z.B. 5x)
* X 	löscht Zeichen links von Cursor (auch xX, z.B. 5X)
* dw 	löscht ab Cursor-Position bis Anfang des nächstens Wortes (ohne Insert Mode)
* D		löscht Text hinter Cursor bis Zeilenende

### Aufgabe 6







