# Oefening 4: Dynamic Host Configuration Protocol

## Korte omschrijving

Bij deze oefening installeren we de rol DHCP. Hierbij doen we de nodige basisconfiguratie. We gaan in deze opdracht een DHCP server maken van onze WinServer1. We gaan voor ons netwerk een scoop instellen van DHCP adressen.

## Stappenplan

1. Rol DHCP installeren
2. Scoop toevoegen
3. Bekijken van de eigenschappen en instellingen van DHCP
4. Configureren van DHCP zodat hij gebruikt kan worden binnen het LAN Netwerk
5. Maken we DHCP actief binnen het domein

## Procedure per stap

### 1. Rol DHCP installeren

Add Roles and Features > DHCP > Next > Next > Next > ... 

Complete DHCP configuration > Skip AD credentials > Commit > Close

### 2. Scope toevoegen

DHCP MMC > DHCP > winserver1.confidas.local > IPv4 rechterklikken > New Scope... 

- Naam: PFScopeGent
- Range IPv4 adressen: 192.168.1.31 tot en met 192.168.1.130 
- Subnetmasker: 255.255.255.0
- Sluit de range 192.168.1.81 tot en met 192.168.1.130 uit
- Lease duur is 6 dagen
- Configureer ook DHCP options met
    - IPv4 adres van de router 192.168.1.1 
    - Domain: confidas.local
    - IPv4 adres van de DNS: 192.168.1.1 
    - GEEN WINS
- Activeer de aangemaakte scope nog niet

### 3. Bekijken van de eigenschappen en instellingen van DHCP

#### Bekijk de container address pool

Bevat 2 ranges van adressen. Eén met de volledige range, de andere met alle excluded adressen.

#### Bekijk de container address leases

Hierin zien we de clients die adressen huren en hoe lang ze dit kunnen doen. 

#### Bekijk het onderdeel Reservatie. Je gaat voor uw eerste Windows Client een reservatie maken binnen DHCP

Hierin zien we de reservaties. Later zullen we één toevoegen. 

#### Controleer of DHCP op het LAN gedeelte de scope Options 003,006 en 015 doorgeeft

- 003 Routers
- 006 DNS Servers
- 015 DNS Domain Name

Scope Options zijn typisch voor LAN: zoals gateway definieren.

Server Options zijn typisch voor grotere zaken zoals DNS.

### 4. Configureren van DHCP zodat hij gebruikt kan worden binnen het LAN Netwerk

#### Regel de samenwerking tussen DHCP en DDNS
- Stel dynamisch updaten in geïnitieerd door de DHCP cliënt
- Laat A en PTR records verwijderen als de lease duur verstreken is

Dynamisch updaten vind je onder DNS MMC > Confidas.local rechterklik > Properties > General > Dynamic updates: Secure only

DHCP > winserver1.confidas.local > IPv4 > Scope [192.168.1.0] PFScopeGent rechterklik > DNS > "Discard A and PTR records when lease is deleted" aanvinken

#### Autoriseer de DHCP Scope

Was al geautoriseerd bij installatie. 

#### Activeer de DHCP scope

DHCP > winserver1.confidas.local > IPv4 > Scope [] PFScopeGent rechterklik > Activate

#### Configureer later uw Windows cliënt als DHCP cliënt



#### Bekijk de IPv4 configuratie van de Windows Cliënt



### 5. Maken we DHCP actief binnen het domein

#### Test de Internetverbinding van WinServer2



#### Maak in DNS het PTR record aan voor WinServer2



## Waar had ik problemen mee?

- Geen

## Extra bronnen

- Windows Server 2016 manual -> sectie "Install DHCP Server Graphically" en volgende (pdf bladzijden 91 tem. 110).