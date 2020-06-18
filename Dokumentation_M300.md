# Dokumentation LB2
Cyrill Blumer
# Einleitung

Das ist meine erste begegnung mit Microservices. Ich finde es spannend, es bietet so viele m�glichkeiten. In LB2 werde ich mich haupts�chlich mit Vagrant auseinander setzen. Es wird von den meisten als einsteiger Software in die Container Welt bezeichnet. Ich habe vor diesem Modul noch nie davon geh�rt aber ich freue mich mehr dar�ber zu lernen.
# Vagrant wichtige befehle

* vagrant up --------- Start and provision Vagrant VM
* vagrant destroy ---- Remove current VM
* vagrant ssh -------- SSH to current Vagrant VM
* vagrant status ----- current state of Vagrant Box
* vagrant reload ----- restart Vagrant Box

# Server

Ich habe einen Webserver und ein FTP Server via Vagrant eingerichtet. Dazu muss man ein Vagrant File erstellen das habe ich mit diesem Command gemacht.

```Ruby
   $ vagrant init hashicrop/bionic64
```
Um die VM zu starten muss man
```Ruby
   $ vagrant up
```
Und dann kann man via SSH verbinden
```Ruby
   $ vagrant ssh
```
# Provisioning

Um das provisioning zu starten muss man zuerst ein provision.sh file erstellen, indem man definiert was installiert werden sollte. z.B.
```Ruby
   #!/usr/bin/env bash

apt-get update
apt-get install -y apache2
if ! [ -L /var/www ]; then
  rm -rf /var/www
  ln -fs /vagrant /var/www
fi
```
Damit es beim Starten aber auch dieses File ausf�hrt muss man es im Vagrantfile noch notieren. In diesem Fall so..
```Ruby
   Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
  config.vm.provision :shell, path: "provision.sh"
end
```
# Security
1. SSH Passwort definiert im Vagrant file
```Ruby
   config.ssh.username = "vagrant"
   config.ssh.password = "vagrant"
end
```
## Webserver mit HTTPS betreiben.
   
Zertifikat und schlüssel erstellen - openssl
```Ruby
$sudo mkdir /vagrant/ssl
$sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /vagrant/ssl/nginx.key -out /vagrant/ssl/nginx.crt
```
Man sollte das hier sehen, da kann man gewisse Daten hinzufügen. Nicht essenziell.
```Ruby
Country Name (2 letter code) [AU]:XY
State or Province Name (full name) [Some-State]:XY
Locality Name (eg, city) []:XY
Organization Name (eg, company) [Internet Widgits Pty Ltd]:XY
Organizational Unit Name (eg, section) []:XY
Common Name (e.g. server FQDN or YOUR name) []:XY
Email Address [] :XY

```
# Firewall
Firewall Rule für die benötigten Ports
```Ruby
sudo ufw enable
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw allow 22/tcp
```
# Reverse Proxy
# Benutzer Rechtevergabe
# SSH-Tunnel
Für mein SSH-Tunell verwende ich Putty, so funktionierts

![](https://github.com/clproduction/Modul300/blob/master/images/SSH_Tunnel.PNG) \
Ich habe für Port 443, 80, 22 eine Weiterleitung erstellt damit die verbindung zwei Teile hat.

![](https://github.com/clproduction/Modul300/blob/master/images/SSH_Tunnel_1.PNG)
Damit ich das nicht jedes mal wieder einstellen muss erstelle ich hier noch ein Profil und speichere somit meine Einstellungen.

# Testing
Was wird getestet->
* Funktionalität
* Sicherheit
* SSH-Tunnel

## Funktionalität

### Startet die VM?
```Ruby
Cyrill@DESKTOP-FCV915D MINGW64 /c/Web/webv2
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'hashicorp/precise32' version '1.0.0' is up to date...
==> default: Resuming suspended VM...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: password
==> default: Machine booted and ready!
==> default: Machine already provisioned. Run `vagrant provision` or use the `--provision`
==> default: flag to force provisioning. Provisioners marked to run always will still run.
```
Funktioniert.

### Lauft der Webserver und kann ich ihn über HTTPS erreichen?
![](https://github.com/clproduction/Modul300/blob/master/images/SSL.PNG) 

Webserver ist erreichbar über die von mir gesetzte IP Adresse und das HTTPS funktioniert auch!

### Verbindung mit SSH-Tunnel
![](https://github.com/clproduction/Modul300/blob/master/images/test-SSH-tunnel.PNG)

Funktioniert auch, Perfekt.\
*Achtung aufpassen das man das erstellte Putty Profil verwendet!*




