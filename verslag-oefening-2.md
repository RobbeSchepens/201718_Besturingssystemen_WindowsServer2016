# Oefening 2: ADDS Installatie

## Korte omschrijving

Bij deze oefening installeren we Active Directory Domain Services in onze Windows Server 2016. Hierbij doen we de nodige basisconfiguratie.

## Stappenplan

1. Opzetten DC - ADDS installatie starten
2. Opzetten DC - Forest instellingen correct kiezen
3. Domain Controller - Juist instellen en verkennen na ADDS met DC te installeren
4. WinServer2 als Standalone Server - Opzetten van tweede Windows Server installatie

## Procedure per stap

### 1. Opzetten DC - ADDS installatie starten

Na het IPv4 juist in te stellen zoals in oefening 1, kunnen we beginnen met de Active Directory Domain Services op te zetten. We kiezen voor "Add roles and features" in het Server Manager Dashboard.

We doorlopen de installatie met default opties en drukken next zoals beschreven in de Windows Server Manual. Bij het selecteren van Server Roles, duiden we Active Directory Domain Services aan en klikken we op Add Features.

Daarna gaan we verder met default opties tot we het eerste deel al installeren en de installatie voltooid. 

### Opzetten DC - Forest instellingen correct kiezen

Als de installatie gedaan is, klikken we op "Promote this server to a Domain Controller". Add a new forest selecteren en kies voor de naam "Confidas.local" zoals beschreven in de opgave van de opdracht (niet de manual). Next.

Forest en Domain Functional Level stellen we beiden in op Windows Server 2016. De DNS server optie vinken we aan en als DSRM wachtwoord stellen we weer Admin2017 in. Geen DNS delegation.

NETBIOS Domain Name is "POLIFORMA". De paden laten we op de default opties: C:\Windows\NTDS, C:\Windows\NTDS en C:\Windows\SYSVOL. Kijk de opties na en laat de installatie eindigen. De server zal automatisch herstarten.

### Domain Controller - Juist instellen en verkennen na ADDS met DC te installeren (per opdrachtinstructie)

#### Welke server rollen zijn er geïnstalleerd op server WinServer1

Naast de standaard services (server roles) in een full Windows Server 2016 installation, hebben we ook Active Directory Domain Services, DNS server, File Server en Storage Services geinstalleerd. Dit zien we als we Add Features and Roles klikken en kijken welke al als geinstalleerd gemarkeerd staan. 

#### Bekijk de MMC “Active Directory Users and computers” inhoud van de container computers

"There are no items to show in this view"

#### Bekijk de MMC “Active Directory and computers” inhoud van de OU Domain controllers

Enkel de huidige computer "WIN50VTQ..."

#### Bekijk de in AD aanwezige gebruikers en groepen. Bekijk de eigenschappenvensters van de domain users administrator en Guest. Stel voor de domain administrator in dat “Password never expires”.

In de Server Manager, klik op Tools > Active Directory Users and Computers. Confidas.local > Users > Administrator dubbelklikken. Tab "Account" onder Account options "Password never expires" aanduiden.

#### Vul de description van DC WinServer1 met: DC in het domein confidas.local

In de Server Manager, klik Local Server, dan op de server naam en als computer description vullen we in "DC in het domein confidas.local". We klikken ook op Change... om de servernaam te veranderen naar "WinServer1" als hier iets anders ingesteld is en herstarten de server. 

#### Controleer of DC WinServer1 een GCS is (Global Catalog Server)

Administrative Tools > Active Directory Sites and Services > Sites. Vouw de eerste en enige uit > WinServer1 > NTDS Settings right click > Properties. In het General tab moet Global Catalog aangevinkt staan.

#### Bekijk van welke groepen DC WinServer1 lid is

Tools > Active Directory Administrative Center > Confidas (local) > Winserver 1 right click > Properties. Onder Member Of zien we dat de DC hoort tot de groep "Domain Controller" onder het mapje "Confidas-Users-Domain Controllers".

#### Voor volgende hebben we 3 verschillende tools nodig: Active Directory Administration Center, de MMC ADUC (Active Directory Users and Computers) en de MMC Active Directory Sites and Services. Wijzig de sitenaam in PFGent.

Right click op "Default first site name" onder Sites and Services > Sites en klik Rename. Verander naar PFGent.

#### Vul voor de site PFGent het tekstvak description in met Vestiging van Confidas

Right click PFGent > Properties. Vul als description in "Vestiging van Confidas". 

#### Vul voor de site PFGent de location Gent in

In hetzelfde venster als het wijzigen van de description, klikken op het tabblad Location en "Gent" invullen.

#### Bekijk welk IP adres voor de NIC LAN CONNECTIE is ingevuld bij de preferred DNS Server

VRAGEN IN DE LES.

#### Controleer of voor de NIC INTERNET CONNECTIE het IP adres van de DNS server is ingevuld van de school

### [Extra] Nog een Domain Controller instellen

Als we een tweede DC nodig hebben kan dit via de manual pagina 147. Onder AD Sites and Services > Sites > PFGent > NTDS Settings right click > Replicate Now...

### WinServer2 als Standalone Server - Opzetten van tweede Windows Server installatie

Maak een nieuwe Virtuele Machine voor Windows Server 2016 met als naam WinServer2. Kies 2048 GB RAM, nieuwe virtuele HDD van 70GB. Optische schijf van iso van Windows Server 2016 toevoegen en launchen. Dutch (Belgium), Belgian Comma. Windows Server 2016 Standard (Desktop Experience). Voeg host-only netwerk adapter toe.

#### Instellingen binnenin WinServer2

Install Guest Additions DVD.

Network Adapter Options... right click op 1 van de 2 > Properties > IPv4 > Properties > Static IP settings: IP adres 192.168.1.2 en subnet 255.255.255.0 instellen. 

Server Manager > Local Server click op server naam > Change... "WinServer2" en werkgroep "WINWERKGROEP".

## Waar had ik problemen mee?

* Ik kon Windows Server 2016 niet selecteren als Domein Functional Level en Forest Functional Level.

Ik heb alle updates geinstalleerd en de installatie dan pas verder gezet. Daarna staat 2016 wel in het dropdownmenu. Zie [Support Microsoft - Shows Technical Preview](https://support.microsoft.com/nl-be/help/3202325/domain-controller-promotion-process-shows-windows-server-technical-pre).

* Ik heb geen tweede product key voor de tweede server op te zetten. 

## Extra bronnen (optioneel)

- [Wikipedia - Domain Controller](https://en.wikipedia.org/wiki/Domain_controller)

- Windows Server 2016 manual

- [Technet GCS uitzoeken](https://technet.microsoft.com/nl-be/library/cc794880(v=ws.10).aspx)

## Statements uit pretest

- Een server role bestaat uit role services en die kunnen ook bestaan uit features. 

- Een domein maakt deel uit van een forest

- Om van een standalone server een Domain Controller te maken in een bestaand domein, moet je eert het IP adres van de DNS server instellen, dan de ADDS installeren en daarna de AD. 

- Windows Server is geinstalleerd op C. Dan is C/Windows/NTDS een server van het type Domain Controller. 

- AD heeft de service DNS nodig.

- Na een clean install van Windows Server, is de PC een standalone server.

- Onder Windows Server maken we verschillende domains als gescheiden autonoom beheer nodig hebben. 

- Als je de AD van de laatste DC verwijdert, dan houdt het domein op met bestaan.

- Als het FFL op 2012 draait en het DFL op 2016, dan is de minimum versie in dat domein 2016, in heel de Forest is het 2012.

- zie ook afbeelding pretest (hoeveel trees en domeinen zijn er?)