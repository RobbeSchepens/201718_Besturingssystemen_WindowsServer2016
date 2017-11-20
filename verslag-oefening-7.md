# Oefening 7: Share permissies

## Korte omschrijving

Bij deze oefening maken we nieuwe gedeelde mappen aan. We gaan voor de gebruikers netwerklocaties beschikbaar stellen. We gaan ook share permissies instellen en NTFS permissies bekijken.

## Stappenplan

1. Shares bekijken
2. Shares maken
3. Mappings

## Procedure per stap

### 1. Shares bekijken

#### Toon op DC WinServer1 de daar aanwezige shares via de MMC Computer Management

Shared Folders > Shares. ADMIN, IPC, SYSVOL, NETLOGON en dan alle volumes.

#### Toon op DC WinServer1 de daar aanwezige shares via de server manager

Server Manager > File and Storage Services > Shares. Hier staan slechts 2: NETLOGON en SYSVOL. 

#### Toon op de DC WinServer1 de daar aanwezige shares via de UNC-Notatie

NETLOGON: `admin$\SYSVOL\sysvol\Confidas.local\SCRIPTS`

SYSVOL: `admin$\SYSVOL\sysvol`

#### Toon op WinClient1 via een UNC-notatie de op DC WinServer1 aanwezige shares

- ADMIN$
- IPC$
- C$
- E$

#### Toon op WinClient1 de daar aanwezige shares via Computer Management

Start > Computerbeheer

#### Toon op WinClient1 via de MMC Computer management de op DC WinServer1 aanwezige shares

Start > "MMC" opdracht uitvoeren. Bestand > Modules toevoegen/verwijderen > Gedeelde mappen toevoegen. 

Start > "MMC". Bestand > Modules toevoegen/verwijderen > Computerbeheer > Andere computer > Geavanceerd > Zoeken op "Win" > WINSERVER1 > OK > OK. 

#### Toon op DC WinServer1 de shares op werkstation WinClient1 met behulp van commando NET.Exe

`net share` in Command Prompt. Geeft overzicht van shares. 

### 2. Shares maken

#### Deel op DC WinServer1 het volume WinServ1Data (F) door gebruik te maken van de New Share Wizard. De share naam is: WinServ 1Data. Geen wijzigingen in de toegangspermissies.

Server Manager > File and Storage > Volumes > F rechterklik > New Share... > SMB Share Quick > WinServer1 volume F: > WinServ1Data > Create. 

#### Verwijder de share WinServ1Data weer

Server Manager > File and Storage Services > Shares > WinServ1Data rechterklik > Stop Sharing

#### Maak op DC WinServer1 de map F:\UserFolders aan. Deel deze map. De Sharenaam is UserFolders met omschrijving Share voor de homefolders voor de gebruikers. Geen wijzigingen in de toegangspermissies

Verkenner > F: > New folder > UserFolders

Server Manager > File and Storage Services > Shares > Tasks > New Share... > SMB Share Quick > Type a Custom Path browse... > F: userfolders > naam en beschrijving invullen > Create.

#### Maak op DC WinServer1 de map F:\UserProfiles aan. Sharenaam is UserProfiles met omschrijving Share voor de Profile Folders van de gebruikers. Geen wijzigingen in de toegangspermissies. Controleer of de shares UserFolders en UserProfiles benaderbaar zijn vanaf werkstation PFWS1

Verkenner > F: > New folder > UserProfiles

Server Manager > File and Storage Services > Shares > Tasks > New Share... > SMB Share Quick > Type a Custom Path browse... > F: userprofiles > naam en beschrijving invullen > Create.

Controleren of ze benaderbaar zijn in WinClient1. (zie 1. Shares bekijken)

### 3. Mappings

#### Maak als Domein Admin op werkstation WinClient1 een netwerkverbinding met de share UserFolders op DC WinServer1 onder de driveletter P:. Zorg dat deze mapping na herstarten opnieuw wordt aangemaakt

Verkenner > Netwerk > WinServer1.Confidas.local > UserFolders rechterklik > Netwerkverbinding maken... > Station P: > "Opnieuw verbinden bij aanmelden" aanvinken

#### Doe dit ook voor UserProfiles onder driveletter Q. Doe dit met het commando Net.Exe

Command prompt (Run as Administrator) >  `net use q: \\WinServer1\UserProfiles` 

#### Maak ook een mapping onder de driveletter R naar de root van volume WinServ1Data (F:)

Command prompt (Run as Administrator) > `net use r: \\WinServer1\F$`

#### Controleer de mappings op WinClient1 in het venster Computer.

Verkenner > Deze PC

## Waar had ik problemen mee?

* Ik weet niet hoe je een mapping kan maken naar de root van volume WinServ1Data F: 

Blijkt dat dit kan door het dollar teken toe te voegen. 

## Extra bronnen (optioneel)

- [LifeWire UNC](https://www.lifewire.com/unc-universal-naming-convention-818230)

- [IT Pro Today Net Exe commands](http://www.itprotoday.com/management-mobility/netexe-reference)

- [MSDN: To share a folder or a drive by using a command line ](https://technet.microsoft.com/en-us/library/cc770880.aspx)

- [How to Map Network Drives From the Command Prompt in Windows](https://www.howtogeek.com/118452/how-to-map-network-drives-from-the-command-prompt-in-windows/)