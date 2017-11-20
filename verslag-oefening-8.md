# Oefening 8: Aanmaken OUs en gebruikers

## Korte omschrijving

Bij deze oefening maken we OUs aan en gebruikers in de huidige omgeving. 

## Stappenplan

1. OU CAfdelingen aanmaken
2. Aanmaken gebruikers in OU
3. Eigen user account

## Procedure per stap

### 1. OU CAfdelingen aanmaken

MMC Active Directory Users and Computers > Confidas.local rechterklik > New > Organizational Unit (of via icoontje)

"PROTECT CONTAINER FROM ACCIDENTAL DELETION" telkens uitvinken. 

- OU Directie 
- OU Staf 
- OU verkoop 
- OU Administratie 
- OU Productie  
    - OU FabricageAalst 
- OU automatisering 

### 2. Aanmaken gebruikers in OU

Via icoontje "New user in current container" in de Users and Computers MMC. 

Zie opdracht. 

In WinClient1 aanmelden als POLIFORMA\mad_sme. 

#### Maak voor Madelief Smets een quata beperking aan op volme PFSV1Data (F:). 100 MB met waarschuwing op 90 MB 

WinServer1 > Verkenner > WinServ1Data F: rechterklik > Properties > Quota > Quota entries... > Quota New Entry > Advanced > "mad" Find Now > selecteer Madelief Smets > OK > Limits setten > OK. 

#### Stel voor User Account Madelief Smets volgende eigenschappen in 

MMC AD Users and Computers > OU Directie > Madelief Smets rechterklik > Properties

- Log on to: DESKTOP-I0U99TC (dit is te vinden onder WinClient1 > Verkenners > Deze PC rechterklik > Eigenschappen)

#### Log in als Madelief Smets en kijk of de mapping naar de homefolder er staat 

Jap, mapping is in orde!

#### Controleer op DC PFSV1 of de folder Madelief Smets staat in de Profielmap 

Na inloggen kwam het profielmapje er ook bij. 

#### Controleer of voor elke gebruiker een homefolder is aangemaakt 

Allemaal selecteren > Properties > Bij Profile path: `\\WinServer1\UserProfiles\%UserName%` en bij Home folder: connect F: to `\\WinServer1\UserFolders\%UserName%`

#### Controleer of alle user accounts lid zijn van de groep domain users 

MMC AD Users and Computers > Confidas.local > Users > Domain Users dubbelklik > Members 

#### Stel voor alle user accounts in dat het paswoord nooit vervalt.  

Allemaal selecteren > Properties > Account > Password never expires

### 3. Eigen user account

#### Zorg dat u dezelfde bevoegdheden krijgt als de domain administrator 

MMC AD Users and Computers > Confidas.local > OU Automatisering > eigen naam dubbelklik > Member of > Add... > zoeken op Administrators

#### Zorg dat u met uw account een remote desktop verbinding met DC mag maken 

> By default, members of the Administrators group have this right on domain controllers, workstations, and servers. The Remote Desktops Users group also has this right on workstations and servers.

Server Manager > Local Server > Remote Desktop op Disabled klikken > "Allow remote connections to this computer"

#### Herstart DC

#### Log in op het werkstation en maak een remote desktop verbinding met DC 

Start > Verbinden met Extern Bureaublad / Connect to Remote Desktop > WinServer1 > ww invullen. 

"Your account is not allowed to use this pc." > MMC Users and Computers > OU Automatisering > eigen naam dubbelklikken > Account > Log on to... > All Computers. 

#### Maak een icoon om deze remote desktop verbinding te maken in uw taskbar.

Bureaublad rechterklik > Nieuw > Snelkoppeling > `mstsc.exe /v:192.168.1.1`

## Waar had ik problemen mee?

## Bronnen

- [Allow log on through Remote Desktop Services](https://technet.microsoft.com/en-us/library/dn221985.aspx)
- [How to enable remote desktop](https://www.rootusers.com/how-to-enable-remote-desktop-in-windows-server-2016/)
- [How to Create a "Remote Desktop Connection" Shortcut to a Specific Computer](https://www.sevenforums.com/tutorials/149790-remote-desktop-connection-shortcut-create-specific-computer.html)