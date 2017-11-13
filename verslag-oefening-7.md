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

?

#### Toon op DC WinServer1 de shares op werkstation WinClient1 met behulp van commando NET.Exe

`net share` in Command Prompt. Geeft overzicht van shares. 

### 2. Shares maken
### 3. Mappings

## Waar had ik problemen mee?

* Geen 

## Extra bronnen (optioneel)

- [LifeWire UNC](https://www.lifewire.com/unc-universal-naming-convention-818230)