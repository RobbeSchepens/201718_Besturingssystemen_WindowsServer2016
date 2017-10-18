# Oefening 2: ADDS Installatie

## Korte omschrijving

Bij deze oefening installeren we Active Directory Domain Services in onze Windows Server 2016. Hierbij doen we de nodige basisconfiguratie.

## Stappenplan

1. Opzetten DC - ADDS installatie starten
2. Opzetten DC - Forest instellingen correct kiezen
3. Domain Controller - Juist instellen en verkennen na ADDS met DC te installeren
4. WinServer2 als Standalone Server - Opzetten van tweede Windows Server installatie
5. WinServer2 als Member Server 

## Procedure per stap

### 1. Opzetten DC - ADDS installatie starten

Na het IPv4 juist in te stellen zoals in oefening 1, kunnen we beginnen met de Active Directory Domain Services op te zetten. We kiezen voor "Add roles and features" in het Server Manager Dashboard.

We doorlopen de installatie met default opties en drukken next zoals beschreven in de Windows Server Manual. Bij het selecteren van Server Roles, duiden we Active Directory Domain Services aan en klikken we op Add Features.

Daarna gaan we verder met default opties tot we het eerste deel al installeren en de installatie voltooid. 

### 2. Opzetten DC - Forest instellingen correct kiezen

Als de installatie gedaan is, klikken we op "Promote this server to a Domain Controller". Add a new forest selecteren en kies voor de naam "Confidas.local" zoals beschreven in de opgave van de opdracht (niet de manual). Next.

Forest en Domain Functional Level stellen we beiden in op Windows Server 2016. De DNS server optie vinken we aan en als DSRM wachtwoord stellen we weer Admin2017 in. Geen DNS delegation.

NETBIOS Domain Name is "POLIFORMA". De paden laten we op de default opties: C:\Windows\NTDS, C:\Windows\NTDS en C:\Windows\SYSVOL. Kijk de opties na en laat de installatie eindigen. De server zal automatisch herstarten.

### 3. Domain Controller - Juist instellen en verkennen na ADDS met DC te installeren (per opdrachtinstructie)

#### Welke server rollen zijn er geïnstalleerd op server WinServer1

Naast de standaard services (server roles) in een full Windows Server 2016 installation, hebben we ook Active Directory Domain Services, DNS server, File Server en Storage Services geinstalleerd. Dit zien we als we Add Features and Roles klikken en kijken welke al als geinstalleerd gemarkeerd staan. 

#### Bekijk de MMC “Active Directory Users and computers” inhoud van de container computers

"There are no items to show in this view"

#### Bekijk de MMC “Active Directory and computers” inhoud van de OU Domain controllers

Enkel de huidige computer "WIN50VTQ..." (later hernoemt naar WinServer1)

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

Server Manager > Local Server > klikken op het IP adres van LAN. 

Right click de LAN adapter > IPv4 > Properties > daarin zien we dat de Preferred DNS server het IP adres 127.0.0.1 is en dat klopt, aangezien de DNS server op dit systeem draait. 

#### Controleer of voor de NIC INTERNET CONNECTIE het IP adres van de DNS server is ingevuld van de school

Zelfde stappen als vorige vraag maar voor Internet adapter > Obtain DNS server address automatically. Je kan ook manueel in vullen. Je vindt ze in Mac: Netwerkvoorkeuren > Geavanceerd > DNS > 193.190.173.1 en 193.190.173.1. 

### [Extra] Nog een Domain Controller instellen

Als we een tweede DC nodig hebben kan dit via de manual pagina 147. Onder AD Sites and Services > Sites > PFGent > NTDS Settings right click > Replicate Now... 

### 3. WinServer2 als Standalone Server - Opzetten van tweede Windows Server installatie

Maak een nieuwe Virtuele Machine voor Windows Server 2016 met als naam WinServer2. Kies 2048 GB RAM, nieuwe virtuele HDD van 70GB. Optische schijf van iso van Windows Server 2016 toevoegen en launchen. Dutch (Belgium), Belgian Comma. Windows Server 2016 Standard (Desktop Experience). Voeg host-only netwerk adapter toe, verwijder NAT.

