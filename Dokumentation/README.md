M300 Services
==

Einleitung
--
Im Modul 300 haben wir die LB01, indem wir verschiedene Aufgaben erfüllen mussten. In dieser Dokumentation sind meine Arbeitsschritte festgehalten und auch alles was ich neu dazu gelernt habe.

Inhaltsverzeichnis
--
* Git Client / Git Account
* Atom (Visual Studio Code)
* Virtual Box
* Vagrant
* Sicherheitsaspekte
* Glossar


Git Client / Git Account
--
Zuerst muss man einen GitHub-Account einrichten. Dieser dient dann als "Cloud-Speicher" für diese Dokumentation.

##### Account erstellen

1. Zuerst bin ich auf die Website www.github.com gegangen und habe ein Benutzerkonto mit meiner Schulmail erstellt.
2. Nach dem Erstellen des Benutzerkontos, musste ich noch mein Mail verifizieren und mich anschliessend auf GitHub anmelden.

##### Repository erstellen

Nachdem ich dann mein Benutzerkonto erstellt habe, musste ich ein Repository erstellen, damit ich dort dann ein Readme File erstelle um diese Dokumentation zu führen.

1. Zuerst musste ich mich unter www.github.com mit meinem erstellten Benutzerkonto anmelden.
2. Auf der Startseite musste ich dann ein neues Projekt erstellen.
3. Dann habe ich unter **Repository name** den Namen M300-Services definiert.
4. Dann musste ichh beim Radio Button **Public** lassen.
5. Nachher den Haken bei **Initialize this respository with a README** setzen.
6. Zum Schluss dann auf **Create respository** geklickt.



### SSH-Key erstellen

1. Zuerst das Terminal Bash öffnen
2. Danach den Befehl eingeben mit der Emailadresse des Github Accounts:

| Befehl      |
| ------------- |
| $ ssh-keygen -t rsa -b 4096 -C 'ferzana.gehringer@edu.tbz.ch'       |

3. Nachher wird dann ein Key erstellt und mit Enter kann man das dann bestätigen.

4. Dannach erstellt man ein Passwort.

### SSH-Key hinzufügen

Der Key ist nun erstellt, aber wir müssen diesen noch hinzufügen:
1. Zuerst musste ich mich anmelden unter www.github.com
2. Auf Benutzerkonto klicken (oben rechts) und den Punkt Settings aufrufen
3. Unter dem Menübereichen auf der linken Seite zum Abschnitt SSH und GPG keys wechseln
4. Auf New SSH key klicken
5. Im Formular unter Title eine Bezeichnung vergeben
6. Den zuvor kopierten Key mit CTRL + V einfügen und auf Add SSH key klicken
7. Der Schlüssel (SSH-Key) sollte nun in der übergeordneten Liste auftauchen

## Git Client

Nun muss man den Git Client installieren. Der Git Client ermöglicht und, die Cloud Repositories zu hochladen (pullen), zu klonen und auch ein lokales Repository zu hochladen (pushen).

Um dies zu ermöglichen muss man folgende Schritte ausführen:

1. Zuerst muss man den Git Client installieren
2. Wenn man den Git Client installiert hat, muss man den Git Client konfigurieren mit folgenden Befehlen:

| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
| $ git config --global user.name <username>       |      Konfiguration Username  |
| $ $ git config --global user.email <e-mail>   | Konfiguration Email


### Repository klonen

1. Zuerst öffne ich das Terminal
2. Dannach führt man folgende Befehle durch:

| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
| $ git clone https://github.com/ferzanagehringer/M300-Services     |      Repository klonen  |
| $ git pull    |      zeigt ob es "up to date" ist   |
|   $ git status   |     Geänderte Datei(en) werden dort aufgelistet |

### Repository herunteraden

1. Zuerst öffnet man das Terminal Bash
2. Man geht dann in den gewünschten Verzeichnes, indem man dann den Ordner erstellt.
3. Dannach klont man das Repository mit SSH. der Befehl dazu:

| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
|  $ git clone git@github.com:ferzanagehringer/M300.git    |      Klont das Respository mit SSH  |

### Repository pushen (hochladen)

1. Zuerst öffnet man das Terminal Bash
2. Man geht hier wieder zum gewählten Verzeichnis indem das Repository drin ist.
3. Dann kann man mit folgendem Befehl den Upload durchführen:

| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
|  $ git add -a  |      Upload wird "commited"   |

4. Dannach den Upload commiten:

| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
|   $ git commit -m "Mein Kommentar" |      commiten |

5. Zu guter Letzt noch pushen:

| Befehle      |    Bedeutung    |
| ------------- |:-------------:|
|    $ git push |      pushen (hochladen) |


Atom (Visual Studio Code)
--
Ich habe mich nicht für Visual Studio entschieden, sondern für Atom. Diese wurde mir von einem Kollegen empfohlen. Das ist ein Editor. Dieser wird benutzt, um dort zu dokumentieren, für eine gute Übersicht. Natürich muss es zuerst mit Github verbunden werden.


VirtualBox
--

Hier gibt es nichts zu dokumentieren, den eine VM mussten wir schon öfters erstellen. Hier habe ich dann einfach auf der VirtualBox die Ubuntu VM erstellt.


Vagrant
--
Eine VM zu erstellen auf VirtualBox ist schon anstrengend, aber dann auch noch mehrere zu erstellen ist schon fast unaushaltbar. Vagrant ist deshalb eine tolle Variante für dieses Problem. Mit Vagrant kann man nämlich mit wenigen Befehlen eine VM erstellen.

Im gewählten Verzeichnis kann man dann diese zwei Befehle ausführen:

| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
|  $ vagrant init ubuntu/xenial64 |   erzeugt Vagrant File |
|  $ vagrant up --provider virtualbox | Virtuelle Maschine wird erstellt & gestartet |

Sicherheitsaspekte
--




Glossar
--
