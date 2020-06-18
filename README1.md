# Dokumentation Modul 300

**Voraussetzungen**

* Virtual Box
* Vagrant
* Visualstudio Code (Markdown extention)
* Git-Bash
* Github Account
* SSH-Key für Client verbunden mit Github
  

**Client SSH-Key erstellen für Github**

 *Link:_https://github.com/settings/keys_*

    $ ssh-keygen -t rsa -b 4096 -C ***"Email die auch bei Github registriert ist!"***
Generating public/private rsa key pair.

    Enter file in which to save the key (/c/Users/Cyrill/.ssh/id_rsa):
Created directory '/c/Users/Cyrill/.ssh'.

    Enter passphrase (empty for no passphrase):***(passwort setzen)***
    Enter same passphrase again:***(passwort setzen)***
Your identification has been saved in /c/Users/Cyrill/.ssh/id_rsa
Your public key has been saved in /c/Users/Cyrill/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:Xkyt4NOGXCevjBFm+1x4+IIrlSa8blyAHQdhBTbVE/o c.blumer008@gmail.com
The key's randomart image is:
+---[RSA 4096]----+
|      B*o...     |
|     o....o.     |
|     o o* +.o    |
|    . o= @ B     |
|     . .S.E +    |
|      o.=@ =     |
|     . *+ * .    |
|      =  . .     |
|     o...        |
+----[SHA256]-----+

* Standart Speicherort %HOME%/.ssh/id_rsa.pub

## Wissensstand

#### Linux

Der Linux kernel ist ein Open Source Kernel, dass heisst jeder darf damit machen was er will. Auch wenn das heisst das man eine Distribution erstellt und diese danach für Geld weiterverkauft. Der Ursprüngliche ersteller des Kerns bekommt keinen Anteil. In ein paar Jahren wird fast alles auf Linux basieren, schon heute ist sehr viel mit Linux aufgebaut.

#### Virtualisierung

Bei Virtualisierung ist die Hardware nicht fix angebunden sondern eher in Ressourcen aufgeteilt die man hinzufügen kann oder entfernen kann. Das heisst man kann eine Virtuelle Maschine erstellen und ihr Ressourcen zuweisen, jedoch kann man nicht mehr Ressourcen verteil wie man auch auf dem Host hat. Eine Virtuelle maschine ist nicht verbunden mit dem Host PC, es hat ihre eigenen Komponenten, OS und alles drum herum.

#### Vagrant

Vagrant ist eine Virtuelle Container lösung, dass heisst man kann auf abruf den "Container" hervorholen. Vagrant ist extrem Ressourcen spaarend und kann extrem einfach migriert werden, da man die meisten Informationen aus der Cloud holt. Vagrant ist sehr umfassend und hat grosses Potenzial wenn man es ausnutzt.

#### Mark Down

Mark Down ist wie ich es mir vorstelle, ähnlich wie HTML. Man kann mit gewissen Sonderzeichen definieren ob man ein Titel will oder normalen Text. Als beispiel, **TEXT** ist ein dicke überschrift in HTML glaube h4 bin mir nicht sicher.

#### Systemsicherheit

Unter Systemsicherheit verstehe ich das abdichten und härten von dem Service den man schützen möchte. Das kann man durch Benutzerrechte oder SSL/TLS. Es gibt tausende wege wie man ein Service schützen kann, dass waren jetzt einfach zwei beispiele.
