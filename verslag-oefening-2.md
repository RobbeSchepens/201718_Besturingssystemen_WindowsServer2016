# Oefening 2: ADDS Installatie

## Korte omschrijving

Bij deze oefening installeren we Active Directory Domain Services in onze Windows Server 2016. Hierbij doen we de nodige basisconfiguratie.

## Stappenplan

1. ADDS installatie starten
2. Forest instellingen correct kiezen
3. Als DNS server inzetten


## Procedure per stap

### ADDS installatie starten

Na het IPv4 juist in te stellen zoals in oefening 1, kunnen we beginnen met de Active Directory Domain Services op te zetten. We kiezen voor "Add roles and features" in het Server Manager Dashboard.

We doorlopen de installatie met default opties en drukken next zoals beschreven in de Windows Server Manual. Bij het selecteren van Server Roles, duiden we Active Directory Domain Services aan en klikken we op Add Features.

Daarna gaan we verder met default opties tot we het eerste deel al installeren en de installatie voltooid. 

### Forest instellingen correct kiezen

Als de installatie gedaan is, klikken we op "Promote this server to a Domain Controller". Add a new forest selecteren en kies voor de naam "Confidas.local" zoals beschreven in de opgave van de opdracht (niet de manual). Next.

Forest en Domain Functional Level stellen we beiden in op Windows Server 2016. De DNS server optie vinken we aan en als DSRM wachtwoord stellen we weer Admin2017 in.

## Gebruikte commando's (optioneel)

(voorbeeld)

Commando om de PowerShell help op te roepen:

```
PS C:\Users\Administrator> Get-Help
```

## Waar had ik problemen mee?

* Ik kon Windows Server 2016 niet selecteren als Domein Functional Level en Forest Functional Level.

Ik heb alle updates geinstalleerd en de installatie dan pas verder gezet. Daarna staat 2016 wel in het dropdownmenu. Zie [Support Microsoft - Shows Technical Preview](https://support.microsoft.com/nl-be/help/3202325/domain-controller-promotion-process-shows-windows-server-technical-pre).

## Extra bronnen (optioneel)

- [Wikipedia - Domain Controller](https://en.wikipedia.org/wiki/Domain_controller)

- Windows Server 2016 manual

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