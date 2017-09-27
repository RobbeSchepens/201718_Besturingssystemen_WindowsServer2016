# Oefening ?: Titel

## Korte omschrijving

(voorbeeld)

Bij deze oefening installeren we Windows Server als virtuele machine in VirtualBox. Hierbij doen we de nodige basisconfiguratie, zoals de configuratie van de netwerkkaarten, zodat de machine meteen startklaar is.


## Stappenplan

(voorbeeld)

1. VirtualBox downloaden en installeren.
2. ISO Windows Server 2016 downloaden en een key opvragen.
3. Virtuele machine aanmaken in VirtualBox.
4. Windows Server 2016 installeren in de aangemaakte VM.
5. Basisconfiguratie uitvoeren.

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

...