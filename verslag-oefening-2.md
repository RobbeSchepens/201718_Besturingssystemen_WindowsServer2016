# Oefening 2: ADDS Installatie

## Korte omschrijving

Bij deze oefening installeren we Active Directory Domain Services in onze Windows Server 2016. Hierbij doen we de nodige basisconfiguratie, zoals de configuratie van 

## Stappenplan

1. ADDS installatie starten
2. 

## Procedure per stap

Noteer hier wat voor u belangrijk is om bij te houden van alles wat u hebt moeten uitvoeren om tot een goed resultaat te komen. Zorg ervoor dat u nadien snel weet hoe u de zaken had aangepakt zodat u het snel opnieuw zou kunnen reproduceren. Zorg eventueel voor voldoende **screenshots** die de procedure verduidelijken.

(voorbeeld)

### VirtualBox downloaden en installeren.

VirtualBox downloaden we van [VirtualBox.org](https://www.virtualbox.org/). We volgen de installatiewizard om de installatie te voltooien.

![VirtualBox](images/virtualbox.png)

### ISO Windows Server 2016 downloaden en een key opvragen.

We downloaden de ISO van [imagine.microsoft.com](https://imagine.microsoft.com/) en krijgen hierbij ook een installatie key.

...


## Gebruikte commando's (optioneel)

(voorbeeld)

Commando om de PowerShell help op te roepen:

```
PS C:\Users\Administrator> Get-Help
```

## Waar had ik problemen mee?

(voorbeeld)

* Ik kon Windows 2016 niet selecteren bij de aanmaak van mijn VM in VirtualBox.

Ik moest mijn toestel opstarten in de BIOS en bij de systeemconfiguratie de instelling "Virtual Technology" activeren.

* Voor mijn VM kon ik geen netwerkkaart activeren van het type "Host-only".

Bij de instellingen van VirtualBox, tabblad "Netwerk", moest ik eerst een "Host-only" netwerk aanmaken.

## Extra bronnen (optioneel)

- [Wikipedia - Domain Controller](https://en.wikipedia.org/wiki/Domain_controller)

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