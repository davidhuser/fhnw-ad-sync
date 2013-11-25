#FHNW Active Directory Folder Sync

Dieses Skript verbindet sich bei Programmstart automatisch mit dem VPN der FHNW (Passwort ausgelesen aus dem Schlüsselbund von OS X), mountet das Active Directory und synchronisiert unidirektional den angegebenen (Klassen-)Ordner in den angegebenen lokalen Ordner.

## 1. Konfiguration

### 1.1 Vorbedingungen
##### Schlüsselbund
Im OS X Programm *«Schlüsselbundverwaltung»* muss unter dem Schlüsselbund *«Anmeldung»* ein Eintrag mit 
*«Name für Schlüsselbundeintrag»* **FHNW** (und Accountname [*vorname.nachname*] und Passwort) vorhanden sein.

##### rsync 3.x
Das Unix-Programm `rsync` **muss** in der Version 3.x installiert sein (OS X Standard: 2.x)  
*Hinweis:*
Welche Version installiert ist, sieht man, wenn man im Terminal `rsync --version` eingibt.  
  
**Installation rsync 3.x:**  
1. Am einfachsten geht dies über [Homebrew](http://brew.sh/), ein Package Manager für OS X:   
=> Homebrew installieren *inkl. aktualisierte XCode Developer Tools*  
2. Terminal: `brew doctor` ... sollte wenn möglich keine Errors generieren   
3. Terminal:  
`brew tap homebrew/dupes`  
`brew install rsync`  
4. Terminal: `/usr/local/bin/rsync --version` ... sollte nun Version 3.x zeigen.


##### Skript anpassen
die [.scpt-Datei FHNW-AD-SYNC.scpt](https://github.com/davidhuser/fhnw-ad-sync/blob/master/FHNW-AD-SYNC.scpt?raw=true) mit dem Applescript-Editor (in OS X standardmässig vorhanden) öffnen.


### 1.2 Skriptvariablen
##### `theText`
Was in diesem Fenster steht unter *«VPN-Verbindung»* (sprachspezifisch)
![theText](http://i.imgur.com/SgGjxzA.png)

##### `theVPN`
Name der VPN-Verbindung unter *«Systemeinstellungen»* > *«Netzwerk»* (hier: VPN FHNW)
![theVPN](http://i.imgur.com/ZBEliHC.png)

##### `localfolder`
Hier gewünschten lokalen Ordner (Dropbox?) eintragen (Pfad herausfinden:`CMD+I` auf Ordner)

##### `sourcefolderlist`
Hier **einen oder mehrere Ordner** mit Komma und alt+Enter (siehe Beispiel im Code) vom Active Directory eintragen (`CMD+I` auf gewünschten Ordner, Pfad anpassen, **nicht einfach kopieren**, es braucht `/Volumes/e_18_data11$...`)  

## 2. App exportieren

**1.** Im Applescript-Editor: Ablage > Exportieren... > Name geben, Dateiformat: Programm, Haken «nur ausführbar» setzen  
**2.** .app in «Programme» ziehen

### Hinweis: OS X 10.9 Maverick
Unter Maverick muss folgendes eingestellt werden, sonst gibt es ein Berechtigungsproblem:
die oben erstelle .app muss Häkchen erhalten unter Systemeinstellungen > Sicherheit > Privatsphäre > Bedienungshilfen
![Berechtigung](http://i.imgur.com/cEUxUbG.png)

## Basiscode von:
#### FHNW VPN Connector (Jan Fässler)+ [http://janfaessler.ch/archives/822](http://janfaessler.ch/archives/822)+ [https://github.com/janfaessler/FHNW-VPN-Connector](https://github.com/janfaessler/FHNW-VPN-Connector)
#### Automated token generation and VPN logins (Corey Gilmore)+ [http://coreygilmore.com/projects/automated-securid-token-generation-and-vpn-login-applescript/](http://coreygilmore.com/projects/automated-securid-token-generation-and-vpn-login-applescript/)#### Andy Breuhan+ [http://www.andybreuhan.de/2010/04/06/mac-os-x-10-6-vpn-passwort-speichern/](http://www.andybreuhan.de/2010/04/06/mac-os-x-10-6-vpn-passwort-speichern/)

===## Changelog
**0.2** – mehrere Ordner möglich zu syncen  
**0.1** – init