#### Instellingen binnenin WinServer2

Install Guest Additions DVD.

Network Adapter Options... right click op 1 van de 2 > Properties > IPv4 > Properties > Static IP settings: IP adres 192.168.1.2 en subnet 255.255.255.0 instellen. Rename "LAN CONNECTIE".

Server Manager > Local Server click op server naam > Change... "WinServer2" en werkgroep "WINWERKGROEP".

### 5. WinServer2 als Member Server 

De vorige stappen had ik al gedaan om de server om te vormen naar Domain Controller. Om er normaal een member van te maken: Verkenner > This PC > Properties > Change Settings van computer name. Daar kun je dan de juiste workgroup en domain instellen enz. 

Hiervoor moet: 
* Het IPV4 van Server 1 op 192.168.1.1 / 255.255.255.0 staan. Zijn DNS server op 127.0.0.1.
* Het IPV4 van Server 2 op 192.168.1.2 / 255.255.255.0 staan. Zijn DNS server op 192.168.1.1.
* Beiden servers moeten een Host-Only adapter hebben. 
* Server 1 aanstaan.

.\Administrator om als lokale administrator aan te melden.

#### Installeer op WinServer2 de server role ADDS en DNS.

Server Manager > Add Roles and Features > ADDS en DNS toevoegen. 

#### Promote this server to a Domain Controller

Add Domain Controller to an existing domain. Domain: Confidas.local [Select...] vul de credentials in: Confidas.local\Administrator met als ww Admin2017 zodat hij toegang heeft tot het domain Confidas. 

DNS server en Global Catalog aangevinkt. Site naam zou op PFGent moeten staan. Als DSRM ww geven we Admin2017. (Tot hierver de opdracht instructies 1.2)

Update Delegations laten we afgevinkt. Replicate from > WinServer1.Confidas.local. Mappen laten we standaard staan. Install. 

#### Welke server roles zijn er op member server WinServer2 geïnstalleerd

Geen. (Enkel de standaard File and Storage Services)

#### Komen er op WinServer2 nog machine local users en groups voor. Zo ja 

Enkel Administrator. (Default account en Guest zijn locked)

#### Open op WinServer1 de MMC ADUC en haal het tabblad members van de domain group “domain admins” voor u en bekijk wie er lid is van deze groep

Enkel Administrator. 

#### Open op WinServer2 het eigenschappenvenster van de machine local group Administrators. Wie is er lid van deze groep

Administrator, POLIFORMA\Domain Admins

#### Zijn er op de member server WinServer2 in het menu tools van de server manager opties opgenomen voor het beheer van de AD

Nee, geen enkele. 

#### In welke container zit het computer account WinServer2 in de AD op WinServer1

De container Computers.

#### Tabel

|                                     | Standalone Server | Member Server | Domain Controller |
| ----------------------------------- |:-----------------:|:-------------:|:-----------------:|
| Bevat de map C:\Windows\NTDS        |   |   | X |
| Bevat de map c:\windows\Sysvol      |   |   | X |
| Bevat Machine Local users en groups | X | X |   |
| Bevat Domain Groups                 |   |   | X |
| Bevat Tools om de AD te beheren     |   |   | X |

## Waar had ik problemen mee?

* Ik kon Windows Server 2016 niet selecteren als Domein Functional Level en Forest Functional Level.

Ik heb alle updates geinstalleerd en de installatie dan pas verder gezet. Daarna staat 2016 wel in het dropdownmenu. Zie [Support Microsoft - Shows Technical Preview](https://support.microsoft.com/nl-be/help/3202325/domain-controller-promotion-process-shows-windows-server-technical-pre).

* Ik heb geen tweede product key voor de tweede server op te zetten. 

## Extra bronnen

- [Wikipedia - Domain Controller](https://en.wikipedia.org/wiki/Domain_controller)

- Windows Server 2016 manual

- [Technet GCS uitzoeken](https://technet.microsoft.com/nl-be/library/cc794880(v=ws.10).aspx)

- [Join domain as member](https://msdn.microsoft.com/en-us/library/ms942519%28v=cs.70%29.aspx?f=255&MSPPError=-2147217396)

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