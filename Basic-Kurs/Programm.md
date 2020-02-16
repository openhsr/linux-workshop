# Programm

Der Linux Basic Kurs bietet einen einfachen Einstieg in den Umgang mit Linux. Willkommen sind
alle mit installiertem Linux oder mit einer vorbereiteten Linux VM. Zu beginn werden die tollen
Eigenschaften von Linux präsentiert und anschliessend interaktiv die wichtigsten Commandline-Befehle
erlernt. Anschliessend sollte der Umgang mit Linux kein Problem mehr sein.

## Ablauf
* Einführung Linux
* Benutzer Oberfläche
* Hilfe
* Software Installieren
* Dateien Suchen/Bearbeiten/Erstellen
* Ein und Ausgabe
* Prozesse
* Benutzerrechte
* Umgebungsvariablen

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

## Dateien Suchen Beatbeiten Erstellen
Dateien suchen und finden (Filesystem Hierarchy Standard /etc, /root, /tmp, /opt, /var/log) aus Präsentation -	Linux Basic CLI Navigation (ls, dir, pwd, cd)

```
Datei Zusammenführung cat , join , paste		Style do
Datei Ansicht cat , od , less , head , tail , tac
Datei Zusammenfassung wc , uniq	Textprssecing
```

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

### Aufgabe
*noch ergänzen*





