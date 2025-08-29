# Automate programmable
## Préambule
- Le simulateur permet d'intégrer un automate programmable physique ou virtuel dans un folio.
- La communication avec l'API est réalisée en utilisant le protocole [Modbus Tcp-IP](modbus.md) :
    - avec l'adresse IP locale (127.0.0.1) du serveur Modbus intégré à l'API virtuel,
    - avec l'adresse IP statique du serveur Modbus intégré à l'API physique connecté sur un réseau Ethernet.
- Cette solution permet d'utiliser les outils de programmation habituels des automates.
- Logique d'échange **client (master) (simulateur) <-> serveur (slave) (api)**, périodiquement  :
    - le client Modbus  (simulateur)  émet une requête d'écriture des entrées du SAP simulé au serveur Modbus (API),
    - l'API calcule l'état des sorties du SAP selon son programme et l'état des entrées reçues,
    - le client Modbus  (simulateur) émet une requête de lecture des sorties calculées par le programme au serveur Modbus (API),
    - le simulateur met à jour l'état du SAP.

## Configuration Modbus

- **M221** Schneider Electric, codes fonctions 3,16 et 23, serveur modbus intégré
- **M340** Schneider Electric, code fonctions 3 et 16, serveur modbus intégré
- **Unilogic** Unitronics, codes fonctions 3,16 et 23, configuration du serveur Modbus requise

    ![](fr/media/unilogic.png)

  
- **CODESYS Control Win** CODESYS 3.5, codes 3,16 et 23, configuration du serveur Modbus requise
  
    ![](fr/media/codesys00.png)
    ![](fr/media/codesys0.png)
    ![](fr/media/codesys1.png)
    ![](fr/media/codesys2.png)
    ![](fr/media/codesys3.png)

    - Seuls les registres de retenue (holding registers) sont utilisés.
    - 48 registres (mot de 16 bits) sont affectés :
        - 24 registres pour les sorties, adresse de départ de la table : **adresse_QW** = 0,
        - 24 registres pour les entrées, adresse de départ de la table : **adresse_IW** = 24.
    - L'affectation des variables utilisées dans le programme est faite directement dans le mappage Modbus des E/S.
    - Le paramètre **accessible en écriture** est coché pour autoriser le serveur à écrire dans les 24 registres de sortie **%QWx.y** des modules M0 à M5.



## Face avant de l'API virtuel

![](fr/media/modbus_modules.png)

- Chaque module d'E/S intègre quatre mots d'entrée et quatre mots de sortie 16 bits.
- Ces mots peuvent-être déclinés :
    - en entrées ou sorties 'analogiques',
    - en entrées ou sorties TOR.
- Finalement, chaque module peut gérer :
    - jusqu'à 64 entrées TOR et 64 sorties TOR,
    - un mix d'E/S TOR et 'analogiques', par exemple pour le module 0 :
        - %QW0.0 -> mot de 16 bits pour une sortie 'analogique'
        - %QW0.1 -> 16 bits utilisables pour 16 sorties TOR
        - %IW0.0  -> 16 bits utilisables pour 16 entrées TOR

Les exemples qui suivent illustrent la mise en oeuvre des modules dE/S.

## Ascenseur M221

Fichiers :

- 15-demo_ascenseur_M221.xrs
- 15-demo_ascenseur_M221.smbp pour **EcoStruxure Basic Expert de SchneiderElectric**

### Préparation côté simulateur

![](fr/media/lift_example.png)

- La commande de l'ascenseur nécessite 8 entrées et 4 sorties TOR. On peut utiliser un M221 type TM221CE16R qui dispose de 9 entrées TOR et de 7 sorties à relais.
- Adressage des entrées TOR : %I0.0, %I0.1, %I0.2, %I0.3, %I0.4, %I0.5, %I0.6, %I0.7, %I0.8
- Adressage des sorties : %Q0.0, %Q0.1, %Q0.2, %Q0.3, %Q0.4, %Q0.5, %Q0.6
- L'exemple étudié implante 8 objets d'entrée et 4 objets de sortie en les identifiant avec les adresses API standards.


**Affectation des entrées**

|                      |                                              |   |
| -------------- | ------------------------------ |--|
|adresse|mnémonique|commentaire|
| %I0.0|E3|appel étage 3|
|%I0.1|E2|appel étage 2|
|%I0.2|E1|appel étage 1|
|%I0.3|P1|cabine à létage 1|   
|%I0.4|P2|cabine à létage 2|   
|%I0.5|P3|cabine à létage 3|
|%I0.6|PF|porte cabine fermée|   
|%I0.7|PO|porte cabine ouverte|

**Affectation des sorties** 

|                      |                              |   |
| -------------- | ------------------ |--|
|adresse|mnémonique|commentaire|
|%Q0.0|OUVRIR|Ouvrir porte|   
|%Q0.1|FERMER|Fermer porte|
|%Q0.2|DESCENDRE|Descendre cage|
|%Q0.3|MONTER|Monter cage|

### Préparation côté **EcoStruxure**


Le programme complet **15-demo_ascenseur_M221.smbp** est disponible dans le dossier : ![](fr/media/image89.png)


Mise en correspondance des tableaux d'entrées/sorties avec la table d'échange ajustée sur l'adresse de départ %MW400 [voir le mappage modbus](modbus.md):
  
|                      |                                    |   |   |
| -------------- | -----------------------|--|--|
|adresse| mappage MODBUS|mnémonique|commentaire|
| %I0.0  |%MW500 :X0|E3|appel étage 3|  
| %I0.1  |%MW500 :X1|E2|appel étage 2|
| %I0.2  |%MW500 :X2|E1|appel étage 1|
| %I0.3  |%MW500 :X3|P1|cabine à létage 1|
| %I0.4  |%MW500 :X4|P2|cabine à létage 2|
| %I0.5  |%MW500 :X5|P3|cabine à létage 3|
| %I0.6  |%MW500 :X6|PF|porte cabine fermée|
| %I0.7  |%MW500 :X7|PO|porte cabine ouverte|

|                      |                    |   |   |
| -------------- | ------------ |--|--|
|adresse| mappage MODBUS|mnémonique|commentaire|
|%Q0.0|%MW400 :X0|OUVRIR|Ouvrir porte|
|%Q0.1|%MW400 :X1|FERMER|Fermer porte|
|%Q0.2|%MW400 :X2|DESCENDRE|Descendre cage|
|%Q0.3|%MW401 :X3|MONTER|Monter cage|


Dans l'onglet **Programmation -\>Outils -\> Liste de symboles**, on trouve l'assignation des entrées/sorties qui correspond aux tableaux précédents:
![](fr/media/lift_symbol_list.png)

**Programme API**:
![](fr/media/lift_sfc.png)
![](fr/media/image95.png)
![](fr/media/image96.png)


Démarrer le contrôleur **AVANT** de lancer le simulateur en activant les boutons **Lancer le simulateur** et **Démarrer le contrôleur** dans l'onglet Mise en service d'EcoStruxure:

![](fr/media/image98.png)


## E-S analogiques CODESYS

Fichiers :

- 41 - demo_E-S_analogiques_CODESYS.smbp
- 41 - demo_E-S_analogiques_CODESYS.project pour **CODESYS 3.5**

[Utiliser CODESYS avec le simulateur](assets/CODESYS_LAUNCH.mp4)

### Préparation côté simulateur

- Le schéma met en oeuvre : 
    - trois entrées analogiques :
        - %IW1.0 connectée au capteur 4-20 mA B2
        - %IW1.1 connectée au capteur 4-20 mA B1 
        - %IW1.2 connectée au capteur 0-10 V AU1
    - deux sorties analogiques :
        - %QW2.0, sortie courant 0-20 mA
        - %QW2.1, sortie tension 0-10 v

- Le grapheur [Grapheur](grapher.md) est paramétré pour visualiser l'évolution de la sortie %QW2.0
    - Vqw2_0.value.5
        - Vqw2_0 -> nom du voltmètre
        - value -> affichage de la valeur mesurée
        - 5 -> calibre du voltmètre (250 * 20e-3)

![](fr/media/saw.png)

- Le programme implanté dans le contrôleur permet d'ajuster la période de la dent de scie avec le potentiomère
du capteur AU1 connecté sur %IW1.2.

![](fr/media/es_codesys.png)

### Préparation côté **CODESYS**

- L'affectation des variables est faite directement dans le mapping modbus des E/S  [configuration Modbus](plc.md) 
    - %IW1.0 -> IW1_0
    - %IW1.1 -> IW1_1
    - %IW1.2 -> IW1_2

- Code ST avec l'ensemble des registres d'E/S pour visualisation
![](fr/media/es_source_codesys.png)

- CODESSYS en exécution
    - F11 (créer code)
    - Alt-F8 (se connecter)  il faut que le contrôleur  CODESYS Control Win Systray soit en marche 
    - F5 (démarrer)

![](fr/media/es_exec_codesys.png)




## Tri de pièces CODESYS

Fichiers :

- 42 - demo_Tri_De_Caisses_CODESYS.smbp
- 42 - demo_Tri_De_Caisses_CODESYS.project pour **CODESYS 3.5**

[Utiliser CODESYS avec le simulateur](assets/CODESYS_LAUNCH.mp4)

### Préparation côté simulateur
![](fr/media/tri_codesys.png)

### Préparation côté **CODESYS**

- L'affectation des variables est faite directement dans le mapping modbus des E/S  [configuration Modbus](plc.md) 
![](fr/media/tri_affec0_codesys.png)
![](fr/media/tri_affec1_codesys.png)

- Préparation du SFC
![](fr/media/tri_source0_codesys.png)

- Code ST avec l'ensemble des registres d'E/S pour visualisation
![](fr/media/tri_source1_codesys.png)

- CODESSYS en exécution
![](fr/media/tri_exec0_codesy.png)
![](fr/media/tri_exec_codesys.png)






## Construction d'un objet API

- Un automate est construit avec les objets élémentaires :
    - input# pour les entrées TOR,
    - output# pour les sorties TOR,
    - analog_input# pour les entrées analogiques,
    - analog_output# pour les sorties analogiques,
    - plc_supply# pour l'alimentation de l'API

- Toutes les E/S ont pour parent l'objet plc_supply afin d'asservir l'alimentation de ces E/S à l'alimentation de l'automate.
- Le serveur MODBUS est implicitement attaché à l'automate en place dans le schéma.
- On ne peut placer qu'un seul automate dans le schéma.
- Des exemples d'automates sont disponibles dans le dossier [blocs_simulables](library.md) à partir de la commande 'Ouvrir un bloc' de WinRelais.

![](fr/media/image104.png)
Toutes ces empreintes d'automate sont ajustables et modifiables selon les besoins.

## Entrées/Sorties logiques
|input, output|bibliothèque _api|
| -----------------| -----------------------|
|%Ir.v ou %Qr.v|r = [0,5] v = [0,31] |
|parent =         | nom de l'objet **plc_supply#**|

![](fr/media/io_tor.png)

## Entrées analogiques
|analog_input|bibliothèque _api|
| ---------------| ----------------------------------------------------------|
|%IWr.v           |r = [0,5] v = [0,3] |
|parent =         | nom de l'objet **plc_supply#**|
|input_type =   | U  ou  I|
|input_range = |(min,max) V [-10,10] V ou (min,max) mA [0, 20] mA|
|input_scale = |min,max   [-32768, 32767]|

![](fr/media/analog_inputs.png)

## Sorties analogiques
|analog_output|bibliothèque _api|
| ---------------| ---------------------------------------------------------|
|%QWr.v           |r = [0,5] v = [0,3]|
|parent =         |   nom de l'objet **plc_supply#**|
|output_type =   | U  ou  I|
|output_range = |(min,max) V [-10,10] V ou (min,max) mA [0, 20] mA|
|output_scale = |min,max [-32768, 32767]|

![](fr/media/analog_outputs.png)
