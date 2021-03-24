M300 Services
==

Inhaltsverzeichnis
--
* Git Client / Git Account
* Atom (Visual Studio Code)
* Virtual Box
* Vagrant

Git Client / Git Account
--
Zuerst muss man einen GitHub-Account einrichten. Dieser dient als "Cloud-Speicher" für diese Dokumentationen.

##### Account erstellen

1. Auf www.github.com habe ich ein Benutzerkonto erstellt mit meiner Schulmail.
2. Nach dem Erstellen des Benutzerkontos, musste ich noch mein Mail verifizieren und mich anschliessend auf GitHub anmelden.

##### Repository erstellen

1. Zuerst musste ich mich unter www.github.com mit meinem erstellten Benutzerkonto anmelden.
2. Auf der Startseite musste ich dann ein neues Projekt erstellen.
3. Dann habe ich unter **Repository name** den Namen M300-Services definiert.
4. Dann musste ichh beim Radio Button **Public** lassen.
5. Nachher den Haken bei **Initialize this respository with a README** setzen.
6. Zum Schluss dann auf **Create respository** geklickt.



### SSH-Key erstellen

1. Terminal Bash öffnen
2. Den Befehl eingeben mit der Emailadresse des Github Accounts:

| $ ssh-keygen -t rsa -b 4096 -C 'DEINE EMAILADRESSE'        |    Regeniert den SSH Key     |
| ------------- |:-------------:|

3. Danach wird ein Key erstellt und man muss mit Enter bestätigen.

4. Nun erstellt man ein Passwort.

### SSH-Key hinzufügen

1. Anmelden unter www.github.com
2. Auf Benutzerkonto klicken (oben rechts) und den Punkt Settings aufrufen
3. Unter den Menübereichen auf der linken Seite zum Abschnitt SSH und GPG keys wechseln
4. Auf New SSH key klicken
5. Im Formular unter Title eine Bezeichnung vergeben (z.B. MB SSH-Key)
6. Den zuvor kopierten Key mit CTRL + V einfügen und auf Add SSH key klicken
7. Der Schlüssel (SSH-Key) sollte nun in der übergeordneten Liste auftauchen

## 02 - Git Client

Jetzt muss der Git Client installiert werden. Dieser ermöglicht uns, Cloud-Repositories zu klonen, zu pullen (herunteraden) oder ein lokales Repository zu pushen (hochladen).

Hierzu müssen folgende Schritte durchgeführt werden:

1. Git Client installieren
2. Konfigurieren des Git Clients

| Befehle      |    Bedeutung    |
| ------------- |:-------------:|
| $ git config --global user.name <username>       |      Konfiguration Username  |
| $ $ git config --global user.email <e-mail>   | Konfiguration Email

3. Konfiguration abgeschlossen

### Repository klonen

1. Terminal öffnen

| Befehle      |    Bedeutung    |
| ------------- |:-------------:|
| $ git clone https://github.com/ferzanagehringer/M300/     |      Repository klonen  |
| $ git pull    |      zeigt ob es up to date ist   |
|   $ git status   |     Geänderte Datei(en) werden rot aufgelistet |

### Repository herunteraden

1. Terminal Bash öffnen
2. Ordner im gewünschtenn Verzeichnis erstellen
3. Repository mit SSH klonen:

| Befehle      |    Bedeutung    |
| ------------- |:-------------:|
|  $ git clone git@github.com:ferzanagehringer/M300.git    |      Klonen des Respository mit SSH  |

### Repository pushen (hochladen)

1. Terminal Bash öffnen
2. Zum Verzeichnis gehen des repository
3. Dateien dem Upload hinzufügen:

| Befehle      |    Bedeutung    |
| ------------- |:-------------:|
|  $ git add -a.  |      Upload wird "commited" > Kommentar zu Dokumentationszwecken ist dafür notwendig  |

4. Upload commiten:

| Befehle      |    Bedeutung    |
| ------------- |:-------------:|
|   $ git commit -m "Mein Kommentar" |      commiten |

5. Zum Schluss noch pushen:

| Befehle      |    Bedeutung    |
| ------------- |:-------------:|
|    $ git push |      pushen (hochladen) |


VirtualBox
--



Vagrant
--

Wenn man schon einmal selber die VM's erstellt hat, dann weiss man für mehrere braucht man lange. Für eine schnellere Variante gibt es Vagrant. Mit dem können VM's automatisch erstellt werden mit nur einem kurzen Code.

Im gewünschten Verzeichnis kann man mit einer Zeile, die VM erzeugen:

| Befehle      |    Bedeutung    |
| ------------- |:-------------:|
|  $ vagrant init ubuntu/xenial64 |   Vagrantfile erzeugen |
|  $ vagrant up --provider virtualbox | Virtuelle Maschine erstellen & starten |



Visual Studio
--

Ich habe mich nicht für Visual Studio entschieden, sondern für Atom. Diese wurde mir von einem Kollegen empfohlen. Das ist ein Editor. Dieser wird benutzt, um dort zu dokumentieren, für eine gute Übersicht. Natürich muss es zuerst mit Github verbunden werden.




## Sicherheitsaspekte sind implementiert


Atom (Visual Studio Code)
--





Virtual Box
--





Vagrant
--
