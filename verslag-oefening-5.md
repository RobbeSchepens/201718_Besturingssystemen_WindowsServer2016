# Oefening 5: Installatie van een windows client

## Korte omschrijving

Bij deze oefening installeren we een Windows Client als virtuele machine in VirtualBox. Hierbij doen we de nodige basisconfiguratie, zoals de configuratie van de netwerkkaarten, zodat de machine meteen startklaar is. En maken we het lid van ons domain Confidas.local. 

## Stappenplan

1. Virtualbox instellingen
2. Windows installatie instellingen
3. Lid maken van Confidas.local

## Procedure per stap

### 1. Virtualbox instellingen

Maak een nieuwe machine aan "WinClient1" met een nieuwe dynamisch gealloceerde schijf van 160GB. Voeg de netwerk adapter toe "intern netwerk". 

### 2. Windows installatie instellingen

Naam van de machine binnen Virtual Box: WinCLient1
- Taal software: Engels of Nederlands
- Tijd en Valuta: Dutch Belgian
- Toetsenbord: Belgium period
- Product code
- Installeer op een primaire partitie van 70 GB
- Werk de installatie af met volgende instellingen
    - Computernaam: WinCLient1
    - Kies voor USE EXPRESS SETTINGS
    - Klik linksonder op de link Sign In Without a Microsoft Account o USER: PCGebruiker1
    - Paswoord: 1PCGebruiker en als hint NAAM
- Bekijk de IPv4 settings
    - IP: 192.168.1.80
    - Subnet: 255.255.255.0
    - Default gateway: 192.168.1.1
    - DNS server: 192.168.1.1
- Creeer binnen DHCP een reservatie voor dit werkstation met
    - IP 192.168.1.80
    - SN 255.255.255.0

### 3. Lid maken van Confidas.local

Start Server1 en Client1 op. In de server: ga naar DHCP MMC tool en maak een IPV4 reservatie aan voor het IP 192.168.1.80, MAC adress 080027621434 (dit is te vinden door ipconfig /all command uit te voeren in de winclient1). 

In de Client rightclick Start > Computer > Verbinden met werk of school > Toevoegen > Toevoegen aan local Active Directory domain > "Confidas.local" > Credentials invoegen (POLIFORMA\Administrator en Admin2017) > Account toevoegen: POLIFORMA\Administrator Administrator type. 

Log nadien in op WinClient1 als domain administrator.

#### Wat zijn de gevolgen voor WinClient1?

Enkele instellingen werden teruggezet. Je logt nu in met het administrator account van het domein ipv de computer zelf. 

#### Waar is WinClient1 opgeslagen in AD?

Onder Computers. Te zien in AD Users and Computers MMC. 

#### Wat staat er in de DNS op WinServer1?

De Desktop workstation staat ook als een Host (A) vermeldt. 

#### Wat staat er in de DHCP op WinServer1?

WinClient1 met IP 192.168.1.80 werd een reservatie toegekend. 

#### Gevolgen voor WinClient1. Bekijk de machine local users en de machine local groups

De WinClient1 heeft nog een DefaultAccount dat wordt beheerd door het systeem, daarnaast zijn Administrator en GastAccount uit het domein overgenomen. 

## Waar had ik problemen mee?

- Geen

## Extra bronnen (optioneel)

- [Imagine Download Windows 10 Multiple Versions (Win 10 Pro)](https://e5.onthehub.com/WebStore/OfferingDetails.aspx?o=dafc87c7-1d1a-e711-9427-b8ca3a5db7a1&pmv=769faff4-d124-e511-940e-b8ca3a5db7a1&ws=9382cda9-c42d-e211-aed3-f04da23e67f6&vsro=8)