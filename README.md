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


### Git Befehle
| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
|   git add -A   |  Änderungen im Verzeichnis zum Zwischenspeicher hinzufügen |
| git commit  | Änderungen auf dem lokalen Git speichern |
| git push  | Änderungen auf dem lokalen Git auf Github pushen |
| git init  | Repo initialisieren |
| git clone  | Github Repo herunterladen |

Atom (Visual Studio Code)
--
Wir haben Visual Studio Code empfohlen bekommen, aber es ist nicht pflicht dies auch zu benutzen. Ich habe mich entschieden Visual Studio Code nicht zu verwenden, sondern Atom. Atom wurde mir von mehreren Klassenkameraden empfohlen. Es ist für mich einfacher zu benutzen und auch übersichtlicher als Visual Studio Code.


VirtualBox
--

 Wie man es schon kennt, muss man eine VM erstellen mit Ubuntu in Virtual Box. Das werde ich nicht dokumentieren, da das nichts neues ist und ich schon weiss wie das funktioniert.


Vagrant
--
Eine VM zu erstellen auf VirtualBox ist schon anstrengend, aber dann auch noch mehrere zu erstellen ist schon fast unaushaltbar. Vagrant ist deshalb eine tolle Variante für dieses Problem. Mit Vagrant kann man nämlich mit wenigen Befehlen eine VM erstellen.

Im gewählten Verzeichnis kann man dann diese zwei Befehle ausführen:

| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
|  $ vagrant init ubuntu/xenial64 |   erzeugt Vagrant File |
|  $ vagrant up --provider virtualbox | Virtuelle Maschine wird erstellt & gestartet |

#### Vagrant Befehle
| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
|  Vagrant init [BOX] | Initialisiert Vagrantfile |
| vagrant port  | Zeigt portmapping zwischen Host und Gast |
| Vagrant status   | Zeigt den Status der Vagrant Box |
| vagrant up  | startet VM aus den Vagrantfiles |
| vagrant halt  | stopt die VM |
| vagrant box add  | lädt Vagrant image local store herunter |
| vagrant box remove  | entfernt Vagrant image local store |
| vagrant ssh "vmname"  | verbindet per ssh auf die VM |
| vagrant ssh  | zeigt die aktuelle Version von Vagrant |
| vagrant destroy  | zerstört die VM |
| vagrant box list  | zeigt alle heruntergeladenen boxes an |



Sicherheitsaspekte
--
### Benutzer und Rechtevergabe

Hier habe ich mit einem Script einen 3 Benutzer, drei Gruppen und die bestimmten Berechtigungen in ein Textfile eingefügt.

>Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provider "virtualbox" do |vb|
end
config.vm.provision "shell", inline: <<-SHELL
sudo useradd Ferzana
sudo useradd Yang
sudo useradd Laura
sudo groupadd IT
sudo groupadd KV
sudo groupadd HR
sudo usermod -a -G IT Ferzana
sudo usermod -a -G KV Yang
sudo usermod -a -G HR Laura
sudo touch file1.txt
SHELL
end

### Firewall
Eine Firewall ist ein Sicherungssystem, welches ein Rechnernetz oder einen einzelnen Computer vor unerwünschten Netzwerkzugriffen schützt und weiter gefasst auch ein Teilaspekt eines Sicherheitskonzepts ist.

Hier habe ich dann auch das gleiche wie bei Benutzer und Rechtevergabe getan:

>Vagrant.configure(2) do |config|
config.vm.box = "ubuntu/xenial64"
config.vm.provider "virtualbox" do |vb|
end
config.vm.provision "shell", inline: <<-SHELL
sudo ufw allow 80/tcp
vagrant ssh web
sudo ufw allow from any to any port 22
sudo ufw allow from any to any port 3306
sudo ufw --force enable
SHELL
end


### Reverse Proxy
Ein Proxy Server ist ein Vermittler in einem Netzwerk, der Anfragen entgegennimmt und sie stellvertretend weiterleitet. Mit Hilfe des Proxy Servers lässt sich die Kommunikation zwischen einem lokalen Client und einem Webserver absichern, verschleiern oder beschleunigen.

Hier musste ich auch wieder den Code in ein Textfile einfügen:

>Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provider "virtualbox" do |vb|
end
config.vm.provision "shell", inline: <<-SHELL
sudo apt-get install apache2 -y
sudo apt-get install libapache2-mod-proxy-html -y
sudo apt-get install libxml2-dev -y
sudo a2enmod proxy
sudo a2enmod proxy_html
sudo a2enmod proxy_http
sudo echo "ServerName localhost" >> /etc/apache2/apache2.conf
sudo service apache2 restart
sudo touch /etc/apache2/sites-enabled/001-reverseproxy.conf
sudo echo "ProxyRequests Off
    <Proxy *>
        Order deny,allow
        Allow from all
    </Proxy>
    ProxyPass /master http://master
    ProxyPassReverse /master http://master" >> /etc/apache2/sites-enabled/001-reverseproxy.conf
SHELL
end


Glossar
--

| Begriff  | Beschreibung  |
| ------------- |:-------------:|
| Git | Es ist ein kostenloses Versionskontrollsystem. Git bietet auch umfassende Unterstützung für das Branching, Merging und Umarbeiten des Repository-Verlaufs. Daraus sind viele innovative, leistungsstarke Workflows und Tools entstanden.   |
| Atom | Ist ein Open-Source-Texteditor.  |
| Visual Studio Code | Ist ein Open-Source-Texteditor. Visual Studio Code basiert auf dem Framework Electron und ermöglicht Syntaxhervorhebung, Code-Faltung, Debugging, Autovervollständigung und Versionsverwaltung. |
| Vagrant | Ermöglicht einfache Softwareverteilung insbesondere in der Software- und Webentwicklung und dient als Wrapper zwischen Virtualisierungssoftware wie VirtualBox. |
| Reverse Proxy | Ein Proxy-Server ist ein dedizierter Computer oder Softwaresystem und dient als Vermittler zwischen einem Endpunktgerät, zum Beispiel einem Computer, und einem anderen Server fungiert, von dem ein Benutzer oder Client einen Dienst anfordert. Der Proxy-Server kann sich auf derselben Maschine wie ein Firewall-Server befinden oder auf einem separaten Server, der Anfragen durch die Firewall weiterleitet. |
| Virtualisierung | Virtualisierung erlaubt es, eine Hardware als mehrere (virtuelle) Maschinen darzustellen. Das Virtualisierungs-System sorgt dafür, dass die Hardware auf die verschiedenen Gast-Systeme verteilt wird. Auf jedem Gast-System wird ein vollständiges Betriebssystem installiert. Im Kontext dieses Betriebssystems kann man seine Applikationen laufen lassen. |
| Linux | Linux ist ein Betriebssystem wie Windows. Allerdings sind die meisten Linux-Betriebssysteme kostenlos und können viel freier konfiguriert werden. |


### Reflexion
Ich habe während der LB01 sehr viel dazu lernen können. Ich habe Vagrant kennengelernt und auch GitHub. Ich konnte auch im Detail mit den Siherheitsaspekten arbeiten und habe auch in diesem Bereich viele neue Dinge dazugelernt. Was ich aber am besten fand, war Vagrant. Ich kann nun viel einfacher und schneller mehrere VM's erstellen. Vorher war dies sehr langsam und ich konnte nicht mehrere auf einaml aufsetzten. Also im Grossen und Ganzen war die LB01 schon sehr informtiv und belehrend.
