#FHNW Active Directory Folder Sync Script
===

Dieses Skript verbindet sich bei Programmstart automatisch mit dem VPN der FHNW (Passwort ausgelesen aus dem Schlüsselbund von OS X), mountet das Active Directory und synchronisiert unidirektional den angegebenen (Klassen-)Ordner in den angegebenen lokalen Ordner.

## 1. Konfiguration
===

### 1.1 Vorbedingungen
====
##### Schlüsselbund
Im OS X Programm "Schlüsselbund" muss unter "Anmeldung" ein Eintrag mit 
**FHNW** (und natürlich Passwort) vorhanden sein.

##### rsync 3.0
Das Unix-Programm `rsync` muss in der Version 3.x installiert sein (OS X Standard: 2.6)  
*Hinweis:*
Welche Version installiert ist, sieht man, wenn man im Terminal `rsync --version` eingibt.  
  
**Installation rsync 3:**  
1. Am einfachsten geht dies über Homebrew
[brew.sh](http://brew.sh/)  
2. `brew update`  
3. `brew install rsync`  
4. Computer neustarten


##### Datei anpassen
.spct-Datei mit dem Applescript-Editor (in OS X standardmässig vorhanden) öffnen


### 1.2 Skriptvariablen
====
##### `theText`
Was in diesem Fenster steht unter "VPN-Verbindung" (Sprachspezifisch)
![alt](http://i.imgur.com/UIJlmNR.png)

##### `theVPN`
Wie die spezifische VPN-Verbindung unter "Systemeinstellungen" > "Netzwerk" heisst (hier: VPN FHNW)
![alt](http://i.imgur.com/9H07Hxn.png)

##### `sourcefolder`
Hier Klassenordner eintragen (Active Directory: `CMD+I` auf gewünschten Ordner, Pfad anpassen, **nicht einfach kopieren**)

##### `localfolder`
Hier gewünschten lokalen Ordner eintragen (Dropbox?)

## 2. App exportieren
===
Im Applescript-Editor: Ablage > Exportieren > Dateiformat: Programm

### Hinweis: OS X 10.9 Maverick
Unter Maverick muss folgendes eingestellt werden, sonst gibt es ein Berechtigungsproblem:
AppleScript-Editor bzw. die oben erstelle Applikation muss Häkchen erhalten unter Systemeinstellungen > Sicherheit > Privatsphäre > Bedienungshilfen
![alt](http://i.imgur.com/SWguUPt.png)

## Code from
===
#### FHNW VPN Connector (Jan Fässler)+ [http://janfaessler.ch/archives/822](http://janfaessler.ch/archives/822)+ [https://github.com/janfaessler/FHNW-VPN-Connector](https://github.com/janfaessler/FHNW-VPN-Connector)
#### Automated token generation and VPN logins (Corey Gilmore)+ [http://coreygilmore.com/projects/automated-securid-token-generation-and-vpn-login-applescript/](http://coreygilmore.com/projects/automated-securid-token-generation-and-vpn-login-applescript/)#### Andy Breuhan+ [http://www.andybreuhan.de/2010/04/06/mac-os-x-10-6-vpn-passwort-speichern/](http://www.andybreuhan.de/2010/04/06/mac-os-x-10-6-vpn-passwort-speichern/)
