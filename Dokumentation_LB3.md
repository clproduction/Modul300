# Modul300
Modul 300 Dokumentation / LB3
#
## Docker auf VMWARE betreiben
### Damit es funktioniert muss man eine Einstllung im Hypervisor tätigen.&nbsp;
Wenn diese Einstellung nicht aktiviert ist wird es beim Installieren eine Fehlermeldung geben.

![](https://github.com/clproduction/Modul300/blob/master/img_LB3/Virtualize.PNG) \

*Grafische Darstellung*


    +---------------------------------------------------------------+
    !                                                               !	
    !                                                               !
    !    ! mysql, phpmyadmin                !                       !  
    !    ! Port: 3306, 8081                 !                       !         
    !    ! Volume: /var/lib/docker/volumes  !                       !                                                               
    !                                                               !
    !                                                               !	
    ! Container                                                     !	
    +---------------------------------------------------------------+
    ! Container-Engine: Docker                                      !	
    +---------------------------------------------------------------+
    ! Guest OS: Debian                                              !	
    +---------------------------------------------------------------+
    ! Hypervisor: HyperV                                            !	
    +---------------------------------------------------------------+
    ! Host OS: Windows	v2004 (On VMWARE)                           !
    +---------------------------------------------------------------+


## Docker-Container kombinieren
#
### Use multi-stage builds
Multi-stage builds are a new feature requiring Docker 17.05 or higher on the daemon and client. Multistage builds are useful to anyone who has struggled to optimize Dockerfiles while keeping them easy to read and maintain.&nbsp;

With multi-stage builds, you use multiple FROM statements in your Dockerfile. Each FROM instruction can use a different base, and each of them begins a new stage of the build. You can selectively copy artifacts from one stage to another, leaving behind everything you don’t want in the final image. To show how this works, let’s adapt the Dockerfile from the previous section to use multi-stage builds.

### Zwei Container verlinken (-link)
```Ruby
docker run --name my-own-phpmyadmin -d --link my-own-mysql:db -p 8081:80 phpmyadmin/phpmyadmin
```

## Bestehende Container im Backend betreiben
### Der Befehl für das ist sehr simpel
```Ruby
docker run --name my-own-mysql -e MYSQL_ROOT_PASSWORD=mypass123 -d mysql:8.0.1
```
The option -d means that docker will run the container in the background in “detached” mode. If -d is not used the container run in the default foreground mode.
## Volumes Datenablage
#
#### So erstellt man ein neues Volume
```Ruby
docker volume create --name [volume name]
```
#### Container mit gewissem Volume starten
```Ruby
-v [volume name]:[container directory]
```
#### Alle bestehenden Volumes anzeigen
```Ruby
sudo docker volume ls
```
## Wichtige Docker Befehle
#
#### Start a container in background    
```Ruby
docker run -d (Container-Name)
```
#### Stop a container
```Ruby
docker stop (Container-Name)
```
#### Start a stopped container
```Ruby
docker start (Container-Name)
```
#### IP Address
```Ruby
docker inspect -f '{{ .NetworkSettings.IPAddress }}' (Container-Name)
```
#### List Volumes
```Ruby
docker volume ls
```
## Netzwerk Umgebung
#
## Security
#

## Aktive Benachrichtigungen Docker - Services überwachen
#
### Mit Solarwinds Container überwachen
#### 3rd party Monitoring Software Solarwinds 
Sobald man Solarwinds auf dem Host OS installiert hat kann man im Browser auf das Interface zugreifen.
```Ruby
https://my.appoptics.com
```
#### So sieht das Interface dann aus.
![](https://github.com/clproduction/Modul300/blob/master/img_LB3/SolarwindsDockerMonitoringHowItCouldLookLike.png) \
#### Danach muss man noch das Docker Plugin hinzufügen und den Agent in dem Container Installieren.
![](https://github.com/clproduction/Modul300/blob/master/img_LB3/DockerPlugin.PNG) \
Befehl für den Install des Agents
```Ruby
sudo bash -c "$(curl -sSL https://files.solarwinds.cloud/solarwinds-snap-agent-installer.sh)" -s --token 7c0852619bd4280e920d81b9f54d385d4b982930fafa1bd750f41a90908fea42
```
## Docker Container absichern
#
*Image speicher
*Volume erstellen (Anderer Speicherort)
*

### Mit dem Command 
```Ruby
Docker Commit -p <Container-Name> example/example
```
Ein Commit macht ein image des Container in dem Aktuellen stand. Es wird später auf dem Host OS gespeichert. Hier sieht man wo es agespeichert wurde.

*Wie man sieht was für images man hat kann man diesen Command verwenden.*
```Ruby
Docker images
```
* -p steht für pause container while commit
* example/example ist der Name des IMAGES
## Testfälle
#

1. Kann ich den Docker Container im hintergrund starten?
![](https://github.com/clproduction/Modul300/blob/master/img_LB3/background.PNG)
Meine Container laufen alle im background, funktioniert!
2. Ist mein erstelltes Volume wirklich meinem Container zugewiesen?
![](https://github.com/clproduction/Modul300/blob/master/img_LB3/Volume.PNG) \
Wie man sieht ist dasa Volume für diesen Webserver "testvolume", dass wurde von mir erstellt und bei starten des Container habe ich es angegeben.
3. Kann ich auf die PHPMYADMIN seite zugreifen? (http://localhost/)
![](https://github.com/clproduction/Modul300/blob/master/img_LB3/PHPMyAdmin.PNG) \
Funktioniert!
## Quellenangaben
#
**Quelle 1**
Offizielle Docker Dokumentation 
[https://docs.docker.com/)&nbsp;

**Quelle 2**
Provider des images & Anleitung (mysql)
https://medium.com
## Vergleich Vorwissen - Wissenszuwachs
#
## Reflektion
