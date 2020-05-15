# Dokumentation Modul 300

**Voraussetzungen**

* Virtual Box
* Vagrant
* Visualstudio Code (Markdown extention)
* Git-Bash
* Github Account
* SSH-Key für Client verbunden mit Github
  

**Client SSH-Key erstellen**

Cyrill@Faxerhino MINGW64 ~
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

*Standart Speicherort %HOME%/.ssh/id_rsa.pub
