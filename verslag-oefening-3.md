# Oefening 3: Domain Name Server

## Korte omschrijving

Bij deze oefening configureren we de DNS server op WinServer1. Hierbij doen we de nodige basisconfiguratie, zoals de configuratie van de A-records en toevoeging van Remote Access.

## Stappenplan

1. VirtualBox downloaden en installeren.
2. ISO Windows Server 2016 downloaden en een key opvragen.
3. Virtuele machine aanmaken in VirtualBox.
4. Windows Server 2016 installeren in de aangemaakte VM.
5. Basisconfiguratie uitvoeren.

## Procedure per stap

Voorvertoning klas

DHCP role toevoegen. Next Next Next...



Lokaal administrator wordt naar domain administrator gemaakt. 



DNS server

DNS tool 

WinServer1 rechterklik > New Zone... met ip 192.168.1, daarna

WinServer1 rechterklik > All Tasks > Reload



Group Policy Management > Forest > Domain > Confidas.local > Group Policy Objects > Default Domain Policies rechterklik > Edit...



DNS tool > WinServer1 rechterklik > Properties > Monitoring > Test now (beiden aanvinken)
Properties > Forwarders (moeten servers van hogent of thuis van provider staan)



Noteer hier wat voor u belangrijk is om bij te houden van alles wat u hebt moeten uitvoeren om tot een goed resultaat te komen. Zorg ervoor dat u nadien snel weet hoe u de zaken had aangepakt zodat u het snel opnieuw zou kunnen reproduceren. Zorg eventueel voor voldoende **screenshots** die de procedure verduidelijken.

(voorbeeld)

### VirtualBox downloaden en installeren.

VirtualBox downloaden we van [VirtualBox.org](https://www.virtualbox.org/). We volgen de installatiewizard om de installatie te voltooien.

![VirtualBox](images/virtualbox.png)

### ISO Windows Server 2016 downloaden en een key opvragen.

We downloaden de ISO van [imagine.microsoft.com](https://imagine.microsoft.com/) en krijgen hierbij ook een installatie key.

...

## Waar had ik problemen mee?

* Ik

Ik

## Extra bronnen

* Windows Server 2016 manual -> hoofdstuk "Configure DNS Server Fully Step by Step" (pdf bladzijden 116 tem. 135).

