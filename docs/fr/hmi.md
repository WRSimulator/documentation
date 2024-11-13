# Interface Homme Machine

![](fr/media/hmi1.png)

- Les composants ihm sont modifiables dans WinSymbole.
- On peut créer des variantes de composants ihm en ajoutant le suffixe **#ma_variante** après la racine du composant. Exemple :
![](fr/media/hmi2.png)


## Voyant
|voyant|bibliothèque /_ihm|
| -------------- | --------------------------------------------- |
|nom_texture =|texture premier plan au format png|
|nom_texture2 =|texture arrière-plan optionnelle au format png|

## Bouton poussoir / Bouton glissière

|bouton_poussoir, bouton_glissiere |bibliothèque /_ihm|
| -------------- | --------------------------------------------- |
|accrochage =|False/True|
|nom_texture =|texture premier plan au format png|
|nom_texture2 =|texture arrière-plan optionnelle au format png|
|state =|fixe l'état actif/non actif du bouton, seulement si accrochage = True|

## Commutateur
|commutateur_2pos, commutateur_3pos |bibliothèque /_ihm|
| -------------- | --------------------------------------------- |
|accrochage =| False/True|
|nom_texture =|texture premier plan au format png|
|nom_texture2 =|texture arrière-plan optionnelle au format png|
|state =|0,1,2 : position du commutateur, seulement si accrochage = True|

## Potentiomètre
|bouton_tournant, bouton_lineaire_horizontal, bouton_lineaire_vertical|bibliothèque /_ihm|
| -------------- | --------------------------------------------- |
|alpha =|[0 à 100%]|
|nom_texture =|texture premier plan au format png|
|nom_texture2 =|texture arrière-plan optionnelle au format png|
|*|fixe la position d'affichage du % réglé par le bouton|

## Composition

Les composants simulables réglables doivent être associés à un composant ihm.

- Bibliothèque **_divers_pneumatique** :
![](fr/media/hmi3.png)

- Bibliothèque **_capteurs**
![](fr/media/hmi4.png)

- Bibliothèque **_résistances**
        - L'association d'un composant ihm n'est pas obligatoire pour les composants résistances
![](fr/media/hmi5.png)