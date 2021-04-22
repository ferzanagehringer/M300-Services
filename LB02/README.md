LB02
==

Einleitung
--
In der folgenden Dokumentation habe ich alles zum Thema Container, Docker, Kubernetes und deren Sicherheit dokumentiert was ich neu dazu gelernt habe und auch die Aufgaben dazu dokumentiert.

Container
--
Container verpacken eine Anwendung und alle zu ihrer Ausführung erforderlichen Dateien in ein handliches Paket. Dies vereinfacht dann die Installation und den Betrieb von Server-Anwendungen wie auch das Management und die Verteilung. Container erleichtern damit also den Umgang mit den komplexen Server-Anwendungen und ermöglichen die Automatisierung von Rollout-Prozessen im Rechenzentrum. Dies ist wiederrum wichtig für die Bereitstellung von Anwendungen innerhalb Cloud-Umgebungen. Container machen Anwendungen unabhängiger von der Umgebung, in der sie ausgeführt werden. Sie sind damit ähnlich einer virtuellen Maschine (VM). Während eine VM jedoch ein vollständiges Betriebssystem sowie Applikationen enthält, teilen sich mehrere Container einen Betriebssystemkern. Jede Anwendung erhält lediglich einen neuen User Space und damit eine komplett isolierte Umgebung.

![Theorie Container](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/Theorie%20Container.jpg)


Docker
--
Die IT-Software Docker ist eine Containerisierungstechnologie, die die Erstellung und den Betrieb von Linux Containern ermöglicht. Mit Docker kann man Container wie extrem leichtgewichtige, modulare virtuelle Maschinen behandeln. Und mit diesen Containern erhält man Flexibilität man können sie erstellen, einsetzen, kopieren und zwischen Umgebungen bewegen, was wiederum die Optimierung der Apps für die Cloud unterstützt. Die Docker-Technologie verwendet den Linux Kernel und seine Funktionen wie Cgroups und namespaces, um Prozesse zu isolieren, damit diese unabhängig voneinander ausgeführt werden können. So wird die Infrastruktur besser genutzt und gleichzeitig die Sicherheit bewahrt, die sich aus der Arbeit mit getrennten Systemen ergibt. Containertools, einschließlich Docker, arbeiten mit einem Image-basierten Bereitstellungsmodell. Das macht es einfacher, eine Anwendung oder ein Paket von Services mit all deren Abhängigkeiten in mehreren Umgebungen gemeinsam zu nutzen. Docker automatisiert außerdem die Bereitstellung der Anwendung (oder Kombinationen von Prozessen, die eine Anwendung darstellen) innerhalb dieser Container-Umgebung.

###### *Vorteile:*

* Modularität
* Layer und Image-Versionskontrolle
* Rollback
* Schnelle Bereitstellung

###### *Wichtigsten Komponente:*

* Docker Client
* Docker Daemon
* Images
* Docker Registry
* Container

###### *Docker Client*

In der Kommandozeile wird er gestartet. Da er über HTTP kommuniziert, ist die Verbindung zu Docker Daemons einfach herzustellen.

###### *Docker Daemon*

Der Docker Daemon erstellt, führt und überwacht Container. Er speichert und baut aber auch Images. Durch das Host-Betriebssytem wird er gestartet.

###### *Images*

Ein Image besteht aus einem Namen und deren Version. UM Container zu starten braucht man Images, die Umgebungen sind, die man nicht verändern kann sondern nur neu erstellen.

###### *Docker Registry*

Im Docker Registry werden alle Images abgelegt und verteilt.

###### *Container*

Dies sind dann die ausgeführten Images. Hier kann man dann auch Änderungen vornehmen, jedoch nur die Änderungen zum originalen Image werden gespeichert.

![Theorie Docker](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/Docker%20Theorie.png)

Sicherheit
--
Das Überwachen und Protokollieren von laufenden Containern ist sehr wichtig. Bei den Microservices ist es wegen der höheren Zahl von Rechnern noch wichtiger.

##### Sicherheitsaspekte

###### Container-Breakouts
Wenn man im Container ein root ist, wird man auch root auf dem Host, dies ist sehr problematisch, da ein Angreifer der Zugriff auf einen Container erhält, auch Zugriff auf den Host bekommen kann.

###### Vergiftete images
Beim Herunterladen von Images, kann man sich nicht sicher sein, ob es vielleicht manipuliert ist oder nicht. Also wird der Host und deren Daten gefährdet.

###### Denial-of-Service Angriffe
Da sich alle Container die Kernel Ressourcen teilen, könnte ein Container den Zugriff auf bestimmte Ressourcen ganz für sich beanspruchen oder andere Container "verhungern" lassen.

###### Verratene Geheimnisse
Um auf einen Container oder eine Datenbank zugreiffen zu können, benötigt man einen API-Schlüssel oder einen Benutzernamen und Passwort. Ein Hacker könnte dies herausfinden.

###### Kernel Exploits
Der Kernel wird von allen Containern und dem Host verwendet, somit ist die Angriffsstelle mit deutlich mehr Auswirkung verbunden.

###### Least Privilage
Jeder Container und Prozess sollte nur mit so viel Zugriffsrechten und Ressourcen laufen, wie es gerade braucht.

##### Beispiele

###### Berechtigungen eingrenzen
>$ RUN groupadd -r user_grp && useradd -r -g user_grp user $ USER user

###### Speicher begrenzen
>$ docker run -m 128m --memory-swap 128m amouat/stress stress --vm 1 --vm-bytes 127m -t 5s

###### Neustarts begrenzen
>$ docker run -d --restart=on-failure:10 my-flaky-image

###### Zugriffe auf die Dateisysteme begrenzen
>$ docker run --read-only ubuntu touch x

###### Capabilities einschränken
>$ docker run --cap-drop all --cap-add CHOWN ubuntu chown 100 /tmp

###### Ressourcen einschränken
>$ docker run --ulimit cpu=12:14 amouat/stress stress --cpu 1_

##### 3 Aspekte der Container Absicherung
1. Ein Passwort erstellen
2. Host Ordner Zugriff einschränken (Least Privilege)
3. Einen Container als none root anlegen/erstellen

Kubernetes
--
Kubernetes ist eine portable, erweiterbare Open-Source-Plattform zur Verwaltung von containerisierten Arbeitslasten und Services, die sowohl die deklarative Konfiguration als auch die Automatisierung erleichtert.

Kubernetes hat eine Reihe von Funktionen. Es kann gesehen werden als:

* eine Containerplattform
* eine Microservices-Plattform
* eine portable Cloud-Plattform und vieles mehr.

##### Wichtige Merkmale:
* Immutable statt Mutable.
* Deklarative statt Imperative Konfiguration.
* Selbstheilende Systeme - Neustart bei Absturz.
* Skalieren der Services durch Änderung der Deklaration.
* Entkoppelte APIs – LoadBalancer / Ingress (Reverse Proxy).
* Anwendungsorientiertes statt Technik Denken.
* Abstraktion der Infrastruktur statt in Rechnern Denken.


Kubernetes Cluster
--
![Kubernetes Theorie](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/Kubernetes%20Theorie.png)

Bei einem Cluster wird ein Kubernetes Master und mehrere Worker erzeugt. Diese Umgebung eignet sich zur Demonstration einer Verteilten Umgebung

Zusatzaufgaben
--

##### Image Bereitstellen
1. Zuerst muss man ein Container erstellen, mit dem Image, welches man auf Docker pushen will.
2. Danach muss man diesen pushen in das Dockerhub.

##### Continous Integration
Ist der den Prozess des fortlaufenden Zusammenfügens von Komponenten zu einer Anwendung beschreibt.

Das Ziel der kontinuierlichen Integration ist die Steigerung der Softwarequalität.

Üblicherweise wird dafür nicht nur das Gesamtsystem neu gebaut, sondern es werden auch automatisierte Tests durchgeführt und Software-Metriken zur Messung der Softwarequalität erstellt.

##### Cloud Integration
Mithilfe der Cloud-Integration lassen sich lokal gespeicherte Daten nahtlos mit Informationen und Anwendungen in der Cloud nutzen.
Heute ist die Virtualisierung besser als früher. Früher hatte man alles physisch und heute alles in der Cloud.

*Vorteile:*
* Netzwerkverkehrsmuster
* Nutzerverhalten
* Sicherheitsrelevante Ereignisse, sowohl extern als auch in Ihrer Umgebung
* Compliance-Informationen
* Fehler und Anomalien, die Ihre Performancedaten beeinflussen
* Ressourcennutzung

*iPaas*

Bei Integration-Platform-as-a-Service handelt es sich um eine unkomplizierte Lösung für das Hosting, die Entwicklung und die Integration von Cloud-Daten und -Anwendungen.

*Saas*

Software as a Service. SaaS ist neben Infrastructure as a Service (IaaS) und Platform as a Service (PaaS) eine der drei Hauptkategorien des Cloud Computing.

*Iaas*

 Infrastruktur as a Service. IT Infra­struktur wie Rechenleistung, Datenspeicher oder Netzkapazität bedarfsgerecht aus der Cloud zu be­zie­hen.

Testfälle
--

Zuerst muss man auf den Server Zugriff bekommen:

1. Im cmd folgenden Befehl eingeben: *$ssh ubuntu@IP*
2. Das angegebene Passwort danach eingeben.

###### Kombination von Docker und Container:
1. Zuerst folgenden Befehle eingeben:
>$docker run --name osticket_mysql -d -e MYSQL_ROOT_PASSWORD=secret \ -e MYSQL_USER=osticket -e MYSQL_PASSWORD=secret -e MYSQL_DATABASE=osticket mariadb

2. Nach dem ersten Befehl dann folgenden eingeben:
>$docker run --name osticket -d --link osticket_mysql:mysql -p 5050:80 osticket/osticket

Nachdem man diese Befehle eingegeben hat, sollte man mit diesem URL: *IP:5050* auf diese Seite kommen:

![Erster Schritt](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/Erster%20Schritt.png)

###### Bestehende Container als Backend, Desktop-App als Fortend einsetzen:

1. Zuerst erstellt man ein Dockerfile: *$docker build -t "Name" -f Dockerfile*

![zweiter Schritt](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/Zweiter%20Schritt.png)

2. Danach mir dem Befehl: *docker images* kontrollieren ob es auch wirklich erstellt wurde:

![dritter Schritt](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/dritter%20Schritt.png)

3. Nun erstellt man den Container, welcher auf Port 2020 hört: *$docker run -dit --name "Name" -p 2020:80 "Name"*

![vierter Schritt](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/vierter%20Schritt.png)

###### Volumes zur persistenten Datenablage einrichten:

1. Diesen Befehl eingeben um ei Volume zu erstellen:
> $ docker run -d \ --name=nginxtest \ --mount source=nginx-vol,destination=/usr/share/nginx/html,readonly \ nginx:latest

2. Kontrolliern ob es erstellt wurde. Wenn bei RW *false* steht, ist es schreibgeschützt:

![fünfter Schritt](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/f%C3%BCnfter%20Schritt%20RWFalse%20%20schreibgesch%C3%BCtzt.png)

Service Überwachung
--
Mit folgendem Befehl kann man die Monitoring Lösung einrichten:
> $docker run -d --name cadvisor -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys:ro -v /var/lib/docker/:/var/lib/docker:ro -p 1010:8080 google/cadvisor:latest

Mit follgendem Link sollte man auf das Monitorring Tool kommen: *IP:1010*

![sechster Schritt](https://github.com/ferzanagehringer/M300-Services/blob/main/LB02/Bilder/sechster%20schritt.png)


Befehle
--
| Befehl      |    Bedeutung    |
| ------------- |:-------------:|
| $docker build -t "Name" | Image von Dockerfile erstellen |
| $docker ps | alle container anzeigen die gestartet wurden |
| $docker run | zum starten neuer Containe |
| $docker run -dit --name "Name" -p 8080:80 "Name" | Container wird erstellt und hört auf Port 8080 |
| $docker images | gibt eine Liste lokaler Images aus |
| $docker logs | Gibt die logs eines Containers aus |
| $docker rm/rmi | Entfernt Container / Entfernt Image |
| $ docker run -d \ --name=nginxtest \ --mount source=nginx-vol,destination=/usr/share/nginx/html,readonly \nginx:latest | schreibgeschütztes Volume erstellen |
| $docker volume inspect nginx-vol | Volumes kontrollieren |
| $docker stop/start/remove "Name/ID" | Docker starten,stoppen, löschen |


Reflexion / Lernvortschritt
--
Bei der LB02 hatte ich vorher noch keine Ahnung von diesen Themen. Ich hatte auch recht Mühe mich mit diesem Thema anzufreunden, da ich es nicht direkt verstanden habe. Doch langsam Schritt für Schritt, find ich an zu verstehen um was es genau geht und wieso man welche Schritte macht. Die Inputs von unserem Lehrer haben auch recht geholfen, denn er hat es uns vorgezeigt und dann auch gleich erklärt wieso man dies mach odert was der vorgezeigte Schritt genau bewirkt. Am meisten haben mir jedoch die Übungen geholfen. Dadurch, dass ich die Übungen gemacht habe, habe ich vieles dazugelernt, anstatt nur alles durch die Theorie zu lernen. Nun weiss ich was eine Container, Docker und Kubernetes ist. Ich kann auch einen Container erstellen und ein Dockerfile erstellen, wie auch ein Image. Ich weiss auch nicht nur, wie man diese erstellt, sondern auch was für Sicherheitsmassnahmen man treffen kann, um dies zu schützen. Also im Grossen und Ganzen fand ich dieses Modul sehr interessant und eine grosse Wissensbereicherung. Ich fand es auch sehr cool, dass wir vieles selbst versuchen durften.
