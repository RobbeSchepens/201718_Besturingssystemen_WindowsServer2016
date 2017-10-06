# Oefening 1: Installatie Windows Server

## Korte omschrijving

Bij deze oefening installeren we Windows Server als virtuele machine in VirtualBox. Hierbij doen we de nodige basisconfiguratie, zoals de configuratie van de netwerkkaarten, zodat de machine meteen startklaar is.


## Stappenplan

1. VirtualBox downloaden en installeren.
2. ISO Windows Server 2016 downloaden en een key opvragen.
3. Virtuele machine aanmaken in VirtualBox.
4. Windows Server 2016 installeren in de aangemaakte VM.
5. Basisconfiguratie uitvoeren.

## Procedure per stap

### VirtualBox downloaden en installeren.

VirtualBox downloaden we van [VirtualBox.org](https://www.virtualbox.org/). We volgen de installatiewizard om de installatie te voltooien.

![VirtualBox](images/virtualbox.png)

### ISO Windows Server 2016 downloaden en een key opvragen.

We downloaden de ISO van [imagine.microsoft.com](https://imagine.microsoft.com/) en krijgen hierbij ook een installatie key.

### Windows Server 2016 installeren.

We maken een nieuwe virtuele machine aan voor Windows Server 2016.

We maken een nieuwe, dynamisch gealloceerde schijf en stellen deze in op 160GB.

In de instellingen van Opslag van onze nieuwe VM voegen we een optisch station toe. We selecteren de iso van Windows Server drukken op OK en starten de server op. 

Als wachtwoord stellen we Admin2017 in. 

### IPv4 adres instellen

Eens we ingelogd zijn in de Windows Server kunnen we de netwerkinstellingen aanpassen. Schakel één van de netwerk adapters uit in de instelling van onze VM in VirtualBox zodat we weten welke host-only is en de andere. We openen de properties van Netwerk Connecties van de host-only adapter. 

We veranderen het IP adres naar 192.168.1.1 met als subnetmask 255.255.255.0.

### Server afsluiten

We sluiten de server af en geven als reden op Other (unplanned). 

## Waar had ik problemen mee?

* Voor mijn VM kon ik geen netwerkkaart activeren van het type "Host-only".

Bij de instellingen van VirtualBox, tabblad "Netwerk", moest ik eerst een "Host-only" netwerk aanmaken.

## Statements uit pretest

- 