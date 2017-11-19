# Oefening 8: Aanmaken OUs en gebruikers

## Korte omschrijving

Bij deze oefening maken we OUs aan en gebruikers in de huidige omgeving. 

## Stappenplan

1. OU CAfdelingen aanmaken
2. Aanmaken gebruikers in OU
3. Eigen user account

## Procedure per stap

### 1. OU CAfdelingen aanmaken

MMC Active Directory Users and Computers > Confidas.local rechterklik > New > Organizational Unit (of via icoontje)

"PROTECT CONTAINER FROM ACCIDENTAL DELETION" telkens uitvinken. 

- OU Directie 
- OU Staf 
- OU verkoop 
- OU Administratie 
- OU Productie  
    - OU FabricageAalst 
- OU automatisering 

### 2. Aanmaken gebruikers in OU

Via icoontje "New user in current container" in de Users and Computers MMC. 

Zie opdracht. 

In WinClient1 aanmelden als POLIFORMA\mad_sme. 

#### Maak voor Madelief Smets een quata beperking aan op volme PFSV1Data (F:). 100 MB met waarschuwing op 90 MB 

WinServer1 > Verkenner > WinServ1Data F: rechterklik > Properties > Quota > Quota entries... > Quota New Entry > Advanced > "mad" Find Now > selecteer Madelief Smets > OK > Limits setten > OK. 

#### Stel voor User Account Madelief Smets volgende eigenschappen in 

MMC AD Users and Computers > OU Directie > Madelief Smets rechterklik > Properties

#### Log in als Madelief Smets en kijk of de mapping naar de homefolder er staat 

// No clue

#### Controleer op DC PFSV1 of de folder Madelief Smets staat in de Profielmap 

// Niets gevonden

### 3. Eigen user account

#### Controleer of voor elke gebruiker een homefolder is aangemaakt 



#### Controleer of alle user accounts lid zijn van de groep domain users 



#### Stel voor alle user accounts in dat het paswoord nooit vervalt.  



## Waar had ik problemen mee?

- "Log in als Madelief Smets en kijk of de mapping naar de homefolder er staat" lukt niet

No fix

## Extra bronnen (optioneel)

- 