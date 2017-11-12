# Oefening 6: Schijvenbeheer binnen het netwerk

## Korte omschrijving

Bij deze oefening maken we verschillende schijven aan op onze windows server en voeren we er bewerkingen op uit. 

## Stappenplan

1. Schijfvolumes aanmaken
2. Bewerkingen uitvoeren op de aangemaakte schijven
3. Quota
4. Volumes instellen op een windows client

## Procedure per stap

### 1. Schijfvolumes aanmaken

Maak alle schijfvolumes aan zoals in de opdracht. Server Manager > File and Storage services > Volumes > Disks rechterklik achtergrond > New volume... 

- E: 20GB WinServ1Appl
- F: 10GB WinServ1Data
- G: 20GB WinServ1Dist
- H: 5GB WinServ1Spec
- I: 5GB WinServ1Test

### 2. Bewerkingen uitvoeren op de aangemaakte schijven

Rechterklik Start > Disk Management

- Converteer volume WinServ1Test (I) van FAT32 naar NTFS
- Schakel automatische compressie in

rightclick Format... naam veranderen naar WINSERV1TES en naar FAT32. Compressie kon niet worden aangeduid bij FAT32. 

- Schakel ook voor WinServ1Dist (G) automatische compressie in

rightclick Properties > Compress this drive to save space

- Stel voor de schijf C de volume naam in op WinServ1Syst

rightclick Properties > Name

- Verander van het volume WinServ1Test (I) de drive letter naar K

rightclick Change Drive Letter and Paths

### 3. Quota

- Stel op volume WinServ1Data (F) diskquota in met volgende Specificaties
    - Max schijfruimte / gebruiker: 100 MB
    - Waarschuwingslevel: 90 MB
    - Een gebeurtenis schrijven als de max ruimte bereikt is, een gebeurtenis schrijven als het waarschuwingsniveau bereikt is.

rightclick Properties > Quota > Enable Quota Management

### 4. Volumes instellen op een windows client

Zorg dat u zowel op WinServer1 als op het WinClient1 bent ingelogd met domain admin account. Maak op WinClient1 op Disk 0 een volume aan met volgende eigenschappen
- Volume grootte: 20 GB
- Drive letter: E
- Bestandssysteem: NTFS
- Clusergrootte: Default
- Volumelabel: WinClient1Data
- Volledig formatterenen Compressie inschakelen

## Waar had ik problemen mee?

- Geen

## Extra bronnen (optioneel)

- 